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

**Qestion 5**

A gaming company adopted AWS CloudFormation to automate load -testing of their games. They have created an AWS CloudFormation template for each gaming environment and one for the load -testing stack. The load – testing stack creates an Amazon Relational Database Service \(RDS\) Postgres database and two web servers running on Amazon Elastic Compute Cloud \(EC2\) that send HTTP requests, measure response times, and write the results into the database. A test run usually takes between 15 and 30 minutes. Once the tests are done, the AWS CloudFormation stacks are torn down immediately. The test results written to the Amazon RDS database must remain accessible for visualization and analysis. Select possible solutions that allow access to the test results after the AWS CloudFormation load -testing stack is deleted. Choose 2 answers.

**\[PROFESSIONAL\]**

1. **Define a deletion policy of type Retain for the Amazon QDS resource to assure that the RDS database is not deleted with the AWS CloudFormation stack.**
2. **Define a deletion policy of type Snapshot for the Amazon RDS resource to assure that the RDS database can be restored after the AWS CloudFormation stack is deleted.**
3. Define automated backups with a backup retention period of 30 days for the Amazon RDS database and perform point -in -time recovery of the database after the AWS CloudFormation stack is deleted. \(
   as the environment is required for limited time the automated backup will not serve the purpose\)
4. Define an Amazon RDS Read-Replica in the load-testing AWS CloudFormation stack and define a dependency relation between master and replica via the DependsOn attribute. \(
   read replica not needed and will be deleted when the stack is deleted\)
5. Define an update policy to prevent deletion of the Amazon RDS database after the AWS CloudFormation stack is deleted. \(
   UpdatePolicy does not apply to RDS\)



**Qestion 6**

ou need to deploy an AWS stack in a repeatable manner across multiple environments. You have selected CloudFormation as the right tool to accomplish this, but have found that there is a resource type you need to create and model, but is unsupported by CloudFormation. How should you overcome this challenge? 

**\[PROFESSIONAL\]**

1. Use a CloudFormation Custom Resource Template by selecting an API call to proxy for create, update, and delete actions. CloudFormation will use the AWS SDK, CLI, or API method of your choosing as the state transition function for the resource type you are modeling.
2. Submit a ticket to the AWS Forums. AWS extends CloudFormation Resource Types by releasing tooling to the AWS Labs organization on GitHub. Their response time is usually 1 day, and they complete requests within a week or two.
3. Instead of depending on CloudFormation, use Chef, Puppet, or Ansible to author Heat templates, which are declarative stack resource definitions that operate over the OpenStack hypervisor and cloud environment.
4. **Create a CloudFormation Custom Resource Type by implementing create, update, and delete functionality, either by subscribing a Custom Resource Provider to an SNS topic, or by implementing the logic in AWS Lambda.**
   \(Refer [link](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-custom-resources.html) \)

**Qestion 7**

Your company needs to automate 3 layers of a large cloud deployment. You want to be able to track this deployment’s evolution as it changes over time, and carefully control any alterations. What is a good way to automate a stack to meet these requirements? 

**\[PROFESSIONAL\]**

1. Use OpsWorks Stacks with three layers to model the layering in your stack.
2. **Use CloudFormation Nested Stack Templates, with three child stacks to represent the three logical layers of your cloud.**
   \(CloudFormation allows source controlled, declarative templates as the basis for stack automation and Nested Stacks help achieve clean separation of layers while simultaneously providing a method to control all layers at once when needed\)
3. Use AWS Config to declare a configuration set that AWS should roll out to your cloud.
4. Use Elastic Beanstalk Linked Applications, passing the important DNS entries between layers using the metadata interface.



**Qestion 8**

You have been asked to de-risk deployments at your company. Specifically, the CEO is concerned about outages that occur because of accidental inconsistencies between Staging and Production, which sometimes cause unexpected behaviors in Production even when Staging tests pass. You already use Docker to get high consistency between Staging and Production for the application environment on your EC2 instances. How do you further de-risk the rest of the execution environment, since in AWS, there are many service components you may use beyond EC2 virtual machines? 

**\[PROFESSIONAL\]**

1. **Develop models of your entire cloud system in CloudFormation. Use this model in Staging and Production to achieve greater parity.**
   \(Only CloudFormation’s JSON Templates allow declarative version control of repeatedly deployable models of entire AWS clouds. Refer [link](https://blogs.aws.amazon.com/application-management/blog/category/Best+practices)\)
2. Use AWS Config to force the Staging and Production stacks to have configuration parity. Any differences will be detected for you so you are aware of risks.
3. Use AMIs to ensure the whole machine, including the kernel of the virual machines, is consistent, since Docker uses Linux Container \(LXC\) technology, and we need to make sure the container environment is consistent.
4. Use AWS ECS and Docker clustering. This will make sure that the AMIs and machine sizes are the same across both environments.



