# AWS Data Pipeline
Summary: for creating ETL workflows to automate processing of data at scheduled intervals, then terminate the resources.

- AWS data pipeline can be used to move data from one dynamoDB table in one region to another region
    - behind the scenes it launches EMR cluster -> stores in S3 -> starts EMR in the other region, Loads from S3 and sends to dynamoDB.

Pipeline
- composed of:
    - Datanodes
    - Activities
    - Preconditions
    - Schedules
- The pipeline is executed in EC2 instances or EMR clusters that are provisioned and terminated automatically.

Running on premise:
- Install a task runner package on your on-prem hosts
- The package continuously polls AWS Data Pipeline for work to perform
- Examples: Running a DB stored procedure or a database dump.
    
Activity:
- An action that Data Pipeline initiates on your behalf as part of a pipeline
    - examples:
        - CopyActivity (copies data between instances)
        - EmrActivity (spawns emr, ... , terminates)
        - ShellCommandActivity (execute a custom shell script)
        - ...

Precondition
- It's optional. Can be applied to a data source or activity.
- When a data source has a precondition check then that check must succeed before any activity that consumes that data source can be launched.
- examples:
    - DynamoDBDataExists
    - DynamoDBTableExists
    - S3KeyExists
    - S3PrefixExists
    - ShellCommandPrecondition (for custom preconditions)

Schedule:
- how frequently does the pipeline run.

A lot of data pipeline functionality has been replaced by AWS Lambda.