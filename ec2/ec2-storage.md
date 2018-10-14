## EC2 Storage Overview

* Amazon EC2 provides flexible, cost effective and easy-to-use EC2 storage options with a unique combination of performance and durability
  * Amazon Elastic Block Store \(EBS\)
  * Amazon EC2 Instance Store
  * Amazon Simple Storage Service \(S3\)
* While EBS and Instance store are Block level, Amazon S3 is an Object level storage

![](https://i1.wp.com/jayendrapatil.com/wp-content/uploads/2016/04/screen-shot-2016-04-19-at-7-09-43-am.png?resize=656%2C359 "EC2 Storage Options - EBS, S3 &amp; Instance Store")

## Storage Types

### Amazon EBS

More details @[AWS EC2 EBS Storage](http://jayendrapatil.com/aws-ec2-ebs-storage/)

### Amazon Instance Store

More details @[AWS EC2 Instance Store Storage](http://jayendrapatil.com/aws-ec2-instance-store-storage/)

### Amazon EBS vs Instance Store

More detailed @[Comparision of EBS vs Instance Store](http://jayendrapatil.com/aws-ebs-vs-instance-store/)

### Amazon S3

More details @[AWS S3](http://jayendrapatil.com/aws-simple-storage-service-s3-overview/)

## Block Device Mapping

* A block device is a storage device that moves data in sequences of bytes or bits \(blocks\) and supports random access and generally use buffered I/O
  _for e.g. hard disks, CD-ROM etc_
* Block devices can be physically attached to a computer \(like an instance store volume\) or can be accessed remotely as if it was attached \(like an EBS volume\)
* Block device mapping defines the block devices to be attached to an instance, which can either be done while creation of an AMI or when an instance is launched
* Block device must be mounted on the instance, after being attached to the instance, to be able to be accessed
* When a block device is detached from an instance, it is unmounted by the operating system and you can no longer access the storage device.
* Additional Instance store volumes can be attached only when the instance is launched while EBS volumes can be attached to an running instance.
* View the block device mapping for an instance, only the EBS volumes can be seen, not the instance store volumes.Instance metadata can be used to query the complete block device mapping.

### Public Data Sets

* Amazon Web Services provides a repository of public data sets that can be seamlessly integrated into AWS cloud-based applications.
* Amazon stores the data sets at no charge to the community and, as with all AWS services, you pay only for the compute and storage you use for your own applications.

---

---

# EC2 Instance Store Storage

## Overview

* An instance store provides temporary block-level storage for an EC2 instance.
* Instance store storage is located on the disks that are physically attached to the host computer.
* Instance store is ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temporary content, or for data that is replicated across a fleet of instances, such as a load-balanced pool of web servers.
* An instance store consists of one or more instance store volumes exposed as block devices.
* Size of an instance store varies by instance type.
* Virtual devices for instance store volumes are 
  ephemeral\[0-23\], starting the first one as ephemeral0 and so on.
* While an instance store is dedicated to a particular instance, the disk subsystem is shared among instances on a host computer.

### Instance Store Lifecycle

* Instance store data lifetime is dependent on the lifecycle of the Instance to which it is attached
* Data on the Instance store persists when an instance is rebooted
* However, the data on the instance store does not persists if the
  * underlying disk drive fails
  * instance stops i.e. if the EBS backed instance with instance store volumes attached is stopped
  * instance terminates
* If an AMI is created from an Instance with Instance strore volume, the data on its instance store volume isn’t preserved

### Instance Store Volumes

* Instance type of an instance determines the size of the instance store available for the instance, and the type of hardware used for the instance store volumes
* Instance store volumes are included as part of the instance’s hourly cost.
* Some instance types use solid state drives \(SSD\) to deliver very high random I/O performance, which is a good option when storage with very low latency is needed, but the data does not need to be persisted when the instance terminates or you can take advantage of fault tolerant architectures.

### Instance Store Volumes with EC2 instances

* EBS volumes and instance store volumes for an instance are specified using a block device mapping
* Instance store volume can be attached to an EC2 instance only when the instance is launched
* Instance store volume cannot be detached and reattached to a different instance
* After an instance is launched, the instance store volumes for the instance should be formatted and mounted before it can be used.
* Root volume of an instance store-backed instance is mounted automatically.

### Instance Store Optimizing Writes

* Because of the way that Amazon EC2 virtualizes disks, the first write to any location on an instance store volume performs more slowly than subsequent writes.
* Amortizing \(gradually writing off\) this cost over the lifetime of the instance might be acceptable.
* However, if high disk performance is required, AWS recommends initializing the drives by writing once to every drive location before production use

---

---



