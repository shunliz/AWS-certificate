# EMR - Elastic Map Reduce
- Presto (and Impala) for running SQL on hadoop / HDFS

- Use cases:
    - log processing / analytics
    - ETL
    - Clickstream analysis
    - Machine learning (spark)
- EMR runs on single AZ
    - for network performance reasons
Apache Hadoop
- Modules:
    - Hadoop Common (Hadoop Core)
        - libraries and utils for other modules
        - abstracts underlying OS, etc.
    - Hadoop Distributed File System (HDFS)
        - Distributed File system
        - Fault-tolerant
        - Replicates Data
        - High throughput access to data
    - Hadoop YARN
        - Cluster resource management and job scheduling
- MapReduce Job Tasks:
    - Map:
        - splits data into smaller chunks processed in parallel
        - output becomes input for reduce task (aggregation)
    - Steps:
        1. Split
        2. Map (e.g. count words)
        3. Shuffle (Bring same keys together from different machines after map, e.g. bring together counts for a given word)
        4. Reduce (aggregate the counts per word., e.g. sum)
        
        
- Hadoop Architecture:
    - Single Master node 
        - Has the Resource manager
    - Multiple Slave nodes
        - contains:
            - Node Manager
            - Application Master
            - Container (that actually runs the application)

EMR Architecture:
- Instance Groups
    - just a way to organize EC2 instances (can have different instances types)
    - can have more than one instance group belonging to Task Instance Group. (To be confirmed)
    - Master Instance Group
    - Core Instance Groups
    - Task Instance Groups
- Nodes:
    - Single Master Node:
        - manages resources
        - coordinates distribution and execution
        - monitors health of core and task nodes
    - Core node (Slave Node):
        - runs tasks
        - store data in HDFS (i.e. they store data)
        - runs DataNode daemon which handles IO of HDFS / EMRFS
        - runs NodeManager to communicate with master node
        - removing core nodes (shrinking) can result in data loss from HDFS
    - Task node
        - they are optional in the cluster
        - they don't store data (no HDFS)
        - Added and removed during running of clusters.
        - Useful for extra capacity.
- HDFS
    - Distributed FS, simultaneous access from different machines.
    - Single global namespace provided by the master node.
    - Individual files are divided into multiple blocks which are stored in multiple Slave Nodes,
    - the same block is stored in multiple slave nodes for fault tolerance and performance
EMR Storage options:
- Instance store (ephemeral, lost after termination)
    - High IO , high IOPS, D2 and I3 instance families
- EBS for HDFS: note they don't persist after EMR termination, contrary to EC2 normal behavior.
- EMRFS: implementation of HDFS where data is read/write directly to S3
    - don't need HDFS necessarily
    - Read consistency is same as S3:
        - write consistency on new put requests
        - eventual consistency on overwrite put and delete
        - can cause problems in ETL pipelines when reading after writing as it may fail to read output of previous step
        - EMRFS consistent view feature:
            - checks read-after-write consistency of new S3 objects written or synced with EMRFS
            - retry logic if inconsistency is detected
            - done using metadata in DynamoDB  
- can use HDFS and EMRFS together
    - Copy data from S3 to HDFS using `S3DistCp`
    - use case:
        - need high I/O performance taking advantage of local instance storage.
        - processing the same dataset frequently.

## EMR Operations
- Launching clusters;
    - prebuilt scripts and apps: Java, Hive, Pig, Python, Scala, .NET
    - automatically launch from S3
    - CLI
    - two ways to configure on creation in browser
        - can use quick options for quick
            - can't select VPC, uses the default VPC
            - can only seelect a limited set of applications
            - can only use one instance type for both master and task nodes
            - can not change security groups at creation time, only after
    - Advanced options
        - define exactly what applications
        - can define different instance types for task nodes, master nodes
    - Launching steps:
        - can define what is ran after launching
        - can specify termination after all steps are terminated (for transient clusters)
    - Note: tag EC2 instances on EMR launching, not directly in EC2.
    - SSH keypair is optional 
    - on creation 2 default security groups are used:
        - one for master node
        - one for core&task nodes
