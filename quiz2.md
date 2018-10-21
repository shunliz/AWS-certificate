**Questions 1**

You are designing a personal document-archiving solution for your global enterprise with thousands of employee. Each employee has potentially gigabytes of data to be backed up in this archiving solution. The solution will be exposed to he employees as an application, where they can just drag and drop their files to the archiving system. Employees can retrieve their archives through a web interface. The corporate network has high bandwidth AWS DirectConnect connectivity to AWS. You have regulatory requirements that all data needs to be encrypted before being uploaded to the cloud. How do you implement this in a highly available and cost efficient way?

1. Manage encryption keys on-premise in an encrypted relational database. Set up an on-premises server with sufficient storage to temporarily store files and then upload them to Amazon S3, providing a client-side master key. \(Storing temporary increases cost and not a high availability option\)
2. Manage encryption keys in a Hardware Security Module\(HSM\) appliance on-premise server with sufficient storage to temporarily store, encrypt, and upload files directly into amazon Glacier. \(Not cost effective\)
3. **Manage encryption keys in amazon Key Management Service \(KMS\), upload to amazon simple storage service \(s3\) with client-side encryption using a KMS customer master key ID and configure Amazon S3 lifecycle policies to store each object using the amazon glacier storage tier.**
   \(with CSE-KMS the encryption happens at client side before the object is upload to S3 and KMS is cost effective as well\)
4. Manage encryption keys in an AWS CloudHSM appliance. Encrypt files prior to uploading on the employee desktop and then upload directly into amazon glacier \(Not cost effective\)

**Questions 2**

Your company host a social media website for storing and sharing documents. the web application allow users to upload large files while resuming and pausing the upload as needed. Currently, files are uploaded to your php front end backed by Elastic Load Balancing and an autoscaling fleet of amazon elastic compute cloud \(EC2\) instances that scale upon average of bytes received \(NetworkIn\) After a file has been uploaded. it is copied to amazon simple storage service\(S3\). Amazon Ec2 instances use an AWS Identity and Access Management \(AMI\) role that allows Amazon s3 uploads. Over the last six months, your user base and scale have increased significantly, forcing you to increase the auto scaling groups Max parameter a few times. Your CFO is concerned about the rising costs and has asked you to adjust the architecture where needed to better optimize costs. Which architecture change could you introduce to reduce cost and still keep your web application secure and scalable?

1. Replace the Autoscaling launch Configuration to include c3.8xlarge instances; those instances can potentially yield a network throughput of 10gbps. \(no info of current size and might increase cost\)
2. Re-architect your ingest pattern, have the app authenticate against your identity provider as a broker fetching temporary AWS credentials from AWS Secure token service \(GetFederation Token\). Securely pass the credentials and s3 endpoint/prefix to your app. Implement client-side logic to directly upload the file to amazon s3 using the given credentials and S3 Prefix. \(will not provide the ability to handle pause and restarts\)
3. Re-architect your ingest pattern, and move your web application instances into a VPC public subnet. Attach a public IP address for each EC2 instance \(using the auto scaling launch configuration settings\). Use Amazon Route 53 round robin records set and http health check to DNS load balance the app request this approach will significantly reduce the cost by bypassing elastic load balancing. \(ELB is not the bottleneck\)
4. **Re-architect your ingest pattern, have the app authenticate against your identity provider as a broker fetching temporary AWS credentials from AWS Secure token service \(GetFederation Token\). Securely pass the credentials and s3 endpoint/prefix to your app. Implement client-side logic that used the S3 multipart upload API to directly upload the file to Amazon s3 using the given credentials and s3 Prefix.**
   \(multipart allows one to start uploading directly to S3 before the actual size is known or complete data is downloaded\)

**Questions 3**

You are running a successful multi-tier web application on AWS and your marketing department has asked you to add a reporting tier to the application. The reporting tier will aggregate and publish status reports every 30 minutes from user-generated information that is being stored in your web applications database. You are currently running a Multi-AZ RDS MySQL instance for the database tier. You also have implemented ElastiCache as a database caching layer between the application tier and database tier. Please select the answer that will allow you to successfully implement the reporting tier with as little impact as possible to your database.

1. Continually send transaction logs from your master database to an S3 bucket and generate the reports off the S3 bucket using S3 byte range requests.
2. Generate the reports by querying the synchronously replicated standby RDS MySQL instance maintained through Multi-AZ \(
   Standby instance cannot be used as a scaling solution\)
3. **Launch a RDS Read Replica connected to your Multi-AZ master database and generate reports by querying the Read Replica.**
4. Generate the reports by querying the ElastiCache database caching tier. \(
   ElasticCache does not maintain full data and is simply a caching solution\)

**Questions 4**

