# ElasticSearch
- use cases
    - log analysis
    - search documents
    - .
- Cluster configuration
    - number of instances and types
    - possible to use dedicated master nodes (yes/no), more stable.
         - recommended 3 per cluster. don't hold data. they are used as backups 
    - can be distributed across AZs.

- Primary shard and Replica shards can be split across different AZs for reliability
- Loading data using lambda: 
    - post data in cloudwatch logs
    - use lambda to load from cloudwatch to firehose
    - lambda decorator processes firehose with additional data (e.g. when processing VPC flow logs)
         - e.g. adding country by querying service for geoip,...
    - then firehose sends data to elasticsearch.

# RStudio
- open source IDE for R
- RStudio Server integrates with Athena, RDS, Redshift, ...
     - needs to install R packages first
- run RStudio in EC2
