1, An IAM user is trying to perform an action on an object belonging to some other root account’s bucket. Which of the below mentioned options will AWS S3 not verify?

1. [ ] The object owner has provided access to the IAM user

2. [x] Permission provided by the parent of the IAM user on the bucket

3. [ ] Permission provided by the bucket owner to the IAM user

4. [ ] Permission provided by the parent of the IAM user

> If the IAM user is trying to perform some action on the object belonging to another AWS user’s bucket, S3 will verify whether the owner of the IAM user has given sufficient permission to him. It also verifies the policy for the bucket as well as the policy defined by the object owner.[http://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-auth-workflow-object-operation.html](http://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-auth-workflow-object-operation.html)

2, Select the correct set of options. These are the initial settings for the default security group:

1. [ ] Allow all inbound traffic, Allow no outbound traffic and Allow instances associated with this security group to talk to each other.
2. [ ] Allow all inbound traffic, Allow all outbound traffic and Does NOT allow instances associated with this security group to talk to each other.
3. [x] Allow no inbound traffic, Allow all outbound traffic and Allow instances associated with this security group to talk to each other.
4. [ ] Allow no inbound traffic, Allow all outbound traffic and Does NOT allow instances associated with this security group to talk to each other.

> > Refer to [http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html\#default-security-group](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html#default-security-group)

3, Placement Groups: enables applications to participate in a low-latency, 10 Gbps network. Which of below statements is false.

1. [ ] Not all of the instance types that can be launched into a placement group.

2. [x] You can move an existing instance into a placement group by specify parameter of placement group.

3. [ ] A placement group can't span multiple Availability Zones.

4. [ ] A placement group can span peered VPCs.

> > Refer to [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html)

4, What about below is false for AWS SLA

1. [ ] EC2 availability is guarantee to 99.95%.
2. [x] S3 availability is guarantee to 99.95%.
3. [ ] EBS availability is guarantee to 99.95%.
4. [ ] RDS multi-AZ is guarantee to 99.95%.
   S3 SLA is 99.9%. Refer to [http://aws.amazon.com/s3/sla/](http://aws.amazon.com/s3/sla/)

5, About the charge of Elastic IP Address, which of the following is true?

 1. [ ] You are charged for each Elastic IP addressed.
 1. [ ] Elastic IP addresses can always be used with no charge.
 1. [ ] You can have 5 Elastic IP addresses per region with no charge.
 1. [x] You can have one Elastic IP (EIP) address associated with a running instance at no charge.
 > > Refer to http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html

6, You have assigned one Elastic IP to your EC2 instance. Now we need to restart the VM without EIP changed. Which of below you should not do?

 1. [x] Reboot and stop/start both works.
 1. [ ] When the instance is in VPC public subnets, stop/start works.
 1. [ ] When the instance is in VPC private subnet, stop/start works.
 1. [ ] Reboot the instance.
 
 > > Refer to http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-lifecycle.html#lifecycle-differences
 
 7, EC2 role
 
 1. [ ] Setup an IAM group with restricted AWS API access and put the instance in the group at launch.
 1. [ ] Pass access AWS credentials in the User Data field when the instance is launched.
 1. [ ] Setup an IAM user for the instance to restrict access to AWS API and assign it at launch.
 1. [x] Launch an instance with an AWS Identity and Aceess Management (IAM) role to restrict AWS API access for the instance.
> > Refer to http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html

8, Which of the below mentioned steps will not be performed while creating the AMI of instance stored-backend?

 1. [ ] Upload the bundled volume.
 1. [x] Define the AMI launch permissions.
 1. [ ] Bundle the volume.
 1. [ ] Register the AMI.
 
 > > Refer to http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/creating-an-ami-instance-store.html
 
 9, The user just started an instance at 3 PM. Between 3 PM to 5 PM, he stopped and started the instance twice. During the same period, he has run the linux reboot command by ssh once and triggered reboot from AWS console once. For how many instance hours will AWS charge this user?
 
  1. [ ] 3
  1. [x] 4
  1. [ ] 5
  1. [ ] 2
  
  > > Refer to http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Stop_Start.html
  
 10, Which service or feature provides the fastest method of getting the
data into Amazon Glacier?
You are working with a customer who has 10 TB of archival data that they want to migrate to Amazon Glacier. The customer has a 1Mbps connection to the Internet. Which service or feature provides the fastest method of getting the data into Amazon Glacier?
A. Amazon Glacier multipart upload
B. AWS Storage Gateway
C. VM Import/Export
D. AWS Import/Export

Answer: D, mail the storage to AWS storage team to help import data.
