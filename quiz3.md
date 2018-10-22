**Qestion 1**

You have a business critical two tier web app currently deployed in two availability zones in a single region, using Elastic Load Balancing and Auto Scaling. The app depends on synchronous replication \(very low latency connectivity\) at the database layer. The application needs to remain fully available even if one application Availability Zone goes off-line, and Auto scaling cannot launch new instances in the remaining Availability Zones. How can the current architecture be enhanced to ensure this? 

**\[PROFESSIONAL\]**

1. Deploy in two regions using Weighted Round Robin \(WRR\), with Auto Scaling minimums set for 100% peak load per region.
2. **Deploy in three AZs, with Auto Scaling minimum set to handle 50% peak load per zone.**
3. Deploy in three AZs, with Auto Scaling minimum set to handle 33% peak load per zone. \(
   Loss of one AZ will handle only 66% if the autoscaling also fails\)
4. Deploy in two regions using Weighted Round Robin \(WRR\), with Auto Scaling minimums set for 50% peak load per region.



