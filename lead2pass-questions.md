**QUESTION 1**

A user plans to use RDS as a managed DB platform. Which of the below mentioned features is not supported by RDS?

A. Automated backup

B. Automated scaling to manage a higher load

C. Automated failure detection and recovery

D. Automated software patching

**Answer: B  **

**Explanation:    **

AWS RDS provides a managed DB platform, which offers features, such as automated backup, patch management, automated failure detection and recovery.

The scaling is not automated and the user needs to plan it with a few clicks.

[http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html        ](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)

---

**QUESTION 2    **

A user has not enabled versioning on an S3 bucket. What will be the version ID of the object inside that bucket?

A. 0

B. There will be no version attached

C. Null

D. Blank

**Answer: C  
Explanation:    **

S3 objects stored in the bucket before the user has set the versioning state have a version ID of null. When the user enables versioning, the objects in the bucket do not change and their ID remains null.

[http://docs.aws.amazon.com/AmazonS3/latest/dev/AddingObjectstoVersionSuspendedBuckets.html](http://docs.aws.amazon.com/AmazonS3/latest/dev/AddingObjectstoVersionSuspendedBuckets.html)

---

**QUESTION 3    **

A user has created a queue named "myqueue" with SQS. There are four messages published to

queue which are not received by the consumer yet. If the user tries to delete the queue, what will

happen?

A. A user can never delete a queue manually. AWS deletes it after 30 days of inactivity on queue

B. It will initiate the delete but wait for four days before deleting until all messages are deleted

automatically.

C. It will ask user to delete the messages first

D. It will delete the queue

**Answer: D  **

**Explanation:    **

SQS allows the user to move data between distributed components of applications so they can

perform different tasks without losing messages or requiring each component to be always

available. The user can delete a queue at any time, whether it is empty or not. It is important to

note that queues retain messages for a set period of time. By default, a queue retains messages

for four days.

[http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/SQSConcepts.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/SQSConcepts.html)

---

**QUESTION 4**

What happens if your application performs more reads or writes than your provisioned capacity?

A. Nothing

B. requests above your provisioned capacity will be performed but you will receive 400 error

codes.

C. requests above your provisioned capacity will be performed but you will receive 200 error

codes.

D. requests above your provisioned capacity will be throttled and you will receive 400 error codes.

**Answer: D**

**Explanation:  **

Speaking about DynamoDB, if your application performs more reads/second or writes/second

than your table's provisioned throughput capacity allows, requests above your provisioned

capacity will be throttled and you will receive 400 error codes.

---

**QUESTION 5**

In relation to Amazon SQS, how can you ensure that messages are delivered in order?

A. Increase the size of your queue

B. Send them with a timestamp

C. Give each message a unique id.

D. AWS cannot guarantee that you will receive messages in the exact order you sent them

**Answer: D**

**Explanation:  **

Amazon SQS makes a best effort to preserve order in messages, but due to the distributed

nature of the queue, AWS cannot guarantee that you will receive messages in the exact order

you sent them. You typically place sequencing information or timestamps in your messages so

that you can reorder them upon receipt.

[https://aws.amazon.com/items/1343?externalID=1343](https://aws.amazon.com/items/1343?externalID=1343)

---

**QUESTION 6  
**

An organization has launched two applications: one for blogging and one for ECM on the same _**\*\***_AWS Linux EC2 instance running in the AWS VPC. The organization has attached two private

IPs \(primary and secondary\) to the above mentioned instance. The organization wants the

instance OS to recognize the secondary IP address. How can the organization configure this?

A. Use the ec2-net-utility package which updates routing tables, uses DHCP to refresh the

secondary IP and adds the network interface.

B. Use the ec2-net-utils package which will configure an additional network interface and update

the routing table

C. Use the ec2-ip-update package which can configure the network interface as well as update the

secondary IP with DHCP.

D. Use the ec2-ip-utility package which can update the routing tables as well as refresh the

secondary IP using DHCP.

Answer: B

Explanation:

A Virtual Private Cloud \(VPC\) is a virtual network dedicated to the user's AWS account. It enables

the user to launch AWS resources into a virtual network that the user has defined. With VPC the

user can specify multiple private IP addresses for his instances. The number of network

interfaces and private IP addresses that a user can specify for an instance depends on the

instance type. This scenario helps when the user wants to host multiple websites on a single EC2

instance. After the user has assigned a secondary private IP address to his instance, he needs to

configure the operating system on that instance to recognize the secondary private IP address.

For AWS Linux, the ec2-net-utils package can take care of this step. It configures additional

network interfaces that the user can attach while the instance is running, refreshes secondary IP

addresses during DHCP lease renewal, and updates the related routing rules.

[http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/MultipleIP.html](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/MultipleIP.html)

