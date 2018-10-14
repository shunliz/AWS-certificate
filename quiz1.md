1. You are implementing a URL whitelisting system for a company that wants to restrict outbound HTTP’S connections to specific domains from their EC2-hosted applications you deploy a single EC2 instance running proxy software and configure It to accept traffic from all subnets and EC2 instances in the VPC. You configure the proxy to only pass through traffic to domains that you define in its whitelist configuration You have a nightly maintenance window or 10 minutes where ail instances fetch new software updates. Each update Is about 200MB In size and there are 500 instances In the VPC that routinely fetch updates After a few days you notice that some machines are failing to successfully download some, but not all of their updates within the maintenance window The download URLs used for these updates are correctly listed in the proxy’s whitelist configuration and you are able to access them manually using a web browser on the instances What might be happening? \(Choose 2 answers\)  
   **\[PROFESSIONAL\]**  
   1. **You are running the proxy on an undersized EC2 instance type so network throughput is not sufficient for all instances to download their updates in time.**  
   2. You have not allocated enough storage to the EC2 instance running me proxy so the network buffer is filling up causing some requests to fall  
   3. You are running the proxy in a public subnet but have not allocated enough EIPs to support the needed network throughput through the Internet Gateway \(IGW\)  
   4. **You are running the proxy on a affluently-sized EC2 instance in a private subnet and its network throughput is being throttled by a NAT running on an undersized EC2 instance**  
   5. The route table for the subnets containing the affected EC2 instances is not configured to direct network traffic for the software update locations to the proxy.

2. You have been asked to design the storage layer for an application. The application requires disk performance of at least 100,000 IOPS in addition; the storage layer must be able to survive the loss of an individual disk, EC2 instance, or Availability Zone without any data loss. The volume you provide must have a capacity of at least 3TB. Which of the following designs will meet these objectives?  
   **\[PROFESSIONAL\]**  
   1. Instantiate an i2.8xlarge instance in us-east-1a. Create a RAID 0 volume using the four 800GB SSD ephemeral disks provided with the instance. Provision 3×1 TB EBS volumes attach them to the instance and configure them as a second RAID 0 volume. Configure synchronous, block-level replication from the ephemeral backed volume to the EBS-backed volume. \(  
      Same AZ will not survive the AZ loss\)  
   2. **Instantiate an i2.8xlarge instance in us-east-1a. Create a RAID 0 volume using the four 800GB SSD ephemeral disks provided with the Instance Configure synchronous block-level replication to an identically configured Instance in us-east-1b.**  
   3. Instantiate a c3.8xlarge Instance in us-east-1. Provision an AWS Storage Gateway and configure it for 3 TB of storage and 100,000 IOPS. Attach the volume to the instance. \(Need synchronous replication to prevent any data loss\)  
   4. Instantiate a c3.8xlarge instance in us-east-1 provision 4x1TB EBS volumes, attach them to the instance, and configure them as a single RAID 5 volume Ensure that EBS snapshots are performed every 15 minutes. \(RAID 5 not recommended by AWS and Need synchronous replication to prevent any data loss\)  
   5. Instantiate a c3 8xlarge Instance in us-east-1 Provision 3x1TB EBS volumes attach them to the instance, and configure them as a single RAID 0 volume Ensure that EBS snapshots are performed every 15 minutes. \(Need synchronous replication to prevent any data loss\)

3. An application you maintain consists of multiple EC2 instances in a default tenancy VPC. This application has undergone an internal audit and has been determined to require dedicated hardware for one instance. Your compliance team has given you a week to move this instance to single-tenant hardware. Which process will have minimal impact on your application while complying with this requirement?

   1. Create a new VPC with tenancy=dedicated and migrate to the new VPC
      \(possible but impact not minimal\)
   2. Use ec2-reboot-instances command line and set the parameter “dedicated=true”
   3. Right click on the instance, select properties and check the box for dedicated tenancy
   4. **Stop the instance, create an AMI, launch a new instance with tenancy=dedicated, and terminate the old instance**

4. Your department creates regular analytics reports from your company’s log files. All log data is collected in Amazon S3 and processed by daily Amazon Elastic Map Reduce \(EMR\) jobs that generate daily PDF reports and aggregated tables in CSV format for an Amazon Redshift data warehouse. Your CFO requests that you optimize the cost structure for this system. Which of the following alternatives will lower costs without compromising average performance of the system or data integrity for the raw data? 
   **\[PROFESSIONAL\]**
   1. Use reduced redundancy storage \(RRS\) for PDF and CSV data in Amazon S3. Add Spot instances to Amazon EMR jobs. Use Reserved Instances for Amazon Redshift. \(Spot instances impacts performance\)
   2. **Use reduced redundancy storage \(RRS\) for all data in S3. Use a combination of Spot instances and Reserved Instances for Amazon EMR jobs. Use Reserved instances for Amazon Redshift**
      \(Combination of the Spot and reserved with guarantee performance and help reduce cost. Also, RRS would reduce cost and guarantee data integrity, which is different from data durability \)
   3. Use reduced redundancy storage \(RRS\) for all data in Amazon S3. Add Spot Instances to Amazon EMR jobs. Use Reserved Instances for Amazon Redshift \(Spot instances impacts performance\)
   4. Use reduced redundancy storage \(RRS\) for PDF and CSV data in S3. Add Spot Instances to EMR jobs. Use Spot Instances for Amazon Redshift. \(Spot instances impacts performance\)
