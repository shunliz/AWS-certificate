**QUESTION 75            
**

A user wants to access RDS from an EC2 instance using IP addresses. Both RDS and EC2 are

in the same region, but different AZs. Which of the below mentioned options help configure that

the instance is accessed faster?

A. Configure the Private IP of the Instance in RDS security group

B. Security group of EC2 allowed in the RDS security group

C. Configuring the elastic IP of the instance in RDS security group

D. Configure the Public IP of the instance in RDS security group

**Answer: A            
**

**Explanation:            
**

If the user is going to specify an IP range in RDS security group, AWS recommends using the

private IP address of the Amazon EC2 instance. This provides a more direct network route from

the Amazon EC2 instance to the Amazon RDS DB instance, and does not incur network charges

for the data sent outside of the Amazon network.

---

**QUESTION 76          
**

A user is creating a snapshot of an EBS volume. Which of the below statements is incorrect in

relation to the creation of an EBS snapshot?

A. Its incremental

B. It can be used to launch a new instance

C. It is stored in the same AZ as the volume

D. It is a point in time backup of the EBS volume

**Answer: C          
**

**Explanation:          
**

The EBS snapshots are a point in time backup of the EBS volume. It is an incremental snapshot,

but is always specific to the region and never specific to a single AZ. Hence the statement "It is

stored in the same AZ as the volume" is incorrect.

[http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSSnapshots.html](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSSnapshots.html)

---

**QUESTION 77        
**

A user is planning to use EBS for his DB requirement. The user already has an EC2 instance

running in the VPC private subnet. How can the user attach the EBS volume to a running

instance?

A. The user must create EBS within the same VPC and then attach it to a running instance.

B. The user can create EBS in the same zone as the subnet of instance and attach that EBS to

instance.

C. It is not possible to attach an EBS to an instance running in VPC until the instance is stopped.

D. The user can specify the same subnet while creating EBS and then attach it to a running

instance.

**Answer: B        
**

**Explanation:        
**

A Virtual Private Cloud \(VPC\) is a virtual network dedicated to the user's AWS account. The user

can create subnets as per the requirement within a VPC. The VPC is always specific to a region.

The user can create a VPC which can span multiple Availability Zones by adding one or more

subnets in each Availability Zone.

The instance launched will always be in the same availability zone of the respective subnet.

When creating an EBS the user cannot specify the subnet or VPC. However, the user must

create the EBS in the same zone as the instance so that it can attach the EBS volume to the

running instance.

