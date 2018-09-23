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



