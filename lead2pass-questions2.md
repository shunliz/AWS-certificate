**QUESTION 38**

Can one instance be registered with two ELBs in the same region?

A. No

B. Yes, provided both ELBs have the same health check configuration

C. Yes, always

D. Yes, provided both ELBs are in the same AZ

**Answer: C**

**Explanation:**

Yes, it is possible to have one instance part of two separate ELBs, though both ELBs have

different configurations. ELBs are never launched in specific zones.

[http://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/enable-disable-az.html](http://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/enable-disable-az.html)

---

**QUESTION 39**

What does Amazon SQS provide?

A. An asynchronous message queue service.

B. A Simple Query Server, managed directly by Amazon Web Services.

C. None of these.

D. A synchronous message queue service.

**Answer: A**

**Explanation:**

Amazon SQS stands for Simple Queue Services, and provides a cost-effective way to decouple

the components of your application through an asynchronous message queue service

[http://aws.amazon.com/sqs/](http://aws.amazon.com/sqs/)

---

**QUESTION 40**

A user is trying to create a list of IAM users with the AWS console. When the IAM users are

created which of the below mentioned credentials will be enabled by default for the user?

A. IAM access key and secret access key

B. IAM X.509 certificates

C. Nothing. Everything is disabled by default

D. IAM passwords

**Answer: C**

**Explanation:**

Newly created IAM users have no password and no access key \(access key ID and secret

access key\). If the user needs to administer your AWS resources using the AWS Management

Console, you can create a password for the user. If the user needs to interact with AWS

programmatically \(using the command line interface \(CLI\), the AWS SDK, or service-specific

APIs\), you can create an access key for that user. The credentials you create for users are what

they use to uniquely identify themselves to AWS.

[http://docs.aws.amazon.com/IAM/latest/UserGuide/Using\_WorkingWithGroupsAndUsers.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/Using_WorkingWithGroupsAndUsers.html)

---

**QUESTION 41**

Bob is an IAM user who has access to the EC2 services. Admin is an IAM user who has access

to all the AWS services including IAM. Can Bob change his password?

A. No, the IAM user can never change the password

B. Yes, provided Admin has given Bob access to change his password

C. Yes, only from AWS CLI

D. Yes, only from the AWS console

**Answer: B**

**Explanation:**

The IAM users by default cannot change their password. The root owner or IAM administrator

needs to set the policy in the password policy page, which should allow the user to change their

password. Once it is enabled, the IAM user can always change their passwords from the AWS

console or CLI.

[http://docs.aws.amazon.com/IAM/latest/UserGuide/Using\_ManagingUserPwdSelf.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/Using_ManagingUserPwdSelf.html)

---

**QUESTION 42**

A user has created photo editing software and hosted it on EC2. The software accepts requests

from the user about the photo format and resolution and sends a message to S3 to enhance the

picture accordingly. Which of the below mentioned AWS services will help make a scalable

software with the AWS infrastructure in this scenario?

A. AWS Elastic Transcoder

B. AWS Simple Notification Service

C. AWS Simple Queue Service

D. AWS Glacier

**Answer: C**

**Explanation:**

Amazon Simple Queue Service \(SQS\) is a fast, reliable, scalable, and fully managed message

queuing service. SQS provides a simple and cost-effective way to decouple the components of

an application. The user can configure SQS, which will decouple the call between the EC2

application and S3. Thus, the application does not keep waiting for S3 to provide the data.

[http://aws.amazon.com/sqs/faqs/](http://aws.amazon.com/sqs/faqs/)

---



