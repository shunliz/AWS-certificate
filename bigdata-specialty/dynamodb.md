# DynamoDB

* fully managed noSQL database
* no practical storage limitations
* runs on SSD behind the scences. single-digit ms latency
* DynamoDB is a collection of Tables

Table:

* You can specify the performance requirements:
  * Write Capacity Units , WCU - number of 1 KB blocks/sec. \(always rounded , 0.5 KB still counts as 1 WCU\)
  * Read Capacity Units, RCU - number of 4 KB blocks/sec. \(also rounded, 2 KB -&gt; 1 RCU\)
* Read Consistency
  * Eventually consistent reads by default
    * uses 0.5 RCU per 4 KB block \(therefore cheaper\)
  * Strongly consistent reads
    * uses 1 RCU per 4 KB block
* Data structure \(data schema\) is not fixed at the table level.
* Elements of a table:

  * Each row is called an `item`.
  * Each row has one or more Attributes \(similar to columns in SQL\).
    * Items don't all need to have the same attributes.
  * Special attributes:
    * Partition Key \(aka Hash Key\)
    * Sort Key \(aka Range Key\)
      * Allows 1-to-many relationship
      * Provides sorted items and efficient range queries
    * The value of the Partition Key + Sort key must unique in the table. If no sort key, then partition key value must be unique.
  * Attribute types:
    * `String`, `Number`, `Binary` \(base64\), `Boolean`, `Null`, `Document(List/Map)`= Json, `Set` = array

* When creating a table you must specify:

  * table name
  * WCU/ RCU
  * Partition key

* DynamoDB integrations:

  * Redshift COPY command can write directly from DynamoDB to Redshift.
  * On EMR, you can use Apache Hive to read and write to DynamoDB using SQL-like language.
    * can join dynamo DB tables, copy to S3, HDFS, etc
  * Use data pipeline to import/ export data from DynamoDB \(which behind the scenes spawns transient EMR clusters\)
  * Can specify triggers that automatically react to dynamoDB tables and call AWS Lambda
  * Kinesis Streams Connector library

DynamoDB Partitions

* A partition relates to the underlying storage and processing nodes of DynamoDB
* Initially one table = one parition
* Initially all data for a table is stored in the single partition.
* You have no direct control over the number of partitions \(only indirect\)
* Max capacity of a single partition:
  * 10 GB
  * 3000 RCU
  * 1000 WCU
* Note that the configured table capacity \(WCU/RCU\) is split accross partitions
* Data distribution over partitions:
  * the node is selected based on the partition key \(hashed\)
  * A given partition key value is mapped to one, and only one partition.
  * However, a partition can hold many different partition key values.
* Scaling \(increase / decrease number of partitions\)

  * When capacity is exceeded a new partition is added automatically and data is spread between them over time.
  * There is no automatic decrease in number of partitions
    * This can cause performance issues whereby a low WCU/RCU is divided among many partitions, which means the actual
      WCU and RCU limit for a given partition is even lower.
  * in other words, table capacity is divided across partitions!

* Calculating the minimum number of partitions:

  * max of:
    * Desired\_RCU / 3000 + Desired\_WCU / 1000
    * Data size / 10 GB

* Good attributes for partition keys:

  * many distinct values
  * uniform write pattern accross partitions
  * writes distributed uniformly across time \(can't usually control this\)

* Creating more uniform distribution of hot keys:

  * add random suffix \(e.g. PARTITION\_KEY=CONCAT\(ORIGINAL\_PARTITION\_KEY, RAND\(0,10\)\)\)
  * querying requires generating all the suffixes for a given `ORIGINAL_PARTITION_KEY` and querying each one of them.

* To handle bursts of writes, use SQS to buffer writes

* Burst Capacity

  * DynamoDB provides some flexibility in your per-partition throughput provisioning by providing burst capacity, as follows. Whenever you are not fully using a partition's throughput, DynamoDB reserves a portion of that unused capacity for later bursts of throughput to handle usage spikes.
  * retains up to five minutes \(300 seconds\) of unused read and write capacity. 
    During an occasional burst of read or write activity, these extra capacity units can be consumed quickly—even faster than the per-second provisioned throughput capacity that you've defined for your table.
    DynamoDB can also consume burst capacity for background maintenance and other tasks without prior notice.   

DynamoDB operations:

* SCAN
  * very inefficient linear search
* QUERY:
  * a single partition key or partition key + sort key
  * a partition key and range of sort keys
  * Indexed partition key + sort keys

Indexes

* Local Secondary Index \(LSI\)
  * Must be created at table-creation, can't be created after the fact.
  * The index itself contains:
    * old partition key \(same as base table\)
    * new sort key \(must be a single scalar attribute\)
    * old sort key \(as a regular, non-key value\)
    * a subset of attributes \(called projected attributes\)
  * LSI are sparse indexes, it will only have items \(=rows\) that contain non null sort key attribute.
  * Querying \(Reads\):
    * If you query an attribute that is not projected, you are charged for the entire ITEM cost as it must be pulled from the main table
      DynamoDB must query first the index and then the main table
      * Each sub query is rounded to 4KB separately 
  * Writes:
    * ADD: two writes if it belongs to LSI
    * DELETE: two writes if it belongs to LSI
    * UPDATE: may require two updates on the LSI, first to delete old entry, one to add a new entry. 
  * LSI limits the number of sort keys for a given partition key to 10 GB
    * \(Called ItemCollections\).
  * LSI limitations:
    * can perform efficient queries for specified partition key values.
      However, cannot efficiently query the sparse index if one wants to query without specifying the partition key
      example: partition key= weather station, LSI sort key=intrusion detected.
      Can't query all items which have intrusion detected regardless of which weather station it is.
      Need GSI for this. In that case the intrusion\_detected attribute would be defined as the partition key
      and the old partition \(=weather station\) would become the sort key of the GSI\).     
      * Global Secondary Index \(GSI\)
      * can be thought of as a copy of the original table whose replication is handled by dynamoDB
      * can have its own alternative Partition and sort key
      * has its own capacity, RCU/WCU, independent from main table
      * GSI is updated asynchronously
      * Options for attribute projection:
    * KEYS\_ONLY:
      * new partition key
      * new sort key
      * old partition key
      * old sort key
    * INCLUDE:
      * specify custom projection values
    * ALL:
      * projects all attributes
  * Note: GSI can cause bottlenecks to updates to the original table.
    * because GSI has its own WCU/RCU limits 

DynamoDB stream

* an ordered record of updates to a DynamoDB table
* stores changes for 24hrs
* endpoint: streams.dynamodb.us-west-2.amazonaws.com
  * note: the streams API has its own endpoint, not the same has the main dynamodb api.
* All changes show up in the stream once and only once.
* Latency is low \(near real-time\)
* What gets written to the stream is configurable with four 'views':
  * `KEYS_ONLY`: only the key attributes are written to the stream \(partition, sort\)
  * `NEW_IMAGE`: entire item after update
  * `OLD_IMAGE`: entire item before update
  * `OLD_AND_NEW_IMAGE`: both old and new
* Use cases:
  * Replication
    * replicate a database table in one AWS region to another in near-realtime for resiliency
    * sync writes in different regions?
    * Note: as of Nov 2017, replication is now supported natively by DynamoDB with the 'Global Tables' feature. 
  * Triggers
    * Lambda function triggered, e.g.
      * when new user is added to the users table
      * when items are added, for performing analytics 



