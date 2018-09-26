**Q: What is the difference between using the local instance store and Amazon Elastic Block Store \(Amazon EBS\) for the root device?**

When you launch your Amazon EC2 instances you have the ability to store your root device data on Amazon EBS or the local instance store. By using Amazon EBS, data on the root device will persist independently from the lifetime of the instance. This enables you to stop and restart the instance at a subsequent time, which is similar to shutting down your laptop and restarting it when you need it again.

Alternatively, the local instance store only persists during the life of the instance. This is an inexpensive way to launch instances where data is not stored to the root device. For example, some customers use this option to run large web sites where each instance is a clone to handle web traffic.

**Q: How do I load and store my systems with Amazon EC2?**

Amazon EC2 allows you to set up and configure everything about your instances from your operating system up to your applications. An Amazon Machine Image \(AMI\) is simply a packaged-up environment that includes all the necessary bits to set up and boot your instance. Your AMIs are your unit of deployment. You might have just one AMI or you might compose your system out of several building block AMIs \(e.g., webservers, appservers, and databases\). Amazon EC2 provides a number of tools to make creating an AMI easy. Once you create a custom AMI, you will need to bundle it. If you are bundling an image with a root device backed by Amazon EBS, you can simply use the bundle command in the AWS Management Console. If you are bundling an image with a boot partition on the instance store, then you will need to use the AMI Tools to upload it to Amazon S3. Amazon EC2 uses Amazon EBS and Amazon S3 to provide reliable, scalable storage of your AMIs so that we can boot them when you ask us to do so.

Or, if you want, you don’t have to set up your own AMI from scratch. You can choose from a number of globally available AMIs that provide useful instances. For example, if you just want a simple Linux server, you can choose one of the standard Linux distribution AMIs.

**Q: How do I select the right instance type?**

Amazon EC2 instances are grouped into 5 families: General Purpose, Compute Optimized, Memory Optimized, Storage Optimized and Accelerated Computing instances. General Purpose Instances have memory to CPU ratios suitable for most general purpose applications and come with fixed performance \(M5, M4\) or burstable performance \(T2\); Compute Optimized instances \(C5, C4\) have proportionally more CPU resources than memory \(RAM\) and are well suited for scale out compute-intensive applications and High Performance Computing \(HPC\) workloads; Memory Optimized Instances \(X1e, X1, R4\) offer larger memory sizes for memory-intensive applications, including database and memory caching applications; Accelerating Computing instances \(P3, P2, G3, F1\) take advantage of the parallel processing capabilities of NVIDIA Tesla GPUs for high performance computing and machine/deep learning; GPU Graphics instances \(G3\) offer high-performance 3D graphics capabilities for applications using OpenGL and DirectX; F1 instances deliver Xilinx FPGA-based reconfigurable computing; Storage Optimized Instances \(H1, I3, D2\) that provide very high, low latency, I/O capacity using SSD-based local instance storage for I/O-intensive applications, with D2 or H1, the dense-storage and HDD-storage instances, provide local high storage density and sequential I/O performance for data warehousing, Hadoop and other data-intensive applications. When choosing instance types, you should consider the characteristics of your application with regards to resource utilization \(i.e. CPU, Memory, Storage\) and select the optimal instance family and instance size.

创建EC2实例的时候，我们可以勾选“自动分配Public IP”（原话是英文的哦~），也可以不勾选，然后手动关联Elastic IP\(EIP\),那么着二者有什么区别呢？

从亚马逊在线技术支持那里了解到：

