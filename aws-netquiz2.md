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

**Question 14**

A user has created a VPC with public and private subnets using the VPC wizard. Which of the below mentioned statements is true in this scenario?

1. AWS VPC will automatically create a NAT instance with the micro size
2. **VPC bounds the main route table with a private subnet and a custom route table with a public subnet**
3. User has to manually create a NAT instance
4. VPC bounds the main route table with a public subnet and a custom route table with a private subnet

**Question 15**

A user has created a VPC with CIDR 20.0.0.0/16. The user has created one subnet with CIDR 20.0.0.0/16 by mistake. The user is trying to create another subnet of CIDR 20.0.0.1/24. How can the user create the second subnet?

1. There is no need to update the subnet as VPC automatically adjusts the CIDR of the first subnet based on the second subnet’s CIDR
2. The user can modify the first subnet CIDR from the console
3. **It is not possible to create a second subnet as one subnet with the same CIDR as the VPC has been created**
4. The user can modify the first subnet CIDR with AWS CLI

**Question 16**

A user has setup a VPC with CIDR 20.0.0.0/16. The VPC has a private subnet \(20.0.1.0/24\) and a public subnet \(20.0.0.0/24\). The user’s data centre has CIDR of 20.0.54.0/24 and 20.1.0.0/24. If the private subnet wants to communicate with the data centre, what will happen?

1. It will allow traffic communication on both the CIDRs of the data centre
2. It will not allow traffic with data centre on CIDR 20.1.0.0/24 but allows traffic communication on 20.0.54.0/24
3. It will not allow traffic communication on any of the data centre CIDRs
4. **It will allow traffic with data centre on CIDR 20.1.0.0/24 but does not allow on 20.0.54.0/24**
   \(as the CIDR block would be overlapping\)

**Question 17**

A user has created a subnet in VPC and launched an EC2 instance within it. The user has not selected the option to assign the IP address while launching the instance. Which of the below mentioned statements is true with respect to the Instance requiring access to the Internet?

1. The instance will always have a public DNS attached to the instance by default
2. The user can directly attach an elastic IP to the instance
3. The instance will never launch if the public IP is not assigned
4. **The user would need to create an internet gateway and then attach an elastic IP to the instance to connect from internet**

**Question 18**

A user has created a VPC with CIDR 20.0.0.0/16 using VPC Wizard. The user has created a public CIDR \(20.0.0.0/24\) and a VPN only subnet CIDR \(20.0.1.0/24\) along with the hardware VPN access to connect to the user’s data centre. Which of the below mentioned components is not present when the VPC is setup with the wizard?

1. Main route table attached with a VPN only subnet
2. **A NAT instance configured to allow the VPN subnet instances to connect with the internet**
3. Custom route table attached with a public subnet
4. An internet gateway for a public subnet

**Question 19**

A user has created a VPC with CIDR 20.0.0.0/16. The user has created public and VPN only subnets along with hardware VPN access to connect to the user’s datacenter. The user wants to make so that all traffic coming to the public subnet follows the organization’s proxy policy. How can the user make this happen?

1. Setting up a NAT with the proxy protocol and configure that the public subnet receives traffic from NAT
2. Setting up a proxy policy in the internet gateway connected with the public subnet
3. It is not possible to setup the proxy policy for a public subnet
4. **Setting the route table and security group of the public subnet which receives traffic from a virtual private gateway**

**Question 20**

Which two components provide connectivity with external networks? When attached to an Amazon VPC which two components provide connectivity with external networks? Choose 2 answers

1. Elastic IPs \(EIP\) \(Does not provide connectivity, public IP address will do as well\)
2. NAT Gateway \(NAT\) \(Not Attached to VPC and still needs IGW\)
3. **Internet Gateway \(IGW\)**
4. **Virtual Private Gateway \(VGW\)**

**Question 21**

If you want to launch Amazon Elastic Compute Cloud \(EC2\) Instances and assign each Instance a predetermined private IP address you should:

