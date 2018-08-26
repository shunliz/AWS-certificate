# AWS Security Best Practices

## Know the AWS Shared Responsibility Model

**assets:**

• Facilities

• Physical security of hardware

• Network infrastructure

• Virtualization infrastructure

**assets of EC2:**

• Amazon Machine Images \(AMIs\)

• Operating systems

• Applications

• Data in transit

• Data at rest

• Data stores

• Credentials

• Policies and configuration



**three main categories of AWS service**

**Infrastructure Services:** This category includes compute services, such as Amazon EC2, and related services, such as Amazon Elastic Block Store \(Amazon EBS\), Auto Scaling, and Amazon Virtual Private Cloud \(Amazon VPC\). With these services, you can architect and builda cloud infrastructure using technologies similar to and largely compatible with on-premises solutions. You control the operating system, and you configure and operate any identity management system that provides access to the user layer of the virtualization stack.



**Container Services: **Services in this category typically run onseparate Amazon EC2 or other infrastructure instances, but sometimes you don’t manage the operating system or the platform layer. AWS provides managed service for these application “containers”. You are responsible for setting up and managing network controls, such as firewall rules, and for managing platform-level identity and access management separately from IAM. Examples of container services include Amazon Relational Database Services \(Amazon RDS\), Amazon Elastic Map Reduce \(Amazon EMR\) and AWS Elastic Beanstalk



**Abstracted Services: **This category includes high-level storage, database, and messaging services, such as Amazon Simple Storage Service \(Amazon S3\), Amazon Glacier, Amazon DynamoDB, Amazon Simple Queuing Service \(Amazon SQS\), and Amazon Simple Email Service \(Amazon SES\). These services abstract the platform or management layer on which you can build and operate cloud applications. You access the endpoints of these abstracted services using AWS APIs, and AWS manages the underlying service components or the operating system on which they reside. You share the underlying infrastructure, and abstracted services provide a multi- tenant platform which isolates your data in a secure fashion and provides for powerful integration withIAM



### Shared Responsibility Model for Infrastructure Services![](/assets/awsshare1.png)

### Shared Responsibility Model for Container Services![](/assets/awsshare2.png)

### Shared Responsibility Model for Abstracted Services![](/assets/awsshare3.png)