（1）EIP是属于某个特定的账号，可以关联到账号的任意实例上，也可卸载下来重新关联到其他实例上，而且实例被删除之后，EIP依然单独存在。\(分配EIP时注意VPC和EC2的EIP的区别，不同类型的EIP时能关联到自己类型的实例上，即VPC中的EIP只能用于VPC中的实例，Classic EC2只能关联非VPC的EIP）

（2）而普通的Public IP是属于具体的某台实例，不能卸载重新关联到别的实例，实例创建时，如果勾选自动分配Public IP，则会随实例一起被创建，实例删除时，跟着被删除，无法被重复利用和保留；

（3）还有一个非常重要的特性：Public IP在实例关机后再开机，可能会改变，重启不影响（这跟Classic EC2实例的Public DNS一样，可能会改变）。而EIP怎么都不会变。

（4）如果实例创建之初，有PublicIP,然后再关联了ElasticIP的话，二者都会变成ElasticIP的样子（被覆盖），当EIP被解除关联之后，PublicIP才会被显露，但此时会重新分配PublicIP，所以PublicIP会变。

所以，如果在EC2实例的生命周期内，有停机再开机的可能，还是使用EIP比较保险

**Q: How isolated are Availability Zones from one another?**

Each Availability Zone runs on its own physically distinct, independent infrastructure, and is engineered to be highly reliable. Common points of failures like generators and cooling equipment are not shared across Availability Zones. Additionally, they are physically separate, such that even extremely uncommon disasters such as fires, tornados or flooding would only affect a single Availability Zone.

**Q: How can I make sure that I am in the same Availability Zone as another developer?**

We do not currently support the ability to coordinate launches into the same Availability Zone across AWS developer accounts. One Availability Zone name \(for example, us-east-1a\) in two AWS customer accounts may relate to different physical Availability Zones.

**Q. How many EBS volumes and Elastic Network Interfaces \(ENIs\) can be attached to instances running on the Nitro Hypervisor?**

Instances running on the Nitro Hypervisor support a maximum of 27 additional PCI devices for EBS volumes and VPC ENIs. Each EBS volume or VPC ENI uses a PCI device. For example, if you attach 3 additional network interfaces to an instance that uses the Nitro Hypervisor, you can attach up to 24 EBS volumes to that instance.\(each pci bus has maximum 32 devices, and some slot for sound card, video card......., so left 27 maxinum for EBS or ENI.\)

**Q: Which volume type should I choose?**

Amazon EBS includes two major categories of storage: SSD-backed storage for transactional workloads \(performance depends primarily on IOPS\) and HDD-backed storage for throughput workloads \(performance depends primarily on throughput, measured in MB/s\). SSD-backed volumes are designed for transactional, IOPS-intensive database workloads, boot volumes, and workloads that require high IOPS. SSD-backed volumes include Provisioned IOPS SSD \(io1\) and General Purpose SSD \(gp2\). HDD-backed volumes are designed for throughput-intensive and big-data workloads, large I/O sizes, and sequential I/O patterns. HDD-backed volumes include Throughput Optimized HDD \(st1\) and Cold HDD \(sc1\). For more information on Amazon EBS see the[EBS product details page](https://amazonaws-china.com/ebs/details/).

**Q: Will I be able to access my EBS snapshots using the regular Amazon S3 APIs?**

No, EBS snapshots are only available through the Amazon EC2 APIs.

**Q: Do volumes need to be un-mounted in order to take a snapshot? Does the snapshot need to complete before the volume can be used again? **

No, snapshots can be done in real time while the volume is attached and in use. However, snapshots only capture data that has been written to your Amazon EBS volume, which might exclude any data that has been locally cached by your application or OS. In order to ensure consistent snapshots on volumes attached to an instance, we recommend cleanly detaching the volume, issuing the snapshot command, and then reattaching the volume. For Amazon EBS volumes that serve as root devices, we recommend shutting down the machine to take a clean snapshot.

**Q: How can I discover Amazon EBS snapshots that have been shared with me?**

You can find snapshots that have been shared with you by selecting “Private Snapshots” from the viewing dropdown in the Snapshots section of the AWS Management Console. This section will list both snapshots you own and snapshots that have been shared with you.

**Q. How do I access a file system from an Amazon EC2 instance?**

To access your file system, you mount the file system on an Amazon EC2 Linux-based instance using the standard Linux mount command and the file system’s DNS name. Once you’ve mounted, you can work with the files and directories in your file system just like you would with a local file system.

Amazon EFS uses the NFSv4.1 protocol. For a step-by-step example of how to access a file system from an Amazon EC2 instance, please see the[Amazon EFS Getting Started guide](http://docs.aws.amazon.com/efs/latest/ug/gs-mount-fs-on-ec2instance-and-test.html).

**Q. How do I access my file system from outside my VPC?**

Amazon EC2 instances within your VPC can access your file system directly, and Amazon EC2 Classic instances outside your VPC can mount a file system via [ClassicLink](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/vpc-classiclink.html). On-premises servers can mount your file systems via an [AWS Direct Connect](https://amazonaws-china.com/directconnect/) connection to your VPC.


#Amazon CloudWatch
**Q: What is the minimum time interval granularity for the data that Amazon CloudWatch receives and aggregates?**

Metrics are received and aggregated at 1 minute intervals.

**Q: Which operating systems does Amazon CloudWatch support?**

Amazon CloudWatch receives and provides metrics for all Amazon EC2 instances and should work with any operating system currently supported by the Amazon EC2 service.

**Q: Will I lose the metrics data if I disable monitoring for an Amazon EC2 instance?**

You can retrieve metrics data for any Amazon EC2 instance up to 2 weeks from the time you started to monitor it. After 2 weeks, metrics data for an Amazon EC2 instance will not be available if monitoring was disabled for that Amazon EC2 instance. If you want to archive metrics beyond 2 weeks you can do so by calling mon-get-stats command from the command line and storing the results in Amazon S3 or Amazon SimpleDB.

