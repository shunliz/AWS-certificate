**Qestion 1**

You have a business critical two tier web app currently deployed in two availability zones in a single region, using Elastic Load Balancing and Auto Scaling. The app depends on synchronous replication \(very low latency connectivity\) at the database layer. The application needs to remain fully available even if one application Availability Zone goes off-line, and Auto scaling cannot launch new instances in the remaining Availability Zones. How can the current architecture be enhanced to ensure this?

**\[PROFESSIONAL\]**

1. Deploy in two regions using Weighted Round Robin \(WRR\), with Auto Scaling minimums set for 100% peak load per region.
2. **Deploy in three AZs, with Auto Scaling minimum set to handle 50% peak load per zone.**
3. Deploy in three AZs, with Auto Scaling minimum set to handle 33% peak load per zone. \(
   Loss of one AZ will handle only 66% if the autoscaling also fails\)
4. Deploy in two regions using Weighted Round Robin \(WRR\), with Auto Scaling minimums set for 50% peak load per region.

**Qestion 2**

Your startup wants to implement an order fulfillment process for selling a personalized gadget that needs an average of 3-4 days to produce with some orders taking up to 6 months you expect 10 orders per day on your first day. 1000 orders per day after 6 months and 10,000 orders after 12 months. Orders coming in are checked for consistency then dispatched to your manufacturing plant for production quality control packaging shipment and payment processing. If the product does not meet the quality standards at any stage of the process employees may force the process to repeat a step. Customers are notified via email about order status and any critical issues with their orders such as payment failure. Your case architecture includes AWS Elastic Beanstalk for your website with an RDS MySQL instance for customer data and orders. How can you implement the order fulfillment process while making sure that the emails are delivered reliably?

**\[PROFESSIONAL\]**

1. Add a business process management application to your Elastic Beanstalk app servers and re-use the ROS database for tracking order status use one of the Elastic Beanstalk instances to send emails to customers.
2. Use SWF with an Auto Scaling group of activity workers and a decider instance in another Auto Scaling group with min/max=1 Use the decider instance to send emails to customers.
3. **Use SWF with an Auto Scaling group of activity workers and a decider instance in another Auto Scaling group with min/max=1 use SES to send emails to customers.**
4. Use an SQS queue to manage all process tasks Use an Auto Scaling group of EC2 Instances that poll the tasks and execute them. Use SES to send emails to customers.

**Qestion 3**

A large enterprise wants to adopt CloudFormation to automate administrative tasks and implement the security principles of least privilege and separation of duties. They have identified the following roles with the corresponding tasks in the company: \(i\) network administrators: create, modify and delete VPCs, subnets, NACLs, routing tables, and security groups \(ii\) application operators: deploy complete application stacks \(ELB, Auto -Scaling groups, RDS\) whereas all resources must be deployed in the VPCs managed by the network administrators \(iii\) Both groups must maintain their own CloudFormation templates and should be able to create, update and delete only their own CloudFormation stacks. The company has followed your advice to create two IAM groups, one for applications and one for networks. Both IAM groups are attached to IAM policies that grant rights to perform the necessary task of each group as well as the creation, update and deletion of CloudFormation stacks. Given setup and requirements, which statements represent valid design considerations? Choose 2 answers

**\[PROFESSIONAL\]**

1. **Network stack updates will fail upon attempts to delete a subnet with EC2 instances**
   \(Subnets cannot be deleted with instances in them\)
2. Unless resource level permissions are used on the CloudFormation: DeleteStack action, network administrators could tear down application stacks \(
   Network administrators themselves need permission to delete resources within the application stack &
    CloudFormation makes calls to create, modify, and delete those resources on their behalf\)
3. The application stack cannot be deleted before all network stacks are deleted \(
   Application stack can be deleted before network stack\)
4. **Restricting the launch of EC2 instances into VPCs requires resource level permissions in the IAM policy of the application group**
   \(IAM permissions need to be given explicitly to launch instances\)
5. Nesting network stacks within application stacks simplifies management and debugging, but requires resource level permissions in the IAM policy of the network group \(
   Although stacks can be nested, Network group will need to have all the application group permissions\)



**Qestion 4**

A marketing research company has developed a tracking system that collects user behavior during web marketing campaigns on behalf of their customers all over the world. The tracking system consists of an auto-scaled group of Amazon Elastic Compute Cloud \(EC2\) instances behind an elastic load balancer \(ELB\), and the collected data is stored in Amazon DynamoDB. After the campaign is terminated, the tracking system is torn down and the data is moved to Amazon Redshift, where it is aggregated, analyzed and used to generate detailed reports. The company wants to be able to instantiate new tracking systems in any region without any manual intervention and therefore adopted AWS CloudFormation. What needs to be done to make sure that the AWS CloudFormation template works in every AWS region? Choose 2 answers 

**\[PROFESSIONAL\]**

1. IAM users with the right to start AWS CloudFormation stacks must be defined for every target region. \(
   IAM users are global\)
2. The names of the Amazon DynamoDB tables must be different in every target region. \(
   DynamoDB names should be unique only within a region\)
3. **Use the built-in function of AWS CloudFormation to set the AvailabilityZone attribute of the ELB resource.**
4. Avoid using DeletionPolicies for EBS snapshots. \(
   Don’t want the data to be retained\)
5. **Use the built-in Mappings and FindInMap functions of AWS CloudFormation to refer to the AMI ID set in the ImageId attribute of the Auto Scaling::LaunchConfiguration resource.**



