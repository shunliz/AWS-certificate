# Notes for the AWS Big Data Specialty Certification Exam

## Links / Tasks
- https://aws.amazon.com/certification/certified-big-data-specialty/
- Course: https://aws.amazon.com/training/course-descriptions/bigdata-fundamentals/
    - https://www.aws.training/transcript/curriculumplayer?transcriptId=WIwWOETJeUC_B31xuDS1pA2
- AWS whitepapers: https://aws.amazon.com/whitepapers/ ,


# Kinesis
- 3 services:
    - Kinesis Streams
    - Kinesis Analytics: Run SQL on the data streams
    - Kinesis Firehose: Load streaming data into S3, Redshift, etc.

## Kinesis Streams
- Collect and process large streams of data in real-time
- Use cases:
    - Fast (second / milisecond latency) processing of log events
    - Real-time metrics and reporting
    - Data analytics
    - Complex stream processing
    
- Kinesis Libraries / Tools:
    - Producing data:
        - Kinesis Producer Library (KPL)
            - Blog post, [Implementing Efficient and Reliable Producers with the Amazon Kinesis Producer Library](https://aws.amazon.com/blogs/big-data/implementing-efficient-and-reliable-producers-with-the-amazon-kinesis-producer-library/)
            - has auto-retry configurable mechanism
            - Supports two complementary ways of batching:
                - Collection (of stream records):
                    - buffers / collects records to write multiple records to multiple shards in a single request.
                    - `RecordMaxBufferedTime`: max time a record may be buffered before a request is sent. Larger = more throughput but higher latency.
                - Aggregation (of user records):
                    - Combines multiple user records into a single kinesis stream record. (using `PutRecords` API request)
            - KCL integration (for deaggregating user records)
        - Kinesis Agent
            - Standalone application that you can install in the servers you're interested in.
            - Features:
                - Monitors file patterns and sends new data records to delivery streams
                - Handles file rotation, checkpointing, and retry upon failure
                - Delivers all data in a reliable, timely, and simpler manner
                - Emits CloudWatch metrics for monitoring and troubleshooting
                - Allows preprocessing data ,e.g. converting multi-line record to single line, converting from delimiter to JSON, converting from log to JSON
        - Kinesis Streams API
    - Reading data:
        - Kinesis Client library (KCL)
            - The KCL ensures there is a record processor running and processing each shard.
            - The Kinesis Client Library uses a DynamoDB table to store control data. It creates one table per application that is processing data.
            - KCL creates a worker thread for each shard. Auto assigns shards to workers (even workers on different ec2 instances)
            - KCL Checkpointing
                - Last processed record sequence number is stored in DynamoDB
                - On worker failure, KCL restarts from last checkpointed record.
            - Supports deaggregation of records aggregated with KPL
            - Note: KCL may be bottlenecked by DynamoDB table (throwing Provisioned Throughput Exceptions)
                - Add more provisioned throughput to the dynamoDB table if needed.
        - Kinesis Stream API
    - Emitting data
        - Kinesis Connector Library (Java), for KCL
            - Connectors for: DynamoDb, Redshift, S3, Elasticsearch
            - Java library with the following steps / interfaces:
                - iTransformer: maps from stream records to user-defined data model
                - iFilter: remove irrelevant records
                - iBuffer: buffers based on size limit and total byte count
                - iEmitter: sends the data in the buffer to AWS services
            - S3Emitter: writes buffer to a single file.
            

- Kinesis Stream API:
    - `PutRecord` (single record per HTTP request)
    - `PutRecords` (multiple records per single HTTP request). Recommended. Higher throughput
        - Single record failure does not stop the processing of subsequent records
        - Will return `HTTP 200` as long as some records succeed (even when others failed).
        - Retry requires application code in the producer to examine the `PutRecordsResult` object and retry whichever records failed.
    

- Kinesis Data Streams (https://docs.aws.amazon.com/streams/latest/dev/key-concepts.html#partition-key)
    - A stream is a set of shards. Each shard is a sequence of data records.
    - Each data record has a sequence number that is assigned automatically by the stream.
    - A data record has 3 parts:
        - sequence number
        - partition key
        - data blob (immutable sequence of bytes). 
        - blob can be up to 1000KB.
    - A sequence number is only unique within it's shard

- Retention Period:
    - The length of time data is accessible in the stream.
    - Default: 24hrs. Max: 7days (168 hrs).
    - You pay more for longer retention periods. 

Kinesis Application Name:
- Each application must have a unique name per (AWS account, region). The name is used to identify the DynamoDB and the namespace for CloudWatch metrics.   

Partition Keys:
- A partition key is used to group data by shard within a stream. It must be present when writing to the stream. 
- When writing to a stream, Kinesis separates data records into multiple shards based on each record's partition key.
- Partition keys are Unicode strings with a maximum length of 256 bytes. An MD5 hash function is used to map partition keys to 128-bit integer values that defines which shard records will end up in.
    
A Kinesis data stream is a set of shards. Each shard has a sequence of data records. Each data record has a sequence number that is assigned by Kinesis Data Streams.
    - Kinesis Shard
        - Uniquely identified group of data records in a stream
        - You can have multiple shards in a stream.
        - Single shard capacity:
            - write
                - 1 MB/sec input
                - 1000 writes/sec
            - read
                - 2 MB/sec output
                - 5 transaction reads/sec
            - Remember: each stream record can have a blob of up to 1000 KB  
        - Resharding
            - Shard split: divide a shard into two shards
                - To split a shard, we must specify the shard that is to be split and the new hash key, which is the position in the shard where the shard gets split. In many cases, the new hash key might simply be the average of the beginning and ending hash key, but it can be any hash key value in the range being mapped into the shard.
                - Example using boto3:
`sinfo = kinesis.describe_stream("BotoDemo")
hkey = int(sinfo["StreamDescription"]["Shards"][0]["HashKeyRange"]["EndingHashKey"])
shard_id = 'shardId-000000000000' #we only have one shard!
kinesis.split_shard("BotoDemo", shard_id, str((hkey+0)/2))`
            - Shard merge: merge two shards into one
        - Partition Key:
            - Specified by the app that writes into the stream

- Kinesis Server-side encryption:
    - Can automatically encrypt data written, using KMS master keys. Both producer and consumer must have permission to access the master key.
    - Before you use user-generated KMS master keys, ensure that your Kinesis stream producers and consumers (IAM principals) are users in the KMS master key policy:
        - Add `kms:GenerateDataKey` to producer's role
        - Add `kms:Decrypt` to consumer's role
        

# Kinesis Firehose
- Managed service for loading data from streams directly into:
    - S3, Redshift and Elasticsearch
- Fully managed:
    - Scalability, sharding and monitoring with zero admin
    - Secure
- Methods to Load data
    - Use Kinesis Agent
    - Use AWS SDK
        - `PutRecord` and `PutRecordBatch`
- Firehose to S3:
    - Buffering of data before sending to S3. Sends whenever any of these conditions is met:
        - Buffer size (from 1 MB to 128 MB)
            - Firehose can raise the buffer size dynamically (e.g. when falling behind)
        - Buffer interval (from 60s to 900s)
- Can invoke AWS lambda for data transformation. Data flow:
    - Buffers incoming data up to 3 MB or buffering size specified, whichever is lowest
    - Firehose invokes Lambda function
    - Transformed data is sent from Lambda to Firehose for buffering
    - Transformed data is delivered to the destination.
    - Response from Lambda must include:
        - `recordId`: must be the same as prior to transformation
        - `result`: status, one of : `"Ok", "Dropped", "ProcessingFailed"`.
        - `data`: Transformed data payload
    - Failure handling of _data transformation_:
        - 3 retries
        - invocation errors logged in CloudWatch Logs
        - Unsuccessful records are stored in `processing_failed` folder in S3.
    - It's possible to store the source records in S3, prior to transformation. (Backup S3 bucket).
- Data delivery speed:
    - S3: based on buffer size / buffer interval
    - Redshift:
        - depending on how fast the redshift cluster finishes the COPY command.
        - Firehose sends new copy commands when previous have finished
    - Elasticsearch:
        - Depends on buffer size (1 - 100 MB) and Buffer interval
- Firehose Failure Handling:
    - S3:   
        - retries for up to 24 hrs
    - Redshift:
        - retry duration from 0-7200 sec (2 hrs) from S3
        - Skips S3 objects on failure
        - Writes failed objects in manifest file, which can be used manually to recover lost data (manual backfill)
    - ElasticSearch:
        - retry duration 0-7200 sec.
        - On failure, skips index request and stores in S3 `index_failed` folder.
        - Manual backfill
    
