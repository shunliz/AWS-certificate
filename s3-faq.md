**Q:  What is Amazon S3?**

Amazon S3 is object storage built to store and retrieve any amount of data from anywhere on the Internet. It’s a simple storage service that offers an extremely durable, highly available, and infinitely scalable data storage infrastructure at very low costs.

**Q:     How much data can I store in Amazon S3?**

The total volume of data and number of objects you can store are unlimited. Individual Amazon S3 objects can range in size from a minimum of 0 bytes to a maximum of 5 terabytes. The largest object that can be uploaded in a single PUT is 5 gigabytes. For objects larger than 100 megabytes, customers should consider using the[Multipart Upload](http://docs.amazonwebservices.com/AmazonS3/latest/dev/UploadingObjects.html)capability.

**Q:      What storage classes does Amazon S3 offer?**

Amazon S3 offers a range of storage classes designed for different use cases. There are four highly durable storage classes including Amazon S3 Standard for general purpose storage of frequently accessed data, Amazon S3 Standard-Infrequent Access or Amazon S3 One Zone-Infrequent Access for long-lived, but less frequently accessed data, and Amazon Glacier for long-term archive. You can learn more about these storage classes on the[Amazon S3 Storage Classes page](https://amazonaws-china.com/s3/storage-classes/).

**Q:         How is Amazon S3 data organized?**

Amazon S3 is a simple key-based object store. When you store data, you assign a unique object key that can later be used to retrieve the data. Keys can be any string, and they can be constructed to mimic hierarchical attributes. Alternatively, you can use S3 Object Tagging to organize your data across all of your S3 buckets and/or prefixes.

**Q:           How reliable is Amazon S3?**

Amazon S3 gives any developer access to the same highly scalable, highly available, fast, inexpensive data storage infrastructure that Amazon uses to run its own global network of web sites. The S3 Standard storage class is designed for 99.99% availability, the S3 Standard-IA storage class is designed for 99.9% availability, and the S3 One Zone-IA storage class is designed for 99.5% availability. All of these storage classes are backed by the[Amazon S3 Service Level Agreement](https://amazonaws-china.com/s3/sla/).

**Q:  Where is my data stored?**

You specify an AWS Region when you create your Amazon S3 bucket. For S3 Standard, S3 Standard-IA, and Amazon Glacier storage classes, your objects are automatically stored across multiple devices spanning a minimum of three Availability Zones, each separated by miles across an AWS Region. Objects stored in the S3 One Zone-IA storage class are stored redundantly within a single Availability Zone in the AWS Region you select. Please refer to[Regional Products and Services](https://amazonaws-china.com/about-aws/global-infrastructure/regional-product-services/)for details of Amazon S3 service availability by AWS Region.

**Q:  What is an AWS Region?**

An AWS Region is a geographic location where AWS provides multiple, physically separated and isolated Availability Zones which are connected with low latency, high throughput, and highly redundant networking.

**Q:  What is an AWS Availability Zone \(AZ\)?**

An AWS Availability Zone is an isolated location within an AWS Region. Within each AWS Region, S3 operates in a minimum of three AZs, each separated by miles to protect against local events like fires, floods, etc.

Amazon S3 Standard, S3 Standard-Infrequent Access, and Amazon Glacier storage classes replicate data across a minimum of three AZs to protect against the loss of one entire AZ. This remains true in Regions where fewer than three AZs are publicly available. Objects stored in these storage classes are available for access from all of the AZs in an AWS Region.

The Amazon S3 One Zone-IA storage class replicates data within a single AZ. Data stored in this storage class is susceptible to loss in an AZ destruction event.

**Q:  How do I decide which AWS Region to store my data in?**

There are several factors to consider based on your specific application. You may want to store your data in a Region that…

* ...is near to your customers, your data centers, or your other AWS resources in order to reduce data access latencies.

* ...is remote from your other operations for geographic redundancy and disaster recovery purposes.

* ...enables you to address specific legal and regulatory requirements.

* ...allows you to reduce storage costs. You can choose a lower priced region to save money. For S3 pricing information, please visit the  
  [S3 pricing page](https://amazonaws-china.com/s3/pricing/)

**Q:  How secure is my data in Amazon S3? **

Amazon S3 is secure by default. Upon creation, only the resource owners have access to Amazon S3 resources they create. Amazon S3 supports user authentication to control access to data. You can use access control mechanisms such as bucket policies and Access Control Lists \(ACLs\) to selectively grant permissions to users and groups of users. The Amazon S3 console highlights your publicly accessible buckets, indicates the source of public accessibility, and also warns you if changes to your bucket policies or bucket ACLs would make your bucket publicly accessible.

You can securely upload/download your data to Amazon S3 via SSL endpoints using the HTTPS protocol. If you need extra security you can use the Server-Side Encryption \(SSE\) option to encrypt data stored at rest. You can configure your Amazon S3 buckets to automatically encrypt objects before storing them if the incoming storage requests do not have any encryption information. Alternatively, you can use your own encryption libraries to encrypt data before storing it in Amazon S3.

**Q:  How secure is my data in Amazon S3? **

Amazon S3 is secure by default. Upon creation, only the resource owners have access to Amazon S3 resources they create. Amazon S3 supports user authentication to control access to data. You can use access control mechanisms such as bucket policies and Access Control Lists \(ACLs\) to selectively grant permissions to users and groups of users. The Amazon S3 console highlights your publicly accessible buckets, indicates the source of public accessibility, and also warns you if changes to your bucket policies or bucket ACLs would make your bucket publicly accessible.

You can securely upload/download your data to Amazon S3 via SSL endpoints using the HTTPS protocol. If you need extra security you can use the Server-Side Encryption \(SSE\) option to encrypt data stored at rest. You can configure your Amazon S3 buckets to automatically encrypt objects before storing them if the incoming storage requests do not have any encryption information. Alternatively, you can use your own encryption libraries to encrypt data before storing it in Amazon S3.

**Q:  How can I control access to my data stored on Amazon S3?**

Customers may use four mechanisms for controlling access to Amazon S3 resources: Identity and Access Management \(IAM\) policies, bucket policies, Access Control Lists \(ACLs\), and Query String Authentication. IAM enables organizations with multiple employees to create and manage multiple users under a single AWS account. With IAM policies, customers can grant IAM users fine-grained control to their Amazon S3 bucket or objects while also retaining full control over everything the users do. With bucket policies, customers can define rules which apply broadly across all requests to their Amazon S3 resources, such as granting write privileges to a subset of Amazon S3 resources. Customers can also restrict access based on an aspect of the request, such as HTTP referrer and IP address. With ACLs, customers can grant specific permissions \(i.e. READ, WRITE, FULL\_CONTROL\) to specific users for an individual bucket or object. With Query String Authentication, customers can create a URL to an Amazon S3 object which is only valid for a limited time. For more information on the various access control policies available in Amazon S3, please refer to the[Access Control topic](http://docs.amazonwebservices.com/AmazonS3/latest/dev/index.html?UsingAuthAccess.html)in the[Amazon S3 Developer Guide](http://docs.aws.amazon.com/AmazonS3/latest/dev/Welcome.html).

[Show less](https://amazonaws-china.com/s3/faqs/#)

## Security {#Security}

**Q:  How secure is my data in Amazon S3? **

Amazon S3 is secure by default. Upon creation, only the resource owners have access to Amazon S3 resources they create. Amazon S3 supports user authentication to control access to data. You can use access control mechanisms such as bucket policies and Access Control Lists \(ACLs\) to selectively grant permissions to users and groups of users. The Amazon S3 console highlights your publicly accessible buckets, indicates the source of public accessibility, and also warns you if changes to your bucket policies or bucket ACLs would make your bucket publicly accessible.

You can securely upload/download your data to Amazon S3 via SSL endpoints using the HTTPS protocol. If you need extra security you can use the Server-Side Encryption \(SSE\) option to encrypt data stored at rest. You can configure your Amazon S3 buckets to automatically encrypt objects before storing them if the incoming storage requests do not have any encryption information. Alternatively, you can use your own encryption libraries to encrypt data before storing it in Amazon S3.

[Show less](https://amazonaws-china.com/s3/faqs/#)

**Q:  How can I control access to my data stored on Amazon S3?**

Customers may use four mechanisms for controlling access to Amazon S3 resources: Identity and Access Management \(IAM\) policies, bucket policies, Access Control Lists \(ACLs\), and Query String Authentication. IAM enables organizations with multiple employees to create and manage multiple users under a single AWS account. With IAM policies, customers can grant IAM users fine-grained control to their Amazon S3 bucket or objects while also retaining full control over everything the users do. With bucket policies, customers can define rules which apply broadly across all requests to their Amazon S3 resources, such as granting write privileges to a subset of Amazon S3 resources. Customers can also restrict access based on an aspect of the request, such as HTTP referrer and IP address. With ACLs, customers can grant specific permissions \(i.e. READ, WRITE, FULL\_CONTROL\) to specific users for an individual bucket or object. With Query String Authentication, customers can create a URL to an Amazon S3 object which is only valid for a limited time. For more information on the various access control policies available in Amazon S3, please refer to the[Access Control topic](http://docs.amazonwebservices.com/AmazonS3/latest/dev/index.html?UsingAuthAccess.html)in the[Amazon S3 Developer Guide](http://docs.aws.amazon.com/AmazonS3/latest/dev/Welcome.html).

**Q:  Does Amazon S3 support data access auditing?**

Yes, customers can optionally configure an Amazon S3 bucket to create access log records for all requests made against it. Alternatively, customers who need to capture IAM/user identity information in their logs can configure[AWS CloudTrail Data Events](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/logging-management-and-data-events-with-cloudtrail.html).

These access log records can be used for audit purposes and contain details about the request, such as the request type, the resources specified in the request, and the time and date the request was processed.

**Q:  What options do I have for encrypting data stored on Amazon S3?**

You can choose to encrypt data using SSE-S3, SSE-C, SSE-KMS, or a client library such as the[Amazon S3 Encryption Client](http://docs.amazonwebservices.com/AWSJavaSDK/latest/javadoc/com/amazonaws/services/s3/AmazonS3EncryptionClient.html). All four enable you to store sensitive data encrypted at rest in Amazon S3.

SSE-S3 provides an integrated solution where Amazon handles key management and key protection using multiple layers of security. You should choose SSE-S3 if you prefer to have Amazon manage your keys.

SSE-C enables you to leverage Amazon S3 to perform the encryption and decryption of your objects while retaining control of the keys used to encrypt objects. With SSE-C, you don’t need to implement or use a client-side library to perform the encryption and decryption of objects you store in Amazon S3, but you do need to manage the keys that you send to Amazon S3 to encrypt and decrypt objects. Use SSE-C if you want to maintain your own encryption keys, but don’t want to implement or leverage a client-side encryption library.

SSE-KMS enables you to use[AWS Key Management Service](https://amazonaws-china.com/kms/)\(AWS KMS\) to manage your encryption keys. Using AWS KMS to manage your keys provides several additional benefits. With AWS KMS, there are separate permissions for the use of the master key, providing an additional layer of control as well as protection against unauthorized access to your objects stored in Amazon S3. AWS KMS provides an audit trail so you can see who used your key to access which object and when, as well as view failed attempts to access data from users without permission to decrypt the data. Also, AWS KMS provides additional security controls to support customer efforts to comply with PCI-DSS, HIPAA/HITECH, and FedRAMP industry requirements.

Using an encryption client library, such as the[Amazon S3 Encryption Client](http://docs.amazonwebservices.com/AWSJavaSDK/latest/javadoc/com/amazonaws/services/s3/AmazonS3EncryptionClient.html), you retain control of the keys and complete the encryption and decryption of objects client-side using an encryption library of your choice. Some customers prefer full end-to-end control of the encryption and decryption of objects; that way, only encrypted objects are transmitted over the Internet to Amazon S3. Use a client-side library if you want to maintain control of your encryption keys, are able to implement or use a client-side encryption library, and need to have your objects encrypted before they are sent to Amazon S3 for storage.

For more information on using Amazon S3 SSE-S3, SSE-C, or SSE-KMS, please refer to the topic on [Using Encryption](http://docs.amazonwebservices.com/AmazonS3/latest/dev/UsingEncryption.html) in the[Amazon S3 Developer Guide](http://docs.amazonwebservices.com/AmazonS3/latest/dev/).

**Q:  What is an Amazon VPC Endpoint for Amazon S3?**

An Amazon VPC Endpoint for Amazon S3 is a logical entity within a VPC that allows connectivity only to S3. The VPC Endpoint routes requests to S3 and routes responses back to the VPC.

**Q:  Can I allow a specific Amazon VPC Endpoint access to my Amazon S3 bucket?**

You can limit access to your bucket from a specific Amazon VPC Endpoint or a set of endpoints using Amazon S3 bucket policies. S3 bucket policies now support a condition, aws:sourceVpce, that you can use to restrict access. For more details and example policies, read[Using VPC Endpoints](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-endpoints.html).

**Q: What is Amazon Macie?**

Amazon Macie is an[AI-powered security service](https://amazonaws-china.com/macie/)that helps you prevent data loss by automatically discovering, classifying, and protecting sensitive data stored in Amazon S3. Amazon Macie uses machine learning to recognize sensitive data such as personally identifiable information \(PII\) or intellectual property, assigns a business value, and provides visibility into where this data is stored and how it is being used in your organization. Amazon Macie continuously monitors data access activity for anomalies, and delivers alerts when it detects risk of unauthorized access or inadvertent data leaks.

**Q:  How durable is Amazon S3?**

Amazon S3 Standard, S3 Standard–IA, S3 One Zone-IA, and Amazon Glacier are all designed to provide 99.999999999% durability of objects over a given year. This durability level corresponds to an average annual expected loss of 0.000000001% of objects. For example, if you store 10,000,000 objects with Amazon S3, you can on average expect to incur a loss of a single object once every 10,000 years. In addition, Amazon S3 Standard, S3 Standard-IA, and Amazon Glacier are all designed to sustain data in the event of an entire S3 Availability Zone loss.

As with any environment, the best practice is to have a backup and to put in place safeguards against malicious or accidental deletion. For S3 data, that best practice includes secure access permissions, Cross-Region Replication, versioning, and a functioning, regularly tested backup.

**Q:  How are Amazon S3 and Amazon Glacier designed to achieve 99.999999999% durability?**

Amazon S3 Standard, S3 Standard-IA, and Amazon Glacier storage classes redundantly store your objects on multiple devices across a minimum of three Availability Zones \(AZs\) in an Amazon S3 Region before returning SUCCESS. The S3 One Zone-IA storage class stores data redundantly across mutliple devices within a single AZ. These services are designed to sustain concurrent device failures by quickly detecting and repairing any lost redundancy, and they also regularly verify the integrity of your data using checksums.

**Q:  What checksums does Amazon S3 employ to detect data corruption?**

Amazon S3 uses a combination of Content-MD5 checksums and cyclic redundancy checks \(CRCs\) to detect data corruption. Amazon S3 performs these checksums on data at rest and repairs any corruption using redundant data. In addition, the service calculates checksums on all network traffic to detect corruption of data packets when storing or retrieving data.

**Q:  What is Versioning?**

Versioning allows you to preserve, retrieve, and restore every version of every object stored in an Amazon S3 bucket. Once you enable Versioning for a bucket, Amazon S3 preserves existing objects anytime you perform a PUT, POST, COPY, or DELETE operation on them. By default, GET requests will retrieve the most recently written version. Older versions of an overwritten or deleted object can be retrieved by specifying a version in the request.

**Q:  How does Versioning protect me from accidental deletion of my objects?**

When a user performs a DELETE operation on an object, subsequent simple \(un-versioned\) requests will no longer retrieve the object. However, all versions of that object will continue to be preserved in your Amazon S3 bucket and can be retrieved or restored. Only the owner of an Amazon S3 bucket can permanently delete a version. You can set [Lifecycle rules](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) to manage the lifetime and the cost of storing multiple versions of your objects.

**Q:  Can I setup a trash, recycle bin, or rollback window on my Amazon S3 objects to recover from deletes and overwrites?**

You can use [Lifecycle rules](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) along with [Versioning](http://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html) to implement a rollback window for your Amazon S3 objects. For example, with your versioning-enabled bucket, you can set up a rule that archives all of your previous versions to the lower-cost Glacier storage class and deletes them after 100 days, giving you a 100-day window to roll back any changes on your data while lowering your storage costs.

**Q:  How can I ensure maximum protection of my preserved versions?**

Versioning’s[Multi-Factor Authentication \(MFA\)](https://amazonaws-china.com/mfa/)Delete capability can be used to provide an additional layer of security. By default, all requests to your Amazon S3 bucket require your AWS account credentials. If you enable Versioning with MFA Delete on your Amazon S3 bucket, two forms of authentication are required to permanently delete a version of an object: your AWS account credentials and a valid six-digit code and serial number from an authentication device in your physical possession. To learn more about enabling Versioning with MFA Delete, including how to purchase and activate an authentication device, please refer to the[Amazon S3 Technical Documentation](http://docs.amazonwebservices.com/AmazonS3/latest/dev/Versioning.html).

**Q:  Why would I choose to use S3 Standard-IA?**

S3 Standard-IA is ideal for data that is accessed less frequently, but requires rapid access when needed. S3 Standard-IA is ideally suited for long-term file storage, older sync and share storage, and other aging data.

**Q:  How do I get my data into S3 Standard-IA?**

There are two ways to get data into S3 Standard-IA. You can directly PUT into S3 Standard-IA by specifying STANDARD\_IA in the x-amz-storage-class header. You can also set Lifecycle policies to transition objects from the S3 Standard to the S3 Standard-IA storage class.

**Q:  Is there a minimum storage duration charge for S3 Standard-IA?**

S3 Standard-IA is designed for long-lived but infrequently accessed data that is retained for months or years. Data that is deleted from S3 Standard-IA within 30 days will be charged for a full 30 days. Please see the[Amazon S3 pricing page](https://amazonaws-china.com/s3/pricing/)for information about S3 Standard-IA pricing.



**Q:  Is there a minimum object storage charge for S3 Standard-IA?**

S3 Standard-IA is designed for larger objects and has a minimum object storage charge of 128KB. Objects smaller than 128KB in size will incur storage charges as if the object were 128KB. For example, a 6KB object in S3 Standard-IA will incur S3 Standard-IA storage charges for 6KB and an additional minimum object size fee equivalent to 122KB at the S3 Standard-IA storage price. Please see the[Amazon S3 pricing page](https://amazonaws-china.com/s3/pricing/)for information about S3 Standard-IA pricing.





