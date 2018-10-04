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



**Q:  How secure is my data in Amazon S3? **

Amazon S3 is secure by default. Upon creation, only the resource owners have access to Amazon S3 resources they create. Amazon S3 supports user authentication to control access to data. You can use access control mechanisms such as bucket policies and Access Control Lists \(ACLs\) to selectively grant permissions to users and groups of users. The Amazon S3 console highlights your publicly accessible buckets, indicates the source of public accessibility, and also warns you if changes to your bucket policies or bucket ACLs would make your bucket publicly accessible.

You can securely upload/download your data to Amazon S3 via SSL endpoints using the HTTPS protocol. If you need extra security you can use the Server-Side Encryption \(SSE\) option to encrypt data stored at rest. You can configure your Amazon S3 buckets to automatically encrypt objects before storing them if the incoming storage requests do not have any encryption information. Alternatively, you can use your own encryption libraries to encrypt data before storing it in Amazon S3.

[Show less](https://amazonaws-china.com/s3/faqs/#)



**Q:  How can I control access to my data stored on Amazon S3?**

Customers may use four mechanisms for controlling access to Amazon S3 resources: Identity and Access Management \(IAM\) policies, bucket policies, Access Control Lists \(ACLs\), and Query String Authentication. IAM enables organizations with multiple employees to create and manage multiple users under a single AWS account. With IAM policies, customers can grant IAM users fine-grained control to their Amazon S3 bucket or objects while also retaining full control over everything the users do. With bucket policies, customers can define rules which apply broadly across all requests to their Amazon S3 resources, such as granting write privileges to a subset of Amazon S3 resources. Customers can also restrict access based on an aspect of the request, such as HTTP referrer and IP address. With ACLs, customers can grant specific permissions \(i.e. READ, WRITE, FULL\_CONTROL\) to specific users for an individual bucket or object. With Query String Authentication, customers can create a URL to an Amazon S3 object which is only valid for a limited time. For more information on the various access control policies available in Amazon S3, please refer to the[Access Control topic](http://docs.amazonwebservices.com/AmazonS3/latest/dev/index.html?UsingAuthAccess.html)in the[Amazon S3 Developer Guide](http://docs.aws.amazon.com/AmazonS3/latest/dev/Welcome.html).



**Q:  Does Amazon S3 support data access auditing?**

Yes, customers can optionally configure an Amazon S3 bucket to create access log records for all requests made against it. Alternatively, customers who need to capture IAM/user identity information in their logs can configure[AWS CloudTrail Data Events](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/logging-management-and-data-events-with-cloudtrail.html).

These access log records can be used for audit purposes and contain details about the request, such as the request type, the resources specified in the request, and the time and date the request was processed.



**Q:  What options do I have for encrypting data stored on Amazon S3?**

You can choose to encrypt data using SSE-S3, SSE-C, SSE-KMS, or a client library such as the[Amazon S3 Encryption Client](http://docs.amazonwebservices.com/AWSJavaSDK/latest/javadoc/com/amazonaws/services/s3/AmazonS3EncryptionClient.html). All four enable you to store sensitive data encrypted at rest in Amazon S3.

SSE-S3 provides an integrated solution where Amazon handles key management and key protection using multiple layers of security. You should choose SSE-S3 if you prefer to have Amazon manage your keys.

SSE-C enables you to leverage Amazon S3 to perform the encryption and decryption of your objects while retaining control of the keys used to encrypt objects. With SSE-C, you don’t need to implement or use a client-side library to perform the encryption and decryption of objects you store in Amazon S3, but you do need to manage the keys that you send to Amazon S3 to encrypt and decrypt objects. Use SSE-C if you want to maintain your own encryption keys, but don’t want to implement or leverage a client-side encryption library.

SSE-KMS enables you to use[AWS Key Management Service](https://amazonaws-china.com/kms/)\(AWS KMS\) to manage your encryption keys. Using AWS KMS to manage your keys provides several additional benefits. With AWS KMS, there are separate permissions for the use of the master key, providing an additional layer of control as well as protection against unauthorized access to your objects stored in Amazon S3. AWS KMS provides an audit trail so you can see who used your key to access which object and when, as well as view failed attempts to access data from users without permission to decrypt the data. Also, AWS KMS provides additional security controls to support customer efforts to comply with PCI-DSS, HIPAA/HITECH, and FedRAMP industry requirements.

Using an encryption client library, such as the[Amazon S3 Encryption Client](http://docs.amazonwebservices.com/AWSJavaSDK/latest/javadoc/com/amazonaws/services/s3/AmazonS3EncryptionClient.html), you retain control of the keys and complete the encryption and decryption of objects client-side using an encryption library of your choice. Some customers prefer full end-to-end control of the encryption and decryption of objects; that way, only encrypted objects are transmitted over the Internet to Amazon S3. Use a client-side library if you want to maintain control of your encryption keys, are able to implement or use a client-side encryption library, and need to have your objects encrypted before they are sent to Amazon S3 for storage.

For more information on using Amazon S3 SSE-S3, SSE-C, or SSE-KMS, please refer to the topic on [Using Encryption](http://docs.amazonwebservices.com/AmazonS3/latest/dev/UsingEncryption.html) in the[Amazon S3 Developer Guide](http://docs.amazonwebservices.com/AmazonS3/latest/dev/).





