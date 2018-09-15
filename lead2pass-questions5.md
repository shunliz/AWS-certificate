**QUESTION 171**

You need to migrate 10 million records in one hour into DynamoDB. All records are 1.5KB in size.

The data is evenly distributed across the partition key. How many write capacity units should you

provision during this batch load?

A. 6667

B. 4166

C. 5556

D. 2778

**Answer: C**

**Explanation:  
**You need 2 units to make a 1.5KB write, since you round up. You need 20 million total units to

perform this load. You have 3600 seconds to do so. Divide and round up for 5556.

---

**QUESTION 172**

You attempt to store an object in the US-STANDARD region in Amazon S3, and receive a

confirmation that it has been successfully stored. You then immediately make another API call

and attempt to read this object. S3 tells you that the object does not exist

What could explain this behavior?

A. US-STANDARD uses eventual consistency and it can take time for an object to be readable in

a bucket

B. Objects in Amazon S3 do not become visible until they are replicated to a second region.

C. US-STANDARD imposes a 1 second delay before new objects are readable.

D. You exceeded the bucket object limit, and once this limit is raised the object will be visible.

**Answer: A**

---

**QUESTION 173**

You are writing to a DynamoDB table and receive the following exception:"

ProvisionedThroughputExceededException". though according to your Cloudwatch metrics for

the table, you are not exceeding your provisioned throughput.

What could be an explanation for this?

A. You haven't provisioned enough DynamoDB storage instances

B. You're exceeding your capacity on a particular Range Key

C. You're exceeding your capacity on a particular Hash Key

D. You're exceeding your capacity on a particular Sort Key

E. You haven't configured DynamoDB Auto Scaling triggers

**Answer: C**

---

**QUESTION 174  
**

If an application is storing hourly log files from thousands of instances from a high traffic web site,

which naming scheme would give optimal performance on S3?

A. Sequential

B. instanceID\_log-HH-DD-MM-YYYY

C. instanceID\_log-YYYY-MM-DD-HH

D. HH-DD-MM-YYYY-log\_instanceID

E. YYYY-MM-DD-HH-log\_instanceID

**Answer: E**

---

**QUESTION 175**

You run an ad-supported photo sharing website using S3 to serve photos to visitors of your site.

At some point you find out that other sites have been linking to the photos on your site, causing

loss to your business.

What is an effective method to mitigate this?

A. Store photos on an EBS volume of the web server

B. Remove public read access and use signed URLs with expiry dates.

C. Use CloudFront distributions for static content.

D. Block the IPs of the offending websites in Security Groups.

**Answer: B**

---

**QUESTION 176**

Company A has an S3 bucket containing premier content that they intend to make available to

only paid subscribers of their website. The S3 bucket currently has default permissions of all

objects being private to prevent inadvertent exposure of the premier content to non-paying

website visitors. How can Company A provide only paid subscribers the ability to download a

premier content file in the S3 bucket?

A. Apply a bucket policy that grants anonymous users to download the content from the S3 bucket

B. Generate a pre-signed object URL for the premier content file when a paid subscriberrequests a

download

C. Add a bucket policy that requires Multi-Factor Authentication for requests to access the S3

bucket objects

D. Enable server side encryption on the S3 bucket for data protection against the non-paying

website visitors

**Answer: B**

---

**QUESTION 177**

Which of the following is chosen as the default region when making an API call with an AWS

SDK?

A. ap-northeast-1

B. us-west-2

C. us-east-1

D. eu-west-1

E. us-central-1

**Answer: C**

---

**QUESTION 178**

Games-R-Us is launching a new game app for mobile devices. Users will log into the game using

their existing Facebook account and the game will record player data and scoring information

directly to a DynamoDB table.

What is the most secure approach for signing requests to the DynamoDB API?

A. Create an IAM user with access credentials that are distributed with the mobile app to sign the

requests

B. Distribute the AWS root account access credentials with the mobile app to sign the requests