A company is running a batch analysis every hour on their main transactional DB running on an RDS MySQL instance to populate their central Data Warehouse running on Redshift. During the execution of the batch their transactional applications are very slow. When the batch completes they need to update the top management dashboard with the new data. The dashboard is produced by another system running on-premises that is currently started when a manually-sent email notifies that an update is required The on-premises system cannot be modified because is managed by another team. How would you optimize this scenario to solve performance issues and automate the process as much as possible?

1. Replace RDS with Redshift for the batch analysis and SNS to notify the on-premises system to update the dashboard
2. Replace RDS with Redshift for the batch analysis and SQS to send a message to the on-premises system to update the dashboard
3. **Create an RDS Read Replica for the batch analysis and SNS to notify me on-premises system to update the dashboard**
4. Create an RDS Read Replica for the batch analysis and SQS to send a message to the on-premises system to update the dashboard.

**Questions 5**

Which statement best describes an Amazon SQS use case?

1. Automate the process of sending an email notification to administrators when the CPU utilization reaches 70% on production servers \(Amazon EC2 instances\) \(CloudWatch + SNS + SES\)
2. **Create a video transcoding website where multiple components need to communicate with each other, but can’t all process the same amount of work simultaneously**\(SQS provides loose coupling\)
3. Coordinate work across distributed web services to process employee’s expense reports \(SWF – Steps in order and might need manual steps\)
4. Distribute static web content to end users with low latency across multiple countries \(CloudFront + S3\)

**Questions 6**

Your application provides data transformation services. Files containing data to be transformed are first uploaded to Amazon S3 and then transformed by a fleet of spot EC2 instances. Files submitted by your premium customers must be transformed with the highest priority. How should you implement such a system?

1. Use a DynamoDB table with an attribute defining the priority level. Transformation instances will scan the table for tasks, sorting the results by priority level.
2. Use Route 53 latency based-routing to send high priority tasks to the closest transformation instances.
3. **Use two SQS queues, one for high priority messages, and the other for default priority. Transformation instances first poll the high priority queue; if there is no message, they poll the default priority queue**
4. Use a single SQS queue. Each message contains the priority level. Transformation instances poll high-priority messages first.

**Questions 7**

A customer has a web application that uses cookie Based sessions to track logged in users. It is deployed on AWS using ELB and Auto Scaling. The customer observes that when load increases Auto Scaling launches new Instances but the load on the existing Instances does not decrease, causing all existing users to have a sluggish experience. Which two answer choices independently describe a behavior that could be the cause of the sluggish user experience?

1. ELB’s normal behavior sends requests from the same user to the same backend instance \(its not by default\)
2. **ELB’s behavior when sticky sessions are enabled causes ELB to send requests in the same session to the same backend **
3. A faulty browser is not honoring the TTL of the ELB DNS name \(DNS TTL would only impact the ELB instances if scaled and not the EC2 instances to which the traffic is routed\)
4. **The web application uses long polling such as comet or websockets. Thereby keeping a connection open to a web server tor a long time**

**Questions 8**

You are designing a multi-platform web application for AWS. The application will run on EC2 instances and will be accessed from PCs, tablets and smart phones. Supported accessing platforms are Windows, MACOS, IOS and Android. Separate sticky session and SSL certificate setups are required for different platform types. Which of the following describes the most cost effective and performance efficient architecture setup?

1. Setup a hybrid architecture to handle session state and SSL certificates on-prem and separate EC2 Instance groups running web applications for different platform types running in a VPC.
2. Set up one ELB for all platforms to distribute load among multiple instance under it. Each EC2 instance implements all functionality for a particular platform.
3. Set up two ELBs. The first ELB handles SSL certificates for all platforms and the second ELB handles session stickiness for all platforms for each ELB run separate EC2 instance groups to handle the web application for each platform.
4. **Assign multiple ELBs to an EC2 instance or group of EC2 instances running the common components of the web application, one ELB for each platform type. Session stickiness and SSL termination are done at the ELBs.**
   \(Session stickiness requires HTTPS listener with SSL termination on the ELB and ELB does not support multiple SSL certs so one is required for each cert\)

**Questions 9**

You are migrating a legacy client-server application to AWS. The application responds to a specific DNS domain \(e.g. www.example.com\) and has a 2-tier architecture, with multiple application servers and a database server. Remote clients use TCP to connect to the application servers. The application servers need to know the IP address of the clients in order to function properly and are currently taking that information from the TCP socket. A Multi-AZ RDS MySQL instance will be used for the database. During the migration you can change the application code but you have to file a change request. How would you implement the architecture on AWS in order to maximize scalability and high availability?

1. **File a change request to implement Proxy Protocol support In the application. Use an ELB with a TCP Listener and Proxy Protocol enabled to distribute load on two application servers in different AZs.**
   \(ELB with TCP listener and proxy protocol will allow IP to be passed \)
