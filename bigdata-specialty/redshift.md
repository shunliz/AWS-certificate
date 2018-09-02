# Redshift
Overview
- for OLAP, not OLTP
- multi-terabyte clusters in minutes
- column-oriented

Redshift architecture
- 1 leader node, multiple compute nodes
    - Leader node
        - has the SQL endpoint
        - coordinates parallel query execution
    - Compute node
        - queries are executed in parallel in multiple nodes
        - scale out / up/ down
        - 10 GBe network  
- runs in a single AZ (high-speed network communication)
- instance types: dc2 (dense compute), and dense storage (ds2)
- data stored on multiple nodes, dedicated CPU, memory and local storage
- Columnar data store:
    - tables are stored as columns not rows, so reading single or few columns is much faster
    - do not use for small amount of data, binary large objects, OLTP

Redshift integrations in AWS:
- COPY command 
    - to load data from:
        - S3,
        - DynamoDB
    - includes reference to IAM role
- skipped others..

Table Design
- Distribution styles
    - Even (default)
        - rows distributed accross slices regardless of values in a particular column
    - Key
        - Used to optimize JOINs. same key should be in the same slice to be faster.
    - All
        - copy of entire table is in each table
        - use case: data that does not change. not large tables.
- Sort Keys
    - Similar to indexes. They are not indexes.
    - Redshift uses block size of 1MB. Less IO seeks
    - Sort order allows quicker reading.
        - compound (default):
            - includes all columns stated. Order matters (sames as mysql indexes). Must include prefix of columns (same order).
            - vacuum and analyze operations used for improving performance
        - interleaved:
            - all columns are equally important.
            - Data load and vacuum is slower
            - Use on very large tables
            - Not good for loading data in sort order
 - Compression:
    - ENCODE lzo, mostly32, etc. reduce size
    - redshift support automatic compression
        - redshift automatically figures out a good encoding
        - runs ANALYZE command behind the scenes on table creation (only first time)
    - manual compression
        - run ANALIZE compression table_name, which suggests compression
 - constraint
    - column-level:
        - PRIMARY KEY
        - UNIQUE (it's not enforceable by redshift)
        - NOT NULL / NULL (the only that is enforced)
        - REFERENCES (same as FK), not enforceable by redshift
    - use only if the application enforces the constraints prior to data ingestion (helps with query planning, improving performance)
 - table_inspector util can be used to list what tables have nconding, sort keys, etc.

Redshift Workload management:
- rules to route queries (to manage slow / fast queries)
- define allocation of % of memory for specific user groups or query groups.
- creating user groups and query groups reqiures cluster reboot
- dont require reboot:
    - changing memory % per user group / query group
    - also concurrency (how many concurrent queries)
    - also timeout
- Can't explicitly prioritize queries, but use queues instead.

Loading data to redshift:
- don't use single inserts, use COPY command:
    - from S3, dynamoDB, EMR, EC2
    - split files (use same prefix), and copy will load in parallel, faster
- services that need to go through S3:
    - Kinesis firehose
    - kinesis app
    - AWS DB Migration Service
- Can use lambda to run the copy command triggered on S3.
- Splitting files
    - use number of files = number of slices or a multiple
        e.g. 4 slices -> 4, 8, 12, .. files
    - keep file sizes even
- Compress files (gzip, bzip, ...)
- Keep files between 1MB to 1GB
- when reading from dynamodb
    - specify readratio (a percentage of total RCU)
    - or use a copy of the table
- manifest:
    - a way to specify which files should be loaded, and from where.
    - manifest file is in JSON format, usually stored in S3
    - useful for:
        load required files only
        - load files from different buckets
        - load files with different prefixes
- Support file format:
    - CSV, delimited, JSON, fixed width, Avro
- When copy command fails, check tables `STL_LOAD_ERRORS`, `STL_LOADERROR_DETAIL`
- Redshift does not support UPSERT. Methods:
    - Staging table
        - use staging table. Replace all table in target table or merge all of them into target table.
        - target and staging table columns must match
        - within a transaction:
            - delete from target table rows from staging table.
            - insert into target table from staging table
    - within a transaction:
        - create a stanging table, update target table from staging table.
        - drop staging table
- Can use encryption with the COPY command.
    - Not supported:
        - servier side with customer provided keys
        - clioent side encryption with KMS
        - client side assymetric master key
- Unloading query results to S3, use UNLOAD command, 
    - using S3 server side encryption by default (SSE-s3). 
    - Can also use server side SSE-KMS
    - can use client side customer managed key (CSW-CMK)
    - not supported:
        - S3 encryption with server side customer supplied key

Maintenance operations
- Resize process
    - cluster goes into read-only mode, running queries and connections are terminated
    - cluster is restarted
    - queries in read-only mode in source cluster
    - target cluster is populated, DNS points to new cluster
    - source cluster is terminated 
- Redshift blocks are immutable. Need to vacuum operation for resorting and remove unused disk space.
    - vacuum is io intensive, use during lower use periods / maintenance windows
    - use redshift utility analyze_and_vacuum_utility to figure out what tables should be vacuumed
    - avoid vacuum by Loading data in sort order, and using timeseries tables
    - avoid vacuum on large tables (>700GB), recreate a nd repopulate table with bulk insert
- Can set up cross region snapshot (can use KMS encrypted snapshots)
    - KMS encrypted creates a nsapshot copy grant in the destination region
- restoring from snapshot is straightforward (same cluster size, etc)
- can restore single table from snapshot as well.
- Monitoring: use cloudwatch

Amazon Machine Learning
- skipped several details ..
- point to an s3 file with the input dataset (e.g: csv)
- define what are the output features
- ML automatically detects type
- ML can choose the type of data automatically (multiclass, ..)
- Default split is 70% training , 30% test
- Can set the score threshold for binary classification 
    
        


- check the grant thingie (where was this from?)

    
        


        