1. Assign a group or sequential Elastic IP address to the instances
2. Launch the instances in a Placement Group
3. **Launch the instances in the Amazon virtual Private Cloud \(VPC\)**
4. Use standard EC2 instances since each instance gets a private Domain Name Service \(DNS\) already
5. Launch the Instance from a private Amazon Machine image \(AMI\)

**Question 22**

You have an Amazon VPC with one private subnet and one public subnet with a Network Address Translator \(NAT\) server. You are creating a group of Amazon Elastic Cloud Compute \(EC2\) instances that configure themselves at startup via downloading a bootstrapping script from Amazon Simple Storage Service \(S3\) that deploys an application via GIT. Which setup provides the highest level of security?

1. **Amazon EC2 instances in private subnet, no EIPs, route outgoing traffic via the NAT**
2. Amazon EC2 instances in public subnet, no EIPs, route outgoing traffic via the Internet Gateway \(IGW\)
3. Amazon EC2 instances in private subnet, assign EIPs, route outgoing traffic via the Internet Gateway \(IGW\)
4. Amazon EC2 instances in public subnet, assign EIPs, route outgoing traffic via the NAT

**Question 23**

Can I move a Reserved Instance from one Region to another?

1. **No**
2. Only if they are moving into GovCloud
3. Yes
4. Only if they are moving to US East from another region

**Question 24**

A user has enabled termination protection on an EC2 instance. The user has also set Instance initiated shutdown behavior to terminate. When the user shuts down the instance from the OS, what will happen?

1. The OS will shutdown but the instance will not be terminated due to protection
2. **It will terminate the instance**
3. It will not allow the user to shutdown the instance from the OS
4. It is not possible to set the termination protection when an Instance initiated shutdown is set to Terminate

**Question 25**

A user has launched an EC2 instance and deployed a production application in it. The user wants to prohibit any mistakes from the production team to avoid accidental termination. How can the user achieve this?

1. **The user can the set DisableApiTermination attribute to avoid accidental termination**
2. It is not possible to avoid accidental termination
3. The user can set the Deletion termination flag to avoid accidental termination
4. The user can set the InstanceInitiatedShutdownBehavior flag to avoid accidental termination

**Question 26**

You have been doing a lot of testing of your VPC Network by deliberately failing EC2 instances to test whether instances are failing over properly. Your customer who will be paying the AWS bill for all this asks you if he being charged for all these instances. You try to explain to him how the billing works on EC2 instances to the best of your knowledge. What would be an appropriate response to give to the customer in regards to this?

1. Billing commences when Amazon EC2 AMI instance is completely up and billing ends as soon as the instance starts to shutdown.
2. **Billing commences when Amazon EC2 initiates the boot sequence of an AMI instance and billing ends when the instance shuts down.**
3. Billing only commences only after 1 hour of uptime and billing ends when the instance terminates.
4. Billing commences when Amazon EC2 initiates the boot sequence of an AMI instance and billing ends as soon as the instance starts to shutdown.

**Question 27**

When you view the block device mapping for your instance, you can see only the EBS volumes, not the instance store volumes.

1. Depends on the instance type
2. FALSE
3. Depends on whether you use API call
4. **TRUE**

**Question 28**

Which of the following will occur when an EC2 instance in a VPC \(Virtual Private Cloud\) with an associated Elastic IP is stopped and started? \(Choose 2 answers\)

1. The Elastic IP will be dissociated from the instance
2. **All data on instance-store devices will be lost**
3. All data on EBS \(Elastic Block Store\) devices will be lost
4. The ENI \(Elastic Network Interface\) is detached
5. **The underlying host for the instance is changed**

**Question 29**

A user has created numerous EBS volumes. What is the general limit for each AWS account for the maximum number of EBS volumes that can be created?

1. 10000
2. **5000**
3. 100
4. 1000



**Question 30**

Select the correct set of steps for exposing the snapshot only to specific AWS accounts

1. Select Public for all the accounts and check mark those accounts with whom you want to expose the snapshots and click save.
2. **Select Private and enter the IDs of those AWS accounts, and click Save.**
3. Select Public, enter the IDs of those AWS accounts, and click Save.
4. Select Public, mark the IDs of those AWS accounts as private, and click Save.