2. File a change request to Implement Cross-Zone support in the application. Use an ELB with a TCP Listener and Cross-Zone Load Balancing enabled, two application servers in different AZs.
3. File a change request to implement Latency Based Routing support in the application. Use Route 53 with Latency Based Routing enabled to distribute load on two application servers in different AZs.
4. File a change request to implement Alias Resource support in the application Use Route 53 Alias Resource Record to distribute load on two application servers in different AZs.

**Questions 10**

You have a web-style application with a stateless but CPU and memory-intensive web tier running on a cc2 8xlarge EC2 instance inside of a VPC The instance when under load is having problems returning requests within the SLA as defined by your business The application maintains its state in a DynamoDB table, but the data tier is properly provisioned and responses are consistently fast. How can you best resolve the issue of the application responses not meeting your SLA?

1. **Add another cc2 8xlarge application instance, and put both behind an Elastic Load Balancer**
2. Move the cc2 8xlarge to the same Availability Zone as the DynamoDB table \(
   Does not improve the response time and performance\)
3. Cache the database responses in ElastiCache for more rapid access \(
   Data tier is responding fast\)
4. Move the database from DynamoDB to RDS MySQL in scale-out read-replica configuration \(
   Data tier is responding fast\)



**Questions 11**

An organization has configured a VPC with an Internet Gateway \(IGW\). pairs of public and private subnets \(each with one subnet per Availability Zone\), and an Elastic Load Balancer \(ELB\) configured to use the public subnets. The applications web tier leverages the ELB, Auto Scaling and a Multi-AZ RDS database instance. The organization would like to eliminate any potential single points of failure in this design. What step should you take to achieve this organization’s objective?

1. **Nothing, there are no single points of failure in this architecture.**
2. Create and attach a second IGW to provide redundant internet connectivity. \(
   VPC can be attached only 1 IGW\)
3. Create and configure a second Elastic Load Balancer to provide a redundant load balancer. \(
   ELB scales by itself with multiple availability zones configured with it\)
4. Create a second multi-AZ RDS instance in another Availability Zone and configure replication to provide a redundant database. \(
   Multi AZ requires 2 different AZ for setup and already has a standby\)



**Questions 12**

Your application currently leverages AWS Auto Scaling to grow and shrink as load Increases/ decreases and has been performing well. Your marketing team expects a steady ramp up in traffic to follow an upcoming campaign that will result in a 20x growth in traffic over 4 weeks. Your forecast for the approximate number of Amazon EC2 instances necessary to meet the peak demand is 175. What should you do to avoid potential service disruptions during the ramp up in traffic?

1. Ensure that you have pre-allocated 175 Elastic IP addresses so that each server will be able to obtain one as it launches \(
   max limit 5 EIP and a service request needs to be submitted\)
2. **Check the service limits in Trusted Advisor and adjust as necessary so the forecasted count remains within limits.**
3. Change your Auto Scaling configuration to set a desired capacity of 175 prior to the launch of the marketing campaign \(
   Will cause 175 instances to be launched and running but not gradually scale\)
4. Pre-warm your Elastic Load Balancer to match the requests per second anticipated during peak demand \(
   Does not need pre warming as the load is increasing steadily\)

**Questions 13**

You have a web application running on six Amazon EC2 instances, consuming about 45% of resources on each instance. You are using auto-scaling to make sure that six instances are running at all times. The number of requests this application processes is consistent and does not experience spikes. The application is critical to your business and you want high availability at all times. You want the load to be distributed evenly between all instances. You also want to use the same Amazon Machine Image \(AMI\) for all instances. Which of the following architectural choices should you make?

1. Deploy 6 EC2 instances in one availability zone and use Amazon Elastic Load Balancer. \(
   Single AZ will not provide High Availability\)
2. Deploy 3 EC2 instances in one region and 3 in another region and use Amazon Elastic Load Balancer. \(
   Different region, AMI would not be available unless copied\)
3. **Deploy 3 EC2 instances in one availability zone and 3 in another availability zone and use Amazon Elastic Load Balancer.**
4. Deploy 2 EC2 instances in three regions and use Amazon Elastic Load Balancer. \(
   Different region, AMI would not be available unless copied\)



**Questions 14**

You are designing an SSL/TLS solution that requires HTTPS clients to be authenticated by the Web server using client certificate authentication. The solution must be resilient. Which of the following options would you consider for configuring the web server infrastructure? \(Choose 2 answers\)

1. **Configure ELB with TCP listeners on TCP/443. And place the Web servers behind it.**
   \(terminate SSL on the instance using client-side certificate\)
2. **Configure your Web servers with EIPs. Place the Web servers in a Route53 Record Set and configure health checks against all Web servers.**
   \(Remove ELB and use Web Servers directly with Route 53\)