- Long running vs transient clusters:
    - when to use Long running clusters:
        - jobs run often
        - queries often on the same dataset, inefficient to load it each time
        - HDFS data is kept on core nodes
        - Termination protection is enabled (can't terminate the cluster accidently)
    - transient clueters
        - reduced costs, only billed when cluster is running
        - input data, output data and code stored in S3.
        - easy recover in case of failure.
            - Hive metastore can be stored in MySQL RDS.
- Choosing Instance types:
    - Map Reduce: use M types or storage optimized I2 instances
    - Large HBase clusters: use I2 or D2
    - Machine learning: use P2, or C
    - Spark: use memory instances, like R4
- EMR default replication factor for HDFS:
    - 3 for >= 10 nodes
    - 2 for 4-9 nodes
    - 1 for <= 3 nodes
    - override in hdfs-site.xml
- Cluster sizing:
    - Master node sizing:
        - m4.xlarge for <= 50 nodes
        - m5.2xlarge for > 50 nodes
    - Task Nodes:
        - for HDFS, if replication factor is 3, 10 i2 instances each with 800GB SSD means we have capacity for 8 TB / 3
            - can add more instances of more EBS volumes
        - AWS best practice: use less, larger nodes.
Monitoring EMR
- Cloudwatch events
    - can set up an events rule that triggers whenever an EMR step status changes
        - as target, you can set e.g. msg sent to an SNS topic
- Cloudwatch metrics
    - `S3BytesRead`, `HDFSUtilization`, etc
- Web Interfaces
    - they are not publicly accessible, set up SSH tunnel to master node using local port forwarding, or using SOCKS proxy.
- Using ganglia, which is a distributed monitoring system. Runs on the master node

Resizing a cluster:
- can be done manually
    - adding instances is straightforward.
    - removing instances
    - EMR removes instances in graceful shrink
        - with HDFS, first EMR will replicate the blocks from instances marked for termination
        - can't have less instances than replication factor
- can enable autoscaling for EMR
    - set up min, max instances
    - can set up scale out rules 
    - can set up scale in rules
    - When creating a cluster through the browser, the default autoscaling role is automatically set `EMR_Autoscaling_DefaultRole`
        - without it , autoscaling doesn't work.
        - can't be added after cluster creation.

Hue in EMR
- open source web interface for apache hadoop
- can browse files in S3 and also in HDFS
- can browse HBase (open source NoSQL database)
- can browse ZooKeeper (key value store)
- has query browser using Hive (SQL)
    - similar to mysql workbench / pgadmin
- Job browser to check status of jobs
- browse server logs
- Oozie dashboard
- can use LDAP using existing credentials in an LDAP directory.
    - Should store this in S3, not in master node.
    - stored as a JSON file.

Hive on EMR
- HiveQL, SQL-like interface
- Hive Architecture
    - skipped
    - can store metastore in Mysql RDS for keeping it after termination
- Can run hive on data in:
    - S3 and DynamoDB
- Supports partitions (folders in S3)
- dynamoDB:
    - join tables, query, copy from and to dynamodb.
    - CREATE EXTERNAL TABLE command can be used to create a 'view' of a dynamodb table, so that inserts, updates, etc change the original dynamoDB table.

HBase on EMR
- NoSQL database, versioned db
- massively scalable 
- stricly consistent random realtime access for tables with billions of rows and millions of columns
- runs on top of EMRFS / HDFS
- Integrates with Hive
- Use cases:
    - Ad tech, clickstream, content (e.g. messages), Financial Data, ...
    - you have 100s of GBs to PBs
    - high write and update rates
    - flexible schema
    - fast access to data, random and real-time
    - fault-tolerance
    - no transactional applications (no complex joins, etc.)
    - wide column (many columns, no row size restrictions)
    - flexible row key data types (dynamodb only supports scalar partition key)
    - HBase index creation is manual and not so easy.
- Hbase VS redshift:
    - both are column oriented
    - writes:
        - HBase: updates and writes perform well
        - Redshift: use batch writes (COPY command), updates are slow
    - queries:
        - HBase: near real-time (over fast changing data)
        - Redshift: OLAP (large complex queries, joins, ...)
    - Summary: use HBase for fast changing data. Redshift for 

Presto on EMR:
- in-memory fast SQL query
- interactive analytic queries
- faster than hive
- query posgres, mongodb, redis, cassandra, dynamodb,...
- high concurrency, run thousands of queries per day.
- Dont use:
    - Not for joining very large tables (100M plus rows), use hive instead
    - not so good for batch processing as data needs to fit in memory

Spark on EMR:
- Fast engine for processing large amounts of data.
- runs in-memory or on disk. Much faster on in-memory
- Use cases:
    - interactive analytics (faster than hive)
    - scala, python ..
    - can query live data (w/ spark streaming)
    - supports stream processing
        - disparate data sources
    - machine learning
        - repeated queries. Traing machine learing algs
    - ETL
- When not to use:
    - not a database
    - data should fit in memory
    - not for large reporting environments with many users
        - instead use spark to copy data to a typical reporting database (redshift, RDS,...)
- Spark Core:
    - skipped
- Spark SQL
    - run low latency SQL
    - RDD and DataFrame APIs
    - file formats: avro, parquet, ORC. JSON
    - can query hive tables
    - JBDC/ OBDC for querying traditional databases.
- Spark integration AWS:
    - Spark streaming integrates with Kinesis streams using micro-batches
        - Spark uses abstracted Discretized Streams
        - makes use of KCL
- Compression file formats:
    - GZIP
        - Splittable: no
        - Compression ratio: high
        - speed: medium
    - BZIP2
        - Splittable: yes
        - ratio: very high
        - soeed: slow
    - LZO
        - Splittable: yes
        - ratio: low
        - speed: fast
    - PARQUET
        - Splittable: no (but splittable on avro?)
        - ratio: low
        - speed: very fast
    - file sizes:
        - gzip: 1-2 GB, because not splittable
        - avoid smaller than 100mbs 
    - S3DistCp can be used to copy data from-to S3 - HDFS.
        - can be used to combine smaller files into larger files
     
Lambda integration with Big Data Ecosystem:
- can trigger when S3, then insert data into DynamoDB, redshift,...
- notes:
    - `/tmp` space is 512mb
    - number of processes/ threads: 1024
    - max exec time: 300s
- can use lambda to process kinesis streams (polls kinesis )
- s3 -> aws lambda -> redshift . There's a lambda template. It stores metadata in dynamodb to prevent duplicates, checkpointing, etc.

EMR Security:
- security groups
    - need SG for master node, 
    - and other for core and task nodes
- default managed security groups
- use custom security groups e.g. when mulyipl clusters should be isolated from eachother.
- Can create EMR in private subnet
    - needs an S3 endpoint
    - needs bastion host to connect to master node
- Data encryption:
    - encryption at rest
    - in transit with TLS
        - for S3 it's enabled automatically
    - To add encryption needs to add an inline policy to the EMR role to allow access to KMS
    - encryption at rest:
        - supports in S3: SSE-s3, SSE-KMS, CSE-KMS, CSE-Custom
        - in local disk: use KMS
    - cannot change data encrpyion, need to unload to s3, then create new cluster without encryption.
- KMS supports sy,mmetric encryption only, same keys are used for encription and decritpion
    

check https://stackoverflow.com/questions/10569455/differences-between-amazon-s3-and-s3n-in-hadoop?rq=1
            
        
 
    
        

