**QUESTION 75  
**

A user wants to access RDS from an EC2 instance using IP addresses. Both RDS and EC2 are

in the same region, but different AZs. Which of the below mentioned options help configure that

the instance is accessed faster?

A. Configure the Private IP of the Instance in RDS security group

B. Security group of EC2 allowed in the RDS security group

C. Configuring the elastic IP of the instance in RDS security group

D. Configure the Public IP of the instance in RDS security group

**Answer: A  
**

**Explanation:  
**

If the user is going to specify an IP range in RDS security group, AWS recommends using the

private IP address of the Amazon EC2 instance. This provides a more direct network route from

the Amazon EC2 instance to the Amazon RDS DB instance, and does not incur network charges

for the data sent outside of the Amazon network.

---

**QUESTION 76**

A user is creating a snapshot of an EBS volume. Which of the below statements is incorrect in

relation to the creation of an EBS snapshot?

A. Its incremental

B. It can be used to launch a new instance

C. It is stored in the same AZ as the volume

D. It is a point in time backup of the EBS volume

**Answer: C**

**Explanation:**

The EBS snapshots are a point in time backup of the EBS volume. It is an incremental snapshot,

but is always specific to the region and never specific to a single AZ. Hence the statement "It is

stored in the same AZ as the volume" is incorrect.

[http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSSnapshots.html](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSSnapshots.html)

---



