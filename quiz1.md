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