5. A research scientist is planning for the one-time launch of an Elastic MapReduce cluster and is encouraged by her manager to minimize the costs. The cluster is designed to ingest 200TB of genomics data with a total of 100 Amazon EC2 instances and is expected to run for around four hours. The resulting data set must be stored temporarily until archived into an Amazon RDS Oracle instance. Which option will help save the most money while meeting requirements? 
   **\[PROFESSIONAL\]**
   1. **Store ingest and output files in Amazon S3. Deploy on-demand for the master and core nodes and spot for the task nodes.**
   2. Optimize by deploying a combination of on-demand, RI and spot-pricing models for the master, core and task nodes. Store ingest and output files in Amazon S3 with a lifecycle policy that archives them to Amazon Glacier. \(
      Reserved Instance not cost effective for 4 hour job and data not needed in S3 once moved to RDS\)
   3. Store the ingest files in Amazon S3 RRS and store the output files in S3. Deploy Reserved Instances for the master and core nodes and on-demand for the task nodes. \(Reserved Instance not cost effective\)
   4. Deploy on-demand master, core and task nodes and store ingest and output files in Amazon S3 RRS \(
      RRS provides not much cost benefits for a 4 hour job while the amount of input data would take time to upload and Output data to reproduce\)
6. A company currently has a highly available web application running in production. The application’s web front-end utilizes an Elastic Load Balancer and Auto scaling across 3 availability zones. During peak load, your web servers operate at 90% utilization and leverage a combination of heavy utilization reserved instances for steady state load and on-demand and spot instances for peak load. You are asked with designing a cost effective architecture to allow the application to recover quickly in the event that an availability zone is unavailable during peak load. Which option provides the most cost effective high availability architectural design for this application? 
   **\[PROFESSIONAL\]**
   1. **Increase auto scaling capacity and scaling thresholds to allow the web-front to cost-effectively scale across all availability zones to lower aggregate utilization levels that will allow an availability zone to fail during peak load without affecting the applications availability.**
      \(Ideal for HA to reduce and distribute load\)
   2. Continue to run your web front-end at 90% utilization, but purchase an appropriate number of utilization RIs in each availability zone to cover the loss of any of the other availability zones during peak load. \(
      90% is not recommended as well RIs would increase the cost\)
   3. Continue to run your web front-end at 90% utilization, but leverage a high bid price strategy to cover the loss of any of the other availability zones during peak load. \(
      90% is not recommended as high bid price would not guarantee instances and would increase cost\)
   4. Increase use of spot instances to cost effectively to scale the web front-end across all availability zones to lower aggregate utilization levels that will allow an availability zone to fail during peak load without affecting the applications availability. \(Availability cannot be guaranteed\)
7. You run accounting software in the AWS cloud. This software needs to be online continuously during the day every day of the week, and has a very static requirement for compute resources. You also have other, unrelated batch jobs that need to run once per day at any time of your choosing. How should you minimize cost?
   **\[PROFESSIONAL\]**
   1. **Purchase a Heavy Utilization Reserved Instance to run the accounting software. Turn it off after hours. Run the batch jobs with the same instance class, so the Reserved Instance credits are also applied to the batch jobs.**
      \(Because the instance will always be online during the day, in a predictable manner, and there are sequences of batch jobs to perform at any time, we should run the batch jobs when the account software is off. We can achieve Heavy Utilization by alternating these times, so we should purchase the reservation as such, as this represents the lowest cost. There is no such thing a “Full” level utilization purchases on EC2.\)
   2. Purchase a Medium Utilization Reserved Instance to run the accounting software. Turn it off after hours. Run the batch jobs with the same instance class, so the Reserved Instance credits are also applied to the batch jobs.
   3. Purchase a Light Utilization Reserved Instance to run the accounting software. Turn it off after hours. Run the batch jobs with the same instance class, so the Reserved Instance credits are also applied to the batch jobs.
   4. Purchase a Full Utilization Reserved Instance to run the accounting software. Turn it off after hours. Run the batch jobs with the same instance class, so the Reserved Instance credits are also applied to the batch jobs.