[http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC\_Subnets.html\#VPCSubnet](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Subnets.html#VPCSubnet)

---

**QUESTION 78        
**

Which of the following groups is AWS Elastic Beanstalk best suited for?

A. Those who want to deploy and manage their applications within minutes in the AWS cloud

B. Those who want to privately store and manage Git repositories in the AWS cloud.

C. Those who want to automate the deployment of applications to instances and to update the

applications as required

D. Those who want to model, visualize, and automate the steps required to release software

**Answer: A        
**

**Explanation:        
**

AWS Elastic Beanstalk is best suited for those groups who want to deploy and manage their

applications within minutes in the AWS cloud. As a bonus, you don't even need experience with

cloud computing to get started.

[https://aws.amazon.com/elasticbeanstalk/faqs/        
](https://aws.amazon.com/elasticbeanstalk/faqs/)

---

**QUESTION 79        
**

You are using Amazon SQS and are getting a "Queue Deleted Recently" error. What is wrong?

A. The message is too big

B. You have incorrect permissions

C. Another user has deleted the queue

D. If you delete a queue, you need to wait for at least 60 seconds before creating a queue with the

same name

**Answer: D        
**

**Explanation:        
**

If you delete a queue, you need to wait for at least 60 seconds before creating a queue with the

same name. Please note that when you delete a queue, the deletion process takes up to 60

seconds. Requests you send to a recently deleted queue might succeed during the 60-second

period. For example, a SendMessage request might succeed, but after 60 seconds the queue

and that message you sent no longer exists.

[https://aws.amazon.com/items/1343?externalID=1343        
](https://aws.amazon.com/items/1343?externalID=1343)

---

**QUESTION 80        
**

Your manager has requested you to tag EC2 instances to organize and manage a load balancer.

Which of the following statements about tag restrictions is incorrect?

A. The maximum key length is 127 Unicode characters.

B. The maximum value length is 255 Unicode characters.

C. Tag keys and values are case sensitive.

D. The maximum number of tags per load balancer is 20.

**Answer: D        
**

**Explanation:        
**

Tags help you to categorize your load balancers in different ways, for example, by purpose,

owner, or environment. The following basic restrictions apply to tags: The maximum number of

tags per resource is

1. The maximum key length is 127 Unicode characters. The maximum value length that can be

used is 255 Unicode characters. The tag keys and values are case sensitive. Allowed characters

are letters, spaces, and numbers representable in UTF-8, plus the following special characters: +

* =. \_ : / @. Do not use leading or trailing spaces. Do not use the aws: prefix in your tag names or

values because it is reserved for AWS use. You can't edit or delete tag names or values with this

prefix. Tags with this prefix do not count against your tags per resource limit.

---

**QUESTION 81        
**

A user is trying to find the state of an S3 bucket with respect to versioning. Which of the below

mentioned states AWS will not return when queried?

A. versioning-enabled

B. versioning-suspended

C. unversioned

D. versioned

**Answer: D        
**

**Explanation:        
**

S3 buckets can be in one of the three states: unversioned \(the default\), versioning-enabled or

versioning-suspended. The bucket owner can configure the versioning state of a bucket. The

versioning state applies to all \(never some\) of the objects in that bucket. The first time owner

enables a bucket for versioning, objects in it are thereafter always versioned and given a unique

version ID.

[http://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html](http://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html)

---

**QUESTION 82        
**

What is the maximum number of tags that a user can assign to an EC2 instance?

A. 50

B. 10

C. 5

D. 25

**Answer: B        
**

**Explanation:        
**

To help manage EC2 instances as well as their usage in a better way, the user can tag the

instances. The tags are metadata assigned by the user which consists of a key and a value.

One resource can have a maximum of 10 tags.

[http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using\_Tags.html        
](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html)

---

**QUESTION 83      
**

How do you configure SQS to support longer message retention?

A. Set the MessageRetentionPeriod attribute using the SetQueueAttributes method

B. Using a Lambda function

C. You can't. It is set to 14 days and cannot be changed

D. You need to request it from AWS

**Answer: A      
**

**Explanation:      
**

To configure the message retention period, set the MessageRetentionPeriod attribute using the

SetQueueAttributes method. This attribute is used to specify the number of seconds a message

will be retained by SQS. Currently the default value for the message retention period is 4 days.

Using the MessageRetentionPeriod attribute, the message retention period can be set anywhere

from 60 seconds \(1 minute\), up to 1209600 seconds \(14 days\).

[https://aws.amazon.com/sqs/faqs/](https://aws.amazon.com/sqs/faqs/)

---

QUESTION 84

The user has created multiple AutoScaling groups. The user is trying to create a new AS group

but it fails. How can the user know that he has reached the AS group limit specified by

AutoScaling in that region?

A. Run the command: as-describe-account-limits

B. Run the command: as-describe-group-limits

C. Run the command: as-max-account-limits

D. Run the command: as-list-account-limits

**Answer: A      
**

**Explanation:      
**

A user can see the number of AutoScaling resources currently allowed for the AWS account

either by using the as-describe-account-limits command or by calling the DescribeAccountLimits

action.

[http://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/ts-as-capacity.html](http://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/ts-as-capacity.html)

---

**QUESTION 85      
**

An organization is hosting an application as part of the free usage tier. The organization wants to

create IAM users for each of its 150 employees and they may access AWS as part of free usage

tier. What will you advise the organization?

A. The IAM is not available as a part of the free usage tier

B. Create IAM roles and give access based on role since it will not cost the user

C. Do not create more than 100 users as it will cost the organization.

D. Create IAM users for each employee as it does not cost

**Answer: D      
**

**Explanation:      
**

IAM is a free service. You can create as many IAM users or groups as desired free of cost.

[http://docs.aws.amazon.com/IAM/latest/UserGuide/IAM\_Introduction.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/IAM_Introduction.html)

---

**QUESTION 86    
**

A user has enabled serverside encryption with S3. The user downloads the encrypted object from

S3.

How can the user decrypt it?

A. S3 does not support server side encryption

B. S3 provides a server side key to decrypt the object

C. The user needs to decrypt the object using their own private key

D. S3 manages encryption and decryption automatically

**Answer: D    
**

**Explanation:    
**

If the user is using the server-side encryption feature, Amazon S3 encrypts the object data before

saving it on disks in its data centres and decrypts it when the user downloads the objects. Thus,

the user is free from the tasks of managing encryption, encryption keys, and related tools.

[http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingEncryption.html](http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingEncryption.html)

---

**QUESTION 87    
**

A user has configured ELB with two instances running in separate AZs of the same region?

Which of the below mentioned statements is true?

A. Multi AZ instances will provide HA with ELB

B. Multi AZ instances are not possible with a single ELB

C. Multi AZ instances will provide scalability with ELB

D. The user can achieve both HA and scalability with ELB

**Answer: A    
**

**Explanation:    
**

If a user is running two instances in separate AZs, it will provide HA with ELB since ELB will

automatically stop routing the traffic to unhealthy instances and send it to healthy instances only.

---

**QUESTION 88    
**

Does Amazon DynamoDB support both increment and decrement atomic operations?

A. No, neither increment nor decrement operations.

B. Only increment, since decrement are inherently impossible with DynamoDB's data model.

C. Only decrement, since increment are inherently impossible with DynamoDB's data model.

D. Yes, both increment and decrement operations.

**Answer: D    
**

**Explanation:    
**

Amazon DynamoDB supports increment and decrement atomic operations.

[http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/APISummary.html](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/APISummary.html)

---

**QUESTION 89    
**

What is the data model of DynamoDB?

A. "Items", with Keys and one or more Attribute; and "Attribute", with Name and Value.

B. "Database", which is a set of "Tables", which is a set of "Items", which is a set of "Attributes".

C. "Table", a collection of Items; "Items", with Keys and one or more Attribute; and "Attribute", with

Name and Value.

D. "Database", a collection of Tables; "Tables", with Keys and one or more Attribute; and

"Attribute", with Name and Value.

**Answer: C    
**

**Explanation:    
**

The data model of DynamoDB is:

"Table", a collection of Items;

"Items", with Keys and one or more Attribute;

"Attribute", with Name and Value.

[http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DataModel.html](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DataModel.html)

---

**QUESTION 90    
**

A user is trying to configure access with S3. Which of the following options is not possible to

provide access to the S3 bucket / object?

A. Define the policy for the IAM user

B. Define the ACL for the object

C. Define the policy for the object

D. Define the policy for the bucket

**Answer: C    
**

**Explanation:    
**

Amazon S3 offers access policy options broadly categorized as resource-based policies and user

policies. Access policies, such as ACL and resource policy can be attached to the bucket. With

the object the user can only have ACL and not an object policy. The user can also attach access

policies to the IAM users in the account. These are called user policies.

[http://docs.aws.amazon.com/AmazonS3/latest/dev/s3-access-control.html](http://docs.aws.amazon.com/AmazonS3/latest/dev/s3-access-control.html)

---

**QUESTION 91  
**

An organization has enabled a strict password policy for its IAM users. The organization is taking

help from the IAM console to set the password policy. Which of the below mentioned rules cannot

be specified by the user as a part of the policy?

A. Allow at least one lower case letter

B. Allow at least one number

C. Allow at least one non-alphanumeric character

D. Do not allow the user to use the password from the last three passwords

**Answer: D  
**

**Explanation:  
**

AWS IAM allows an organization to create multiple users and provide them access to various

AWS services. By default when the user is created, he does not have password enabled and can

not login to AWS console. If the organization wants to allow the users to login to AWS console,

they can enable password for each user. It is required that IAM users follow certain guidelines to

set their IAM login password. For this IAM provides root account owner to setup passwrod policy.

The password policy also lets the specify whether all IAM users can change their own passwords.

As part of policy, organization can specify that passwords for IAM users must be of a certain

minimum length, must include certain characters, and a few more criteria such as below.

One upper / lower or both letters

One alpha numeric

One number

[http://docs.aws.amazon.com/IAM/latest/UserGuide/Using\_ManagingPasswordPolicies.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/Using_ManagingPasswordPolicies.html)

---

**QUESTION 92  
**

A user has developed an application which is required to send the data to a NoSQL database.

The user wants to decouple the data sending such that the application keeps processing and

sending data but does not wait for an acknowledgement of DB. Which of the below mentioned

applications helps in this scenario?

A. AWS Simple Notification Service

B. AWS Simple Workflow

C. AWS Simple Query Service

D. AWS Simple Queue Service

**Answer: D  
**

**Explanation:  
**

Amazon Simple Queue Service \(SQS\) is a fast, reliable, scalable, and fully managed message

queuing service. SQS provides a simple and cost-effective way to decouple the components of

an application. In this case, the user can use AWS SQS to send messages which are received

from an application and sent to DB. The application can continue processing data without waiting

for any acknowledgement from DB. The user can use SQS to transmit any volume of data without

losing messages or requiring other services to always be available.

[http://aws.amazon.com/sqs/](http://aws.amazon.com/sqs/)

---

**QUESTION 93**

In regard to DynamoDB, can I modify the index once it is created?

A. Yes, if it is a primary hash key index

B. Yes, if it is a Global secondary index

C. No

D. Yes, if it is a local secondary index

**Answer: C**

**Explanation:**

Currently, in DynamoDB, an index cannot be modified once it is created.

[http://aws.amazon.com/dynamodb/faqs/\#security\_anchor](http://aws.amazon.com/dynamodb/faqs/#security_anchor)

---

**QUESTION 94**

A user has created a new raw EBS volume. The user mounts the volume on the instance to

which it is attached. Which of the below mentioned options is a required step before the user can

mount the volume?

A. Run a cyclic check on the device for data consistency

B. Create a file system of the volume

C. No step is required. The user can directly mount the device

D. Resize the volume as per the original snapshot size

**Answer: B**

**Explanation:**

When a user is trying to mount a blank EBS volume, it is required that the user first creates a file

system within the volume.

[http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-using-volumes.html](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-using-volumes.html)

---

**QUESTION 95**

A user is launching an AWS RDS with MySQL. Which of the below mentioned options allows the

user to configure the INNODB engine parameters?

A. Options group

B. Engine parameters

C. Parameter groups

D. DB parameters

**Answer: C**

**Explanation:**

With regard to RDS, the user can manage the configuration of a DB engine by using a DB

parameter group. A DB parameter group contains engine configuration values that can be applied

to one or more DB instances of the same instance type.

[http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)

---



