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



