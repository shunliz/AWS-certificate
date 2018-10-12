**Question 1**

REST or Query requests are HTTP or HTTPS requests that use an HTTP verb \(such as GET or POST\) and a parameter named Action or Operation that specifies the API you are calling.

1. FALSE
2. **TRUE**

**Question 2**

Through which of the following interfaces is AWS Identity and Access Management available?

A\) AWS Management Console

B\) Command line interface \(CLI\)

C\) IAM Query API

D\) Existing libraries

1. Only through Command line interface \(CLI\)
2. A, B and C
3. A and C
4. **All of the above**

Question 3

Which of the following programming languages have an officially supported AWS SDK? Choose 2 answers

1. **PHP**
2. Pascal
3. **Java**
4. SQL
5. Perl

**Question 4**

HTTP Query-based requests are HTTP requests that use the HTTP verb GET or POST and a Query parameter named\_\_\_\_\_\_\_\_\_\_\_\_\_.

1. **Action**
2. Value
3. Reset
4. Retrieve

**Question 5**

An AWS customer is deploying an application that is composed of an AutoScaling group of EC2 Instances. The customers security policy requires that every outbound connection from these instances to any other service within the customers Virtual Private Cloud must be authenticated using a unique x.509 certificate that contains the specific instanceid. In addition an x.509 certificates must be designed by the customer’s Key management service in order to be trusted for authentication. Which of the following configurations will support these requirements?

1. Configure an IAM Role that grants access to an Amazon S3 object containing a signed certificate and configure the Auto Scaling group to launch instances with this role. Have the instances bootstrap get the certificate from Amazon S3 upon first boot.
2. Embed a certificate into the Amazon Machine Image that is used by the Auto Scaling group. Have the launched instances generate a certificate signature request with the instance’s assigned instance-id to the Key management service for signature.
3. **Configure the Auto Scaling group to send an SNS notification of the launch of a new instance to the trusted key management service. Have the Key management service generate a signed certificate and send it directly to the newly launched instance.**
4. Configure the launched instances to generate a new certificate upon first boot. Have the Key management service poll the AutoScaling group for associated instances and send new instances a certificate signature that contains the specific instance-id.

**Question 6**

When assessing an organization AWS use of AWS API access credentials which of the following three credentials should be evaluated? Choose 3 answers

1. Key pairs
2. **Console passwords**
3. **Access keys**
4. **Signing certificates**
5. Security Group memberships \(required for EC2 instance access\)

**Question 7**

Your organization’s security policy requires that all privileged users either use frequently rotated passwords or one-time access credentials in addition to username/password. Which two of the following options would allow an organization to enforce this policy for AWS users? Choose 2 answers

1. **Configure multi-factor authentication for privileged IAM users**
2. **Create IAM users for privileged accounts \(**can set password policy**\)**
3. Implement identity federation between your organization’s Identity provider leveraging the IAM Security Token Service
4. Enable the IAM single-use password policy option for privileged users \(no such option the password expiration can be set from 1 to 1095 days\)

**Question 8**

A company needs to deploy services to an AWS region which they have not previously used. The company currently has an AWS identity and Access Management \(IAM\) role for the Amazon EC2 instances, which permits the instance to have access to Amazon DynamoDB. The company wants their EC2 instances in the new region to have the same privileges. How should the company achieve this?

1. Create a new IAM role and associated policies within the new region
2. **Assign the existing IAM role to the Amazon EC2 instances in the new region**
3. Copy the IAM role and associated policies to the new region and attach it to the instances
4. Create an Amazon Machine Image \(AMI\) of the instance and copy it to the desired region using the AMI Copy feature

**Question 9**

When you use the AWS Management Console to delete an IAM user, IAM also deletes any signing certificates and any access keys belonging to the user.

1. FALSE
2. This is configurable
3. **TRUE**

**Question 10**

You are setting up a blog on AWS. In which of the following scenarios will you need AWS credentials? \(Choose 3\)

1. **Sign in to the AWS management console to launch an Amazon EC2 instance**
2. Sign in to the running instance to instance some software \(needs ssh keys\)
3. **Launch an Amazon RDS instance**
4. Log into your blog’s content management system to write a blog post \(need to authenticate using blog authentication\)
5. **Post pictures to your blog on Amazon S3**

**Question 11**

You have a business-to-business web application running in a VPC consisting of an Elastic Load Balancer \(ELB\), web servers, application servers and a database. Your web application should only accept traffic from predefined customer IP addresses. Which two options meet this security requirement? Choose 2 answers

1. Configure web server VPC security groups to allow traffic from your customers’ IPs \(
   Web server is behind the ELB and customer IPs will never reach web servers\)
2. **Configure your web servers to filter traffic based on the ELB’s “X-forwarded-for” header**
   \(get the customer IPs and create a custom filter to restrict access. Refer [link](https://aws.amazon.com/premiumsupport/knowledge-center/log-client-ip-load-balancer-apache/)\)
3. **Configure ELB security groups to allow traffic from your customers’ IPs and deny all outbound traffic**
   \(ELB will see the customer IPs so can restrict access, deny all is basically have no rules in outbound traffic, implicit, and its stateful so would work\)
4. Configure a VPC NACL to allow web traffic from your customers’ IPs and deny all outbound traffic \(NACL is stateless, deny all will not work\)

**Question 12**

A user has created a VPC with public and private subnets using the VPC wizard. Which of the below mentioned statements is true in this scenario?

1. AWS VPC will automatically create a NAT instance with the micro size
2. **VPC bounds the main route table with a private subnet and a custom route table with a public subnet**
3. User has to manually create a NAT instance
4. VPC bounds the main route table with a public subnet and a custom route table with a private subnet

**Question 13**

A user has launched an EC2 instance and installed a website with the Apache webserver. The webserver is running but the user is not able to access the website from the Internet. What can be the possible reason for this failure?

1. **The security group of the instance is not configured properly.**
2. The instance is not configured with the proper key-pairs.
3. The Apache website cannot be accessed from the Internet.
4. Instance is not configured with an elastic IP.