C. Request temporary security credentials using web identity federation to sign the requests

D. Establish cross account access between the mobile app and the DynamoDB table to sign the

requests

**Answer: C**

---

**QUESTION 179**

After launching an instance that you intend to serve as a NAT \(Network Address Translation\)

device in a public subnet you modify your route tables to have the NAT device be the target of

internet bound traffic of your private subnet. When you try and make an outbound connection to

the Internet from an instance in the private subnet, you are not successful.

Which of the following steps could resolve the issue?

A. Attaching a second Elastic Network interface \(ENI\) to the NAT instance, and placing it in the

private subnet

B. Attaching a second Elastic Network Interface \(ENI\) to the instance in the private subnet, and

placing it in the public subnet

C. Disabling the Source/Destination Check attribute on the NAT instance

D. Attaching an Elastic IP address to the instance in the private subnet

**Answer: C**

---

**QUESTION 180**

What happens, by default, when one of the resources in a CloudFormation stack cannot be

created?

A. Previously-created resources are kept but the stack creation terminates.

B. Previously-created resources are deleted and the stack creation terminates.

C. The stack creation continues, and the final results indicate which steps failed.

D. CloudFormation templates are parsed in advance so stack creation is guaranteed to succeed.

**Answer: B**

---

**QUESTION 181**

Which of the following statements about SQS is true?

A. Messages will be delivered exactly once and messages will be delivered in First in, First out

order

B. Messages will be delivered exactly once and message delivery order is indeterminate

C. Messages will be delivered one or more times and messages will be delivered in First in, First

out order

D. Messages will be delivered one or more times and message delivery order is indeterminate

**Answer: D**

---

**QUESTION 182**

A user is running a MySQL RDS instance. The user will not use the DB for the next 3 months.

How can the user save costs?

A. Pause the RDS activities from CLI until it is required in the future

B. Stop the RDS instance

C. Create a snapshot of RDS to launch in the future and terminate the instance now

D. Change the instance size to micro

**Answer: C**

**Explanation:**

The RDS instances unlike the AWS EBS backed instances cannot be stopped or paused.

The user needs to take the final snapshot, terminate the instance and launch a new instance in

the future from that snapshot.

---

**QUESTION 183**

In DynamoDB, if you create a table and request 10 units of write capacity and 200 units of read

capacity of provisioned throughput, how much would you be charged in US East \(Northern

Virginia\) Region?

A. $0.05 per hour

B. $0.10 per hour

C. $0.03 per hour

D. $0.15 per hour

**Answer: A**

**Explanation:**

To understand pricing in DynamoDB, consider the following example. If you create a table and

request 10 units of write capacity and 200 units of read capacity of provisioned throughput, you

would be charged:

$0.01 + \(4 x $0.01\) = $0.05 per hour