3. Configure ELB with HTTPS listeners, and place the Web servers behind it. \(
   ELB with HTTPs does not support Client-Side certificates\)
4. Configure your web servers as the origins for a CloudFront distribution. Use custom SSL certificates on your CloudFront distribution \(CloudFront [does not](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/RequestAndResponseBehaviorCustomOrigin.html#RequestCustomClientSideSslAuth) Client-Side ssl certificates\)



**Questions 15**

You are designing an application that contains protected health information. Security and compliance requirements for your application mandate that all protected health information in the application use encryption at rest and in transit. The application uses a three-tier architecture where data flows through the load balancer and is stored on Amazon EBS volumes for processing, and the results are stored in Amazon S3 using the AWS SDK. Which of the following two options satisfy the security requirements? Choose 2 answers

1. Use SSL termination on the load balancer, Amazon EBS encryption on Amazon EC2 instances, and Amazon S3 with server-side encryption. \(connection between ELB and EC2 not encrypted\)
2. Use SSL termination with a SAN SSL certificate on the load balancer, Amazon EC2 with all Amazon EBS volumes using Amazon EBS encryption, and Amazon S3 with server-side encryption with customer-managed keys.
3. **Use TCP load balancing on the load balancer, SSL termination on the Amazon EC2 instances, OS-level disk encryption on the Amazon EBS volumes, and Amazon S3 with server-side encryption.**
4. Use TCP load balancing on the load balancer, SSL termination on the Amazon EC2 instances, and Amazon S3 with server-side encryption. \(Does not mention EBS encryption\)
5. **Use SSL termination on the load balancer, an SSL listener on the Amazon EC2 instances, Amazon EBS encryption on EBS volumes containing PHI, and Amazon S3 with server-side encryption.**



**Questions 16**

A startup deploys its photo-sharing site in a VPC. An elastic load balancer distributes web traffic across two subnets. The load balancer session stickiness is configured to use the AWS-generated session cookie, with a session TTL of 5 minutes. The web server Auto Scaling group is configured as min-size=4, max-size=4. The startup is preparing for a public launch, by running load-testing software installed on a single Amazon Elastic Compute Cloud \(EC2\) instance running in us-west-2a. After 60 minutes of load-testing, the web server logs show the following:WEBSERVER LOGS \| \# of HTTP requests from load-tester \| \# of HTTP requests from private beta users \|\| webserver \#1 \(subnet in us-west-2a\): \| 19,210 \| 434 \|\| webserver \#2 \(subnet in us-west-2a\): \| 21,790 \| 490 \|\| webserver \#3 \(subnet in us-west-2b\): \| 0 \| 410 \|\| webserver \#4 \(subnet in us-west-2b\): \| 0 \| 428 \|Which recommendations can help ensure that load-testing HTTP requests are evenly distributed across the four web servers? Choose 2 answers

   1. Launch and run the load-tester Amazon EC2 instance from us-east-1 instead.
   2. Configure Elastic Load Balancing session stickiness to use the app-specific session cookie.
   3. **Re-configure the load-testing software to re-resolve DNS for each web request.**
      \(Refer [link](https://aws.amazon.com/articles/1636185810492479) \)
   4. Configure Elastic Load Balancing and Auto Scaling to distribute across us-west-2a and us-west-2b.
   5. **Use a third-party load-testing service which offers globally distributed test clients. **
      \(Refer [link](https://aws.amazon.com/articles/1636185810492479)\)


**Questions 17**
To serve Web traffic for a popular product your chief financial officer and IT director have purchased 10 m1.large heavy utilization Reserved Instances \(RIs\) evenly spread across two availability zones: Route 53 is used to deliver the traffic to an Elastic Load Balancer \(ELB\). After several months, the product grows even more popular and you need additional capacity As a result, your company purchases two c3.2xlarge medium utilization RIs You register the two c3.2xlarge instances with your ELB and quickly find that the ml large instances are at 100% of capacity and the c3.2xlarge instances have significant capacity that’s unused Which option is the most cost effective and uses EC2 capacity most effectively?
   1. **Use a separate ELB for each instance type and distribute load to ELBs with Route 53 weighted round robin**
   2. Configure Autoscaling group and Launch Configuration with ELB to add up to 10 more on-demand mi large instances when triggered by CloudWatch shut off c3.2xlarge instances \(increase cost as you still pay for the RI\)
   3. Route traffic to EC2 m1.large and c3.2xlarge instances directly using Route 53 latency based routing and health checks shut off ELB \(will not still use the capacity effectively\)
   4. Configure ELB with two c3.2xlarge Instances and use on-demand Autoscailng group for up to two additional c3.2xlarge instances Shut on m1.large instances\(Increases cost, as you still pay for the 10 m1.large RI\)



