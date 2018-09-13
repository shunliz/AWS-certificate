QUESTION 121

A user is uploading archives to Glacier. The user is trying to understand key Glacier resources.

Which of the below mentioned options is not a Glacier resource?

A. Notification configuration

B. Archive ID

C. Job

D. Archive

**Answer: B      
**

**Explanation:      
**

AWS Glacier has four resources. Vault and Archives are core data model concepts. Job is

required to initiate download of archive. The notification configuration is required to send user

notification when archive is available for download.

[**http://docs.aws.amazon.com/amazonglacier/latest/dev/amazon-glacier-data-model.html**](http://docs.aws.amazon.com/amazonglacier/latest/dev/amazon-glacier-data-model.html)

---

**QUESTION 122      
**

An organization has 10 departments. The organization wants to track the AWS usage of each

department. Which of the below mentioned options meets the requirement?

A. Setup IAM groups for each department and track their usage

B. Create separate accounts for each department, but use consolidated billing for payment and

tracking

C. Create separate accounts for each department and track them separately

D. Setup IAM users for each department and track their usage

**Answer: B      
**

**Explanation:      
**

The cost of an IAM user or groups can never be tracked separately for the purpose of billing.

The best solution in this case is to create a separate account for each department and use

consolidated billing.

[http://docs.aws.amazon.com/IAM/latest/UserGuide/IAM\_Introduction.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/IAM_Introduction.html)

---

**QUESTION 123      
**

Regarding Amazon SWF, at times you might want to record information in the workflow history of

a workflow execution that is specific to your use case. \_\_\_\_\_\_\_\_\_ enable you to record

information in the workflow execution history that you can use for any custom or scenario-specific

purpose.

A. Markers

B. Tags

C. Hash keys

D. Events

**Answer: A      
**

**Explanation:      
**

In Amazon SWF, at times you might want to record information in the workflow history of a

workflow execution that is specific to your use case. Markers enable you to record information in

the workflow execution history that you can use for any custom or scenario-specific purpose.

[http://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dg-adv.html](http://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dg-adv.html)

---

**QUESTION 124      
**

How can you peek at a message in Amazon SQS?

A. Log the message ID and the receipt handle for your messages and correlate them to confirm

when a message has been received and deleted

B. Send the message to Amazon S3

C. You can't

D. Set up a CloudWatch alarm to auto send you the message

**Answer: A      
**

**Explanation:      
**

With version 2008-01-01, the PeekMessage action has been removed from Amazon SQS. This

functionality was used mainly to debug small systems -- specifically to confirm a message was

successfully sent to the queue or deleted from the queue.

To do this with version 2008-01-01, you can log the message ID and the receipt handle for your

messages and correlate them to confirm when a message has been received and deleted.

[https://aws.amazon.com/items/1343?externalID=1343      
](https://aws.amazon.com/items/1343?externalID=1343)

---

**QUESTION 125      
**

In regard to DynamoDB, for which one of the following parameters does Amazon not charge you?

A. Cost per provisioned write units

B. Cost per provisioned read units

C. Storage cost

D. I/O usage within the same Region

**Answer: D      
**

**Explanation:      
**

In DynamoDB, you will be charged for the storage and the throughput you use rather than for the

I/O which has been used.

[http://aws.amazon.com/dynamodb/pricing/](http://aws.amazon.com/dynamodb/pricing/)

---

**QUESTION 126      
**

An organization has created 10 IAM users. The organization wants those users to work

independently and access AWS. Which of the below mentioned options is not a possible

solution?

A. Create the access key and secret access key for each user and provide access to AWS using

the console

B. Create the X.509 certificate for each user and provide them access to AWS CLI

C. Enable MFA for each IAM user and assign them the virtual MFA device to access the console

D. Provide each user with the IAM login and password for the AWS console

**Answer: A      
**

**Explanation:      
**

If an organization has created the IAM users, the users can access AWS services either with an

IAM specific login/password or console. The organization can generate the IAM X.509 certificates

to access AWS with CLI. The organization can also enable MFA for each IAM user, which allows

an added security for each IAM user. If the organization has created the access key and secret

key than the user cannot access the console using those keys. Access key and secret access

key are useful for CLI or Webservices.

[http://docs.aws.amazon.com/IAM/latest/UserGuide/IAM\_Introduction.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/IAM_Introduction.html)

---

**QUESTION 127      
**

What is the maximum size for messages stored in SQS?

A. 256KB

B. 128KB

C. 1024KB

D. 64KB

**Answer: A      
**

**Explanation:**

By default, SQS queues allow you to send the largest supported payload size, currently 256KB.

You can choose to specify a limit on how many bytes can be sent per payload, using the

MaximumMessageSize attribute of the SetQueueAttributes method.

[http://aws.amazon.com/sqs/faqs/](http://aws.amazon.com/sqs/faqs/)

---

**QUESTION 128      
**

A user is planning to host data with RDS. Which of the below mentioned databases is not

supported by RDS?

A. PostgreSQL

B. SQLDB

C. Oracle

D. MS SQL

**Answer: B      
**

**Explanation:      
**

Amazon Relational Database Service \(Amazon RDS\) is a web service that makes it easier to set

up, operate, and scale a relational database in the cloud. AWS RDS supports popular DBs, such

as MySQL, PostgreSQL, MS SQL and Oracle. This means that the code, applications, and tools

user is already using with existing databases can be used with Amazon RDS too. In short, it is a

managed Relation Database offering from AWS which manages backups, software patching,

automatic failure detection, and recovery of Database.

[http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)

---

**QUESTION 129      
**

An EC2 instance has one additional EBS volume attached to it. How can a user attach the same

volume to another running instance in the same AZ?

A. Terminate the first instance and only then attach to the new instance

B. Attach the volume as read only to the second instance

C. Detach the volume first and attach to new instance

D. No need to detach. Just select the volume and attach it to the new instance, it will take care of

mapping internally

**Answer: C      
**

**Explanation:      
**

If an EBS volume is attached to a running EC2 instance, the user needs to detach the volume

from the original instance and then attach it to a new running instance. The user doesn't need to

stop / terminate the original instance.

[http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-detaching-volume.html](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-detaching-volume.html)

---

**QUESTION 130      
**

A user has configured an automated backup between 5 AM ?5:30 AM for the MySQL RDS DB.

Will the performance of RDS get frozen momentarily during a backup?

A. No

B. Yes, only if the instance size is smaller than large size

C. Yes, provided it is a single zone implementation

D. Yes, always

**Answer: C      
**

**Explanation:      
**

Amazon RDS provides two different methods for backing up and restoring the Amazon DB

instances. A brief I/O freeze, typically lasting a few seconds, occurs during both automated

backups and DB snapshot operations on Single-AZ DB instances.

---

**QUESTION 131      
**

A root AWS account owner has created three IAM users: Bob, John and Michael. Michael is the

IAM administrator. Bob and John are not the superpower users, but users with some pre-defined

policies. John does not have access to modify his password. Thus, he asks Bob to change his

password. How can Bob change John's password?

A. This statement is false. It should be Michael who changes the password for John

B. It is not possible that John cannot modify his password

C. Provided Bob is the manager of John

D. Provided Michael has added Bob to a group, which has permissions to modify the IAM

passwords

**Answer: D      
**

**Explanation:      
**

Generally with IAM users, the password can be modified in two ways. The first option is to define

the IAM level policy which allows each user to modify their own passwords. The other option is to

create a group and create a policy for the group which can change the passwords of various IAM

users.

[http://docs.aws.amazon.com/IAM/latest/UserGuide/HowToPwdIAMUser.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/HowToPwdIAMUser.html)

---

**QUESTION 132    
**

Regarding Amazon SNS, to send messages to a queue through a topic, you must subscribe the

queue to the Amazon SNS topic. You specify the queue by its \_\_\_\_\_\_\_.

A. ARN

B. Token

C. Registration ID

D. URL

**Answer: A    
**

**Explanation:    
**

In Amazon SNS, to send messages to a queue through a topic, you must subscribe the queue to

the Amazon SNS topic. You specify the queue by its ARN.

[http://docs.aws.amazon.com/sns/latest/dg/SendMessageToSQS.html](http://docs.aws.amazon.com/sns/latest/dg/SendMessageToSQS.html)

---

**QUESTION 133  
**

To scale up the AWS resources using manual AutoScaling, which of the below mentioned

parameters should the user change?

A. Maximum capacity

B. Desired capacity

C. Preferred capacity

D. Current capacity

**Answer: B  
**

**Explanation:  
**

The Manual Scaling as part of Auto Scaling allows the user to change the capacity of Auto

Scaling group. The user can add / remove EC2 instances on the fly. To execute manual scaling,

the user should modify the desired capacity. AutoScaling will adjust instances as per the

requirements. If the user is trying to CLI, he can use command as-set-desired-capacity &lt;Auto

Scaling Group Name&gt; --desired-capacity &lt;New Capacity&gt;

[http://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/as-manual-scaling.html](http://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/as-manual-scaling.html)

---

**QUESTION 134

A user has configured a website and launched it using the Apache web server on port 80. The

user is using ELB with the EC2 instances for Load Balancing. What should the user do to ensure

that the EC2 instances accept requests only from ELB?

A. Open the port for an ELB static IP in the EC2 security group

B. Configure the security group of EC2, which allows access to the ELB source security group

C. Configure the EC2 instance so that it only listens on the ELB port

D. Configure the security group of EC2, which allows access only to the ELB listener

**Answer: B

**Explanation:

When a user is configuring ELB and registering the EC2 instances with it, ELB will create a

source security group. If the user wants to allow traffic only from ELB, he should remove all the

rules set for the other requests and open the port only for the ELB source security group.

---

**QUESTION 135

When working with AWS CloudFormation Templates what is the maximum number of stacks that

you can create?

A. 500

B. 50

C. 20

D. 10

**Answer: C

**Explanation:

CloudFormation Limits

Maximum number of AWS CloudFormation stacks that you can create is 20 stacks.

[http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cloudformation-limits.html](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cloudformation-limits.html)

---

**QUESTION 136

Does DynamoDB support in-place atomic updates?

A. It is not defined

B. Yes

C. It does support in-place non-atomic updates

D. No

**Answer: B

**Explanation:

DynamoDB supports in-place atomic updates.

---

**QUESTION 137

A user is having access to objects of an S3 bucket which is not owned by him. If he is trying to set

the objects of that bucket public, which of the below mentioned options may be a right fit for this

action?

A. Make the bucket public with full access

B. Define the policy for the bucket

C. Provide ACL on the object

D. Create an IAM user with permission

**Answer: C

**Explanation:

An S3 object ACL is the only way to manage access to objects which are not owned by the

bucket owner. An AWS account that owns the bucket can grant another AWS account permission

to upload objects. The bucket owner does not own these objects. The AWS account that created

the object must grant permissions using object ACLs.

[http://docs.aws.amazon.com/AmazonS3/latest/dev/access-policy-alternatives-guidelines.html](http://docs.aws.amazon.com/AmazonS3/latest/dev/access-policy-alternatives-guidelines.html)

---

**QUESTION 138

A bucket owner has allowed another account's IAM users to upload or access objects in his

bucket. The IAM user of Account A is trying to access an object created by the IAM user of

account B. What will happen in this scenario?

A. The bucket policy may not be created as S3 will give error due to conflict of Access Rights

B. It is not possible to give permission to multiple IAM users

C. AWS S3 will verify proper rights given by the owner of Account A, the bucket owner as well as

by the IAM user B to the object

D. It is not possible that the IAM user of one account accesses objects of the other IAM user

**Answer: C

**Explanation:

If a IAM user is trying to perform some action on an object belonging to another AWS user's

bucket, S3 will verify whether the owner of the IAM user has given sufficient permission to him.

It also verifies the policy for the bucket as well as the policy defined by the object owner.

---

**QUESTION 139

A user wants to achieve High Availability with PostgreSQL DB. Which of the below mentioned

functionalities helps achieve HA?

A. Read Replica

B. Multi AZ

C. Multi region

D. PostgreSQL does not support HA

**Answer: B

**Explanation:

The Multi AZ feature allows the user to achieve High Availability. For Multi AZ, Amazon RDS

automatically provisions and maintains a synchronous "standby" replica in a different Availability

Zone.

[http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)

---


