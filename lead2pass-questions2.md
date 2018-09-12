**QUESTION 38  
**

Can one instance be registered with two ELBs in the same region?

A. No

B. Yes, provided both ELBs have the same health check configuration

C. Yes, always

D. Yes, provided both ELBs are in the same AZ

**Answer: C  
**

**Explanation:  
**

Yes, it is possible to have one instance part of two separate ELBs, though both ELBs have

different configurations. ELBs are never launched in specific zones.

[http://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/enable-disable-az.html](http://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/enable-disable-az.html)

---

**QUESTION 39  
**

What does Amazon SQS provide?

A. An asynchronous message queue service.

B. A Simple Query Server, managed directly by Amazon Web Services.

C. None of these.

D. A synchronous message queue service.

**Answer: A  
**

**Explanation:  
**

Amazon SQS stands for Simple Queue Services, and provides a cost-effective way to decouple

the components of your application through an asynchronous message queue service

[http://aws.amazon.com/sqs/](http://aws.amazon.com/sqs/)

---

**QUESTION 40  
**

A user is trying to create a list of IAM users with the AWS console. When the IAM users are

created which of the below mentioned credentials will be enabled by default for the user?

A. IAM access key and secret access key

B. IAM X.509 certificates

C. Nothing. Everything is disabled by default

D. IAM passwords

**Answer: C  
**

**Explanation:  
**

Newly created IAM users have no password and no access key \(access key ID and secret

access key\). If the user needs to administer your AWS resources using the AWS Management

Console, you can create a password for the user. If the user needs to interact with AWS

programmatically \(using the command line interface \(CLI\), the AWS SDK, or service-specific

APIs\), you can create an access key for that user. The credentials you create for users are what

they use to uniquely identify themselves to AWS.

[http://docs.aws.amazon.com/IAM/latest/UserGuide/Using\_WorkingWithGroupsAndUsers.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/Using_WorkingWithGroupsAndUsers.html)

---

**QUESTION 41  
**

Bob is an IAM user who has access to the EC2 services. Admin is an IAM user who has access

to all the AWS services including IAM. Can Bob change his password?

A. No, the IAM user can never change the password

B. Yes, provided Admin has given Bob access to change his password

C. Yes, only from AWS CLI

D. Yes, only from the AWS console

**Answer: B  
**

**Explanation:  
**

The IAM users by default cannot change their password. The root owner or IAM administrator

needs to set the policy in the password policy page, which should allow the user to change their

password. Once it is enabled, the IAM user can always change their passwords from the AWS

console or CLI.

[http://docs.aws.amazon.com/IAM/latest/UserGuide/Using\_ManagingUserPwdSelf.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/Using_ManagingUserPwdSelf.html)

---

**QUESTION 42  
**

A user has created photo editing software and hosted it on EC2. The software accepts requests

from the user about the photo format and resolution and sends a message to S3 to enhance the

picture accordingly. Which of the below mentioned AWS services will help make a scalable

software with the AWS infrastructure in this scenario?

A. AWS Elastic Transcoder

B. AWS Simple Notification Service

C. AWS Simple Queue Service

D. AWS Glacier

**Answer: C  
**

**Explanation:  
**

Amazon Simple Queue Service \(SQS\) is a fast, reliable, scalable, and fully managed message

queuing service. SQS provides a simple and cost-effective way to decouple the components of

an application. The user can configure SQS, which will decouple the call between the EC2

application and S3. Thus, the application does not keep waiting for S3 to provide the data.

[http://aws.amazon.com/sqs/faqs/](http://aws.amazon.com/sqs/faqs/)

---

**QUESTION 43**

A user has created a blank EBS volume in the US-East-1 region. The user is unable to attach the

volume to a running instance in the same region. What could be the possible reason for this?

A. The instance must be in a running state. It is required to stop the instance to attach volume

B. The AZ for the instance and volume are different

C. The instance is from an instance store backed AMI

D. The instance has enabled the volume attach protection

Answer: B

Explanation:

An EBS volume provides persistent data storage. The user can attach a volume to any instance

provided they are both in the same AZ. Even if they are in the same region but in a different AZ, it

will not be able to attach the volume to that instance.

[http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html)

---

**QUESTION 44**

In DynamoDB, could you use IAM to grant access to Amazon DynamoDB resources and API

actions?

A. Yes

B. Depended to the type of access

C. In DynamoDB there is no need to grant access

D. No

**Answer: A**

**Explanation:**

Amazon DynamoDB integrates with AWS Identity and Access Management \(IAM\).

You can use AWS IAM to grant access to Amazon DynamoDB resources and API actions.

To do this, you first write an AWS IAM policy, which is a document that explicitly lists the

permissions you want to grant. You then attach that policy to an AWS IAM user or role.

[http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/UsingIAMWithDDB.html](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/UsingIAMWithDDB.html)

---

**QUESTION 45**

A user is planning to host a mobile game on EC2 which sends notifications to active users on

either high score or the addition of new features. The user should get this notification when he is

online on his mobile device. Which of the below mentioned AWS services can help achieve this

functionality?

A. AWS Simple Notification Service.

B. AWS Simple Queue Service.

C. AWS Mobile Communication Service.

D. AWS Simple Email Service.

**Answer: A**

**Explanation:**

Amazon Simple Notification Service \(Amazon SNS\) is a fast, flexible, and fully managed push

messaging service. Amazon SNS makes it simple and cost-effective to push to mobile devices,

such as iPhone, iPad, Android, Kindle Fire, and internet connected smart devices, as well as

pushing to other distributed services.

[http://aws.amazon.com/sns](http://aws.amazon.com/sns)

---

**QUESTION 46**

An organization is setting up their website on AWS. The organization is working on various

security measures to be performed on the AWS EC2 instances. Which of the below mentioned

security mechanisms will not help the organization to avoid future data leaks and identify security

weaknesses?

A. Perform SQL injection for application testing.

B. Run penetration testing on AWS with prior approval from Amazon.

C. Perform a hardening test on the AWS instance.

D. Perform a Code Check for any memory leaks.

**Answer: D**

**Explanation:**

AWS security follows the shared security model where the user is as much responsible as

Amazon. Since Amazon is a public cloud it is bound to be targeted by hackers. If an organization

is planning to host their application on AWS EC2, they should perform the below mentioned

security checks as a measure to find any security weakness/data leaks:

Perform penetration testing as performed by attackers to find any vulnerability. The organization

must take an approval from AWS before performing penetration testing Perform hardening testing

to find if there are any unnecessary ports open Perform SQL injection to find any DB security

issues

The code memory checks are generally useful when the organization wants to improve the

application performance.

[http://aws.amazon.com/security/penetration-testing/](http://aws.amazon.com/security/penetration-testing/)

---

**QUESTION 47**

A root account owner is trying to setup an additional level of security for all his IAM users. Which

of the below mentioned options is a recommended solution for the account owner?

A. Enable access key and secret access key for all the IAM users

B. Enable MFA for all IAM users

C. Enable the password for all the IAM users

D. Enable MFA for the root account

**Answer: B**

**Explanation:**

Multi-Factor Authentication adds an extra level of security for all the users. The user can enable

MFA for all IAM users which ensures that each user has to provide an extra six digit code for

authentication.

[http://docs.aws.amazon.com/IAM/latest/UserGuide/Using\_ManagingMFA.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/Using_ManagingMFA.html)

---

