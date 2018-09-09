**QUESTION 1**

A user plans to use RDS as a managed DB platform. Which of the below mentioned features is

not supported by RDS?

A. Automated backup

B. Automated scaling to manage a higher load

C. Automated failure detection and recovery

D. Automated software patching

**Answer: B**

**Explanation:**

AWS RDS provides a managed DB platform, which offers features, such as automated backup,

patch management, automated failure detection and recovery.

The scaling is not automated and the user needs to plan it with a few clicks.

[http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)



**QUESTION 2**

A user has not enabled versioning on an S3 bucket. What will be the version ID of the object

inside that bucket?

A. 0

B. There will be no version attached

C. Null

D. Blank

**Answer: C**

**Explanation:**

S3 objects stored in the bucket before the user has set the versioning state have a version ID of

null. When the user enables versioning, the objects in the bucket do not change and their ID

remains null.

[http://docs.aws.amazon.com/AmazonS3/latest/dev/AddingObjectstoVersionSuspendedBuckets.ht](/h ttp://docs.aws.amazon.com/AmazonS3/latest/dev/AddingObjectstoVersionSuspendedBuckets.ht  ml)

[ml](/h ttp://docs.aws.amazon.com/AmazonS3/latest/dev/AddingObjectstoVersionSuspendedBuckets.ht  ml)



**QUESTION 3**

A user has created a queue named "myqueue" with SQS. There are four messages published to

queue which are not received by the consumer yet. If the user tries to delete the queue, what will

happen?

A. A user can never delete a queue manually. AWS deletes it after 30 days of inactivity on queue

B. It will initiate the delete but wait for four days before deleting until all messages are deleted

automatically.

C. It will ask user to delete the messages first

D. It will delete the queue

**Answer: D**

**Explanation:**

SQS allows the user to move data between distributed components of applications so they can

perform different tasks without losing messages or requiring each component to be always

available. The user can delete a queue at any time, whether it is empty or not. It is important to

note that queues retain messages for a set period of time. By default, a queue retains messages

for four days.

[http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/SQSConcept](/h ttp://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/SQSConcept  s.html)

[s.html](/h ttp://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/SQSConcept  s.html)





