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

**Question 5**

Which of the following are valid statements about Amazon S3? Choose 2 answers

1. S3 provides read-after-write consistency for any type of PUT or DELETE.
2. Consistency is not guaranteed for any type of PUT or DELETE.
3. **A successful response to a PUT request only occurs when a complete object is saved**
4. Partially saved objects are immediately readable with a GET after an overwrite PUT.
5. **S3 provides eventual consistency for overwrite PUTS and DELETES**

**Question 6**

A user has an S3 object in the US Standard region with the content “color=red”. The user updates the object with the content as “color=”white”. If the user tries to read the value 1 minute after it was uploaded, what will S3 return?

1. It will return “color=white”
2. It will return “color=red”
3. It will return an error saying that the object was not found
4. **It may return either “color=red” or “color=white” i.e. any of the value**
   \(Eventual Consistency\)

**Question 7**

A user has not enabled versioning on an S3 bucket. What will be the version ID of the object inside that bucket?

1. 0
2. There will be no version attached
3. **Null**
4. Blank

**Question 8**

Which set of Amazon S3 features helps to prevent and recover from accidental data loss?

1. Object lifecycle and service access logging
2. **Object versioning and Multi-factor authentication**
3. Access controls and server-side encryption
4. Website hosting and Amazon S3 policies



**Question 9**

If an object is stored in the Standard S3 storage class and you want to move it to Glacier, what must you do in order to properly migrate it?

1. Change the storage class directly on the object.
2. Delete the object and re-upload it, selecting Glacier as the storage class.
3. None of the above.
4. **Create a lifecycle policy that will migrate it after a minimum of 30 days.**
   \(Any object uploaded to S3 must first be placed into either the Standard, Reduced Redundancy, or Infrequent Access storage class. Once in S3 the only way to move the object to glacier is through a lifecycle policy\)







