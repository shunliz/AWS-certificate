**QUESTION 261**

You have a video transcoding application running on Amazon EC2. Each instance polls a queue to find out which video should be transcoded, and then runs a transcoding process. If this process is interrupted, the video will be transcoded by another instance based on the queuing system. You have a large backlog of videos which need to be transcoded and would like to reduce this backlog by adding more instances. You will need these instances only until the backlog is reduced. Which type of Amazon EC2 instances should you use to reduce the backlog in the most cost efficient way?

A. Reserved instances  
 B. Spot instances  
 C. Dedicated instances  
 D. On-demand instances

**Answer: B**

---

**QUESTION 262**

A customer has established an AWS Direct Connect connection to AWS. The link is up and routes are being advertised from the customer’s end, however the customer is unable to connect from EC2 instances inside its VPC to servers residing in its datacenter.  
Which of the following options provide a viable solution to remedy this situation? \(Choose 2 answers\)

A. Add a route to the route table with an iPsec VPN connection as the target.

B. Enable route propagation to the virtual pinnate gateway \(VGW\).

C. Enable route propagation to the customer gateway \(CGW\).

D. Modify the route table of all Instances using the ‘route’ command.

E. Modify the Instances VPC subnet route table by adding a route back to the customer’s on-premises environment.

**Answer: B,E**

---

**QUESTION 263**

An International company has deployed a multi-tier web application that relies on DynamoDB in a single region For regulatory reasons they need disaster recovery capability In a separate region with a Recovery Time Objective of 2 hours and a Recovery Point Objective of 24 hours They should synchronize their data on a regular basis and be able to provision me web application rapidly using CloudFormation.  
The objective is to minimize changes to the existing web application, control the throughput of DynamoDB used for the synchronization of data and synchronize only the modified elements.  
Which design would you choose to meet these requirements?

A. Use AWS data Pipeline to schedule a DynamoDB cross region copy once a day. create a Lastupdated’ attribute in your DynamoDB table that would represent the timestamp of the last update and use it as a filter.

B. Use EMR and write a custom script to retrieve data from DynamoDB in the current region using a SCAN operation and push it to DynamoDB in the second region.

C. Use AWS data Pipeline to schedule an export of the DynamoDB table to S3 in the current region once a day then schedule another task immediately after it that will import data from S3 to DynamoDB in the other region.

D. Send also each Ante into an SQS queue in me second region; use an auto-scaiing group behind the SQS queue to replay the write in the second region.

**Answer: C**

---

**QUESTION 264**

If you’re unable to connect via SSH to your EC2 instance, which of the following should you check and possibly correct to restore connectivity?

A. Adjust Security Group to permit egress traffic over TCP port 443 from your IP.

B. Configure the IAM role to permit changes to security group settings.

C. Modify the instance security group to allow ingress of ICMP packets from your IP.

D. Adjust the instance’s Security Group to permit ingress traffic over port 22 from your IP.

E. Apply the most recently released Operating System security patches.

**Answer: D**

---

**QUESTION 265**

Your company produces customer commissioned one-of-a-kind skiing helmets combining nigh fashion with custom technical enhancements Customers can show off their  
Individuality on the ski slopes and have access to head-up-displays. GPS rear-view cams and any other technical innovation they wish to embed in the helmet.  
The current manufacturing process is data rich and complex including assessments to ensure that the custom electronics and materials used to assemble the helmets are to the highest standards Assessments are a mixture of human and automated assessments you need to add a new set of assessment to model the failure modes of the custom electronics using GPUs with CUDA. across a cluster of servers with low latency networking.  
What architecture would allow you to automate the existing process using a hybrid approach and ensure that the architecture can support the evolution of processes over time?

A. Use AWS Data Pipeline to manage movement of data &meta-data and assessments Use an auto-scaling group of G2 instances in a placement group.

B. Use Amazon Simple Workflow \(SWF\) to manages assessments, movement of data &meta-data Use an auto-scaling group of G2 instances in a placement group.

C. Use Amazon Simple Workflow \(SWF\) to manages assessments movement of data &meta-data Use an auto-scaling group of C3 instances with SR-IOV \(Single Root I/O Virtualization\).

D. Use AWS data Pipeline to manage movement of data & meta-data and assessments use auto-scaling group of C3 with SR-IOV \(Single Root I/O virtualization\).

**Answer: B**

\(SR-IOV is a method of device virtualization that provides higher I/O performance and lower CPU utilization when compared to traditional virtualized network interfaces\)

---

**QUESTION 266**

Your startup wants to implement an order fulfillment process for selling a personalized gadget that needs an average of 3-4 days to produce with some orders taking up to 6 months you expect 10 orders per day on your first day. 1000 orders per day after 6 months and 10,000 orders after 12 months.  
Orders coming in are checked for consistency men dispatched to your manufacturing plant for production quality control packaging shipment and payment processing If the product does not meet the quality standards at any stage of the process employees may force the process to repeat a step Customers are notified via email about order status and any critical issues with their orders such as payment failure.  
Your case architecture includes AWS Elastic Beanstalk for your website with an RDS MySQL instance for customer data and orders.  
How can you implement the order fulfillment process while making sure that the emails are delivered reliably?

