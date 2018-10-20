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