[http://aws.amazon.com/dynamodb/pricing/](http://aws.amazon.com/dynamodb/pricing/)

---

**QUESTION 184**

You have been doing a lot of testing of your VPC Network by deliberately failing EC2 instances to

test whether instances are failing over properly. Your customer who will be paying the AWS bill

for all this asks you if he being charged for all these instances. You try to explain to him how the

billing works on EC2 instances to the best of your knowledge. What would be an appropriate

response to give to the customer in regards to this?

A. Billing commences when Amazon EC2 AMI instance is completely up and billing ends as soon

as the instance starts to shutdown.

B. Billing commences when Amazon EC2 initiates the boot sequence of an AMI instance and

billing ends when the instance shuts down.

C. Billing only commences only after 1 hour of uptime and billing ends when the instance

terminates.

D. Billing commences when Amazon EC2 initiates the boot sequence of an AMI instance and

billing ends as soon as the instance starts to shutdown.

**Answer: B**

**Explanation:**

Billing commences when Amazon EC2 initiates the boot sequence of an AMI instance. Billing

ends when the instance shuts down, which could occur through a web services command, by

running "shutdown -h", or through instance failure.

[http://aws.amazon.com/ec2/faqs/\#Billing](http://aws.amazon.com/ec2/faqs/#Billing)

---

**QUESTION 185  
**AWS Elastic Load Balancer supports SSL termination.

A. True. For specific availability zones only.

B. False

C. True. For specific regions only

D. True. For all regions

**Answer: D**

**Explanation:**

You can configure your load balancer in ELB \(Elastic Load Balancing\) to use a SSL certificate in

order to improve your system security.The load balancer uses the certificate to terminate and

then decrypt requests before sending them to the back-end instances. Elastic Load Balancing

uses AWS Identity and Access Management \(IAM\) to upload your certificate to your load

balancer.

---

**QUESTION 186  
**A user has launched five instances with ELB. How can the user add the sixth EC2 instance to

ELB?

A. The user can add the sixth instance on the fly.

B. The user must stop the ELB and add the sixth instance.

C. The user can add the instance and change the ELB config file.

D. The ELB can only have a maximum of five instances.

**Answer: A**

**Explanation:**

Elastic Load Balancing automatically distributes incoming traffic across multiple EC2 instances.

You create a load balancer and register instances with the load balancer in one or more

Availability Zones. The load balancer serves as a single point of contact for clients. This enables

you to increase the availability of your application. You can add and remove EC2 instances from

your load balancer as your needs change, without disrupting the overall flow of information.

[http://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/SvcIntro.html](http://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/SvcIntro.html)

---

**QUESTION 187**

An organization has 500 employees. The organization wants to set up AWS access for each

department. Which of the below mentioned options is a possible solution?

A. Create IAM roles based on the permission and assign users to each role

B. Create IAM users and provide individual permission to each

C. Create IAM groups based on the permission and assign IAM users to the groups

D. It is not possible to manage more than 100 IAM users with AWS

**Answer: C  
Explanation:**

An IAM group is a collection of IAM users. Groups let the user specify permissions for a collection

of users, which can make it easier to manage the permissions for those users.

[http://docs.aws.amazon.com/IAM/latest/UserGuide/Using\_WorkingWithGroupsAndUsers.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/Using_WorkingWithGroupsAndUsers.html)

---

**QUESTION 188  
**How long can you keep your Amazon SQS messages in Amazon SQS queues?

A. From 120 secs up to 4 weeks

B. From 10 secs up to 7 days

C. From 60 secs up to 2 weeks

D. From 30 secs up to 1 week

**Answer: C**

**Explanation:**

The SQS message retention period is configurable and can be set anywhere from 1 minute to 2

weeks. The default is 4 days and once the message retention limit is reached your messages will

be automatically deleted. The option for longer message retention provides greater flexibility to

allow for longer intervals between message production and consumption.

[https://aws.amazon.com/sqs/faqs/  
](https://aws.amazon.com/sqs/faqs/)

---

**QUESTION 189**

In regard to DynamoDB, which of the following statements is correct?

A. An Item should have at least two value sets, a primary key and another attribute.

B. An Item can have more than one attributes.

C. A primary key should be single-valued.

D. An attribute can have one or several other attributes.

**Answer: B  
Explanation:**

In Amazon DynamoDB, a database is a collection of tables. A table is a collection of items and

each item is a collection of attributes.

[http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DataModel.html](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DataModel.html)

---

**QUESTION 190**

Which one of the following statements is NOT an advantage of DyanamoDB being built on Solid

State Drives:

A. serve high-scale request workloads

B. low request pricing

C. high I/O performance of WebApp on EC2 instance

D. low-latency response times

**Answer: C**

**Explanation:**

In DynamoDB, SSDs help achieve design goals of predictable low-latency response times for

storing and accessing data at any scale. The high I/O performance of SSDs also enables to serve

high-scale request workloads cost efficiently, and to pass this efficiency along in low request

pricing.

[http://aws.amazon.com/dynamodb/faqs/](http://aws.amazon.com/dynamodb/faqs/)

---



