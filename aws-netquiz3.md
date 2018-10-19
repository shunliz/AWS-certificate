**Question 1**

You have multiple Amazon EC2 instances running in a cluster across multiple Availability Zones within the same region. What combination of the following should be used to ensure the highest network performance \(packets per second\), lowest latency, and lowest jitter? Choose 3 answers

1. Amazon EC2 placement groups \(would not work for multiple AZs\)
2. **Enhanced networking**
   \(provides network performance, lowest latency\)
3. Amazon PV AMI \(Requires HVM\)
4. **Amazon HVM AMI \(**Requires HVM**\)**
5. Amazon Linux \(Can be on others as well\)
6. **Amazon VPC**
   \(works only in VPC, can’t enable enhanced networking if the instance is in EC2-Classic\)

**Question 2**

What are characteristics of Amazon S3? Choose 2 answers

1. **Objects are directly accessible via a URL**
2. S3 should be used to host a relational database
3. S3 allows you to store objects or virtually unlimited size
4. **S3 allows you to store virtually unlimited amounts of data**
5. S3 offers Provisioned IOPS



**Question 3**

When you put objects in Amazon S3, what is the indication that an object was successfully stored?

1. Each S3 account has a special bucket named\_s3\_logs. Success codes are written to this bucket with a timestamp and checksum.
2. A success code is inserted into the S3 object metadata.
3. **A HTTP 200 result code and MD5 checksum, taken together, indicate that the operation was successful.**
4. Amazon S3 is engineered for 99.999999999% durability. Therefore there is no need to confirm that data was inserted.

**Question 4**

What is the maximum number of S3 buckets available per AWS Account?

1. 100 Per region
2. There is no Limit
3. **100 Per Account**\(Refer[documentation](http://docs.aws.amazon.com/AmazonS3/latest/dev/BucketRestrictions.html)\)
4. 500 Per Account
5. 100 Per IAM User