A. Add a business process management application to your Elastic Beanstalk app servers and re-use the ROS database for tracking order status use one of the Elastic Beanstalk instances to send emails to customers.

B. Use SWF with an Auto Scaling group of activity workers and a decider instance in another Auto Scaling group with min/max=1 Use the decider instance to send emails to customers.

C. Use SWF with an Auto Scaling group of activity workers and a decider instance in another Auto Scaling group with min/max=1 use SES to send emails to customers.

D. Use an SQS queue to manage all process tasks Use an Auto Scaling group of EC2 Instances that poll the tasks and execute them. Use SES to send emails to customers.

**Answer: C**

---

**QUESTION 267**

Will my standby RDS instance be in the same Region as my primary?

A Only for Oracle RDS types

B Yes

C Only if configured at launch

D No

**Answer： B**

---

**QUESTION 268**

Out of the stripping options available for the EBS volumes, which one has the following disadvantage: ‘Doubles the amount of I/O required from the instance to EBS compared to RAID 0, because you’re mirroring all writes to a pair of volumes, limiting how much you can stripe.’ ?

A Raid 0

B RAID 1+0 \(RAID 10\)

C Raid 1

D Raid 2

**Answer: B**

---

**QUESTION 269**

Can Amazon S3 uploads resume on failure or do they need to restart?

A Restart from beginning

B You can resume them, if you flag the “resume on failure” option before uploading.

C Resume on failure

D Depends on the file size

**Answer: A**

---

**QUESTION 270**

What is the maximum write throughput I can provision for a single DynamoDB table?

A 1,000 write capacity units

B 100,000 write capacity units

C DynamoDB is designed to scale without limits, but if you go beyond 10,000 you have to contact AWS first.—

D 10,000 write capacity units

**Answer: D**

---

**QUESTION 271**

Is Federated Storage Engine currently supported by Amazon RDS for MySQL?

A Only for Oracle RDS instances

B No

C Yes

D Only in VPC

**Answer: B**

---

**QUESTION 272**

You must increase storage size in increments of at least**\_**%

A 40

B 30

C 10

D 20

**Answer: C**

---

**QUESTION 273**

You have an application running in us-west-2 that requires six Amazon Elastic Compute Cloud \(EC2\) instances running at all times. With three Availability Zones available in that region \(us-west-2a, us-west-2b, and us-west-2c\), which of the following deployments provides 100 percent fault tolerance if any single Availability Zone in us-west-2 becomes unavailable?Choose 2 answers

A. Us-west-2a with two EC2 instances, us-west-2b with two EC2 instances, and us-west-2c with two EC2 instances

B. Us-west-2a with three EC2 instances, us-west-2b with three EC2 instances, and us-west-2c with no EC2 instances

C. Us-west-2a with four EC2 instances, us-west-2b with two EC2 instances, and us-west-2c with two EC2 instances

D. Us-west-2a with six EC2 instances, us-west-2b with six EC2 instances, and us-west-2c with no EC2 instances

E. Us-west-2a with three EC2 instances, us-west-2b with three EC2 instances, and us-west-2c with three EC2 instances

**Answer： D, E**

---

**QUESTION 274**

You have a business-critical two-tier web app currently deployed in two Availability Zones in a single region, using Elastic Load Balancing and Auto Scaling. The app depends on synchronous replication \(very low latency connectivity\) at the database layer. The application needs to remain fully available even if one application Availability Zone goes off-line, and Auto Scaling cannot launch new instances in the remaining Availability Zones. How can the current architecture be enhanced to ensure this?

A. Deploy in three Availability Zones, with Auto Scaling minimum set to handle 33 percent peak load per zone.

B. Deploy in three Availability Zones, with Auto Scaling minimum set to handle 50 percent peak load per zone.

C. Deploy in two regions using Weighted Round Robin \(WRR\), with Auto Scaling minimums set for 50 percent peak load per Region.

D. Deploy in two regions using Weighted Round Robin \(WRR\), with Auto Scaling minimums set for 100 percent peak load per region.

**Answer: B**

---

**QUESTION 275**

Amazon Glacier is designed for:Choose 2 answers

A. Frequently accessed data

B. Active database storage

C. Infrequently accessed data

D. Cached session data

E. Data archives

**Answer： C, E**

---

**QUESTION 276**

You receive a Spot Instance at a bid of0.03/hr.After30minutes,theSpotPriceincreasesto0.03/hr.After30minutes,theSpotPriceincreasesto0.05/hr and your Spot Instance is terminated by AWS. What was the total EC2 compute cost of running your Spot Instance?

A. $0.00

B. $0.02

C. $0.03

D. $0.05

E. $0.06

**Answer: A**

---

**QUESTION 277**

You have been tasked with creating a VPC network topology for your company. The VPC network must support both Internet-facing applications and internally-facing applications accessed only over VPN. Both Internet-facing and internally-facing applications must be able to leverage at least three AZs for high availability. At a minimum, how many subnets must you create within your VPC to accommodate these requirements?

A. 2

B. 3

C. 4

D. 6

**Answer: D**

---



