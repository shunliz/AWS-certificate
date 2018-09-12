**QUESTION 75**

A user wants to access RDS from an EC2 instance using IP addresses. Both RDS and EC2 are

in the same region, but different AZs. Which of the below mentioned options help configure that

the instance is accessed faster?

A. Configure the Private IP of the Instance in RDS security group

B. Security group of EC2 allowed in the RDS security group

C. Configuring the elastic IP of the instance in RDS security group

D. Configure the Public IP of the instance in RDS security group

**Answer: A**

**Explanation:**

If the user is going to specify an IP range in RDS security group, AWS recommends using the

private IP address of the Amazon EC2 instance. This provides a more direct network route from

the Amazon EC2 instance to the Amazon RDS DB instance, and does not incur network charges

for the data sent outside of the Amazon network.

---



