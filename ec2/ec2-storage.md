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
* Instance store storage is located on the disks that are physically attached to the host computer.
* Instance store is ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temporary content, or for data that is replicated across a fleet of instances, such as a load-balanced pool of web servers.
* An instance store consists of one or more instance store volumes exposed as block devices.
* Size of an instance store varies by instance type.
* Virtual devices for instance store volumes are ephemeral\[0-23\], starting the first one as ephemeral0 and so on.
* While an instance store is dedicated to a particular instance, the disk subsystem is shared among instances on a host computer.

### Instance Store Lifecycle

* Instance store data lifetime is dependent on the lifecycle of the Instance to which it is attached
* Data on the Instance store persists when an instance is rebooted
* However, the data on the instance store does not persists if the
  * underlying disk drive fails
  * instance stops i.e. if the EBS backed instance with instance store volumes attached is stopped
  * instance terminates
* If an AMI is created from an Instance with Instance strore volume, the data on its instance store volume isn’t preserved

### Instance Store Volumes

* Instance type of an instance determines the size of the instance store available for the instance, and the type of hardware used for the instance store volumes
* Instance store volumes are included as part of the instance’s hourly cost.
* Some instance types use solid state drives \(SSD\) to deliver very high random I/O performance, which is a good option when storage with very low latency is needed, but the data does not need to be persisted when the instance terminates or you can take advantage of fault tolerant architectures.

### Instance Store Volumes with EC2 instances

* EBS volumes and instance store volumes for an instance are specified using a block device mapping
* Instance store volume can be attached to an EC2 instance only when the instance is launched
* Instance store volume cannot be detached and reattached to a different instance
* After an instance is launched, the instance store volumes for the instance should be formatted and mounted before it can be used.
* Root volume of an instance store-backed instance is mounted automatically.

### Instance Store Optimizing Writes

* Because of the way that Amazon EC2 virtualizes disks, the first write to any location on an instance store volume performs more slowly than subsequent writes.
* Amortizing \(gradually writing off\) this cost over the lifetime of the instance might be acceptable.
* However, if high disk performance is required, AWS recommends initializing the drives by writing once to every drive location before production use

---

---

# EC2 Elastic Block Storage – EBS Overview

* Amazon EBS provides highly available, reliable, durable, block-level storage volumes that can be attached to a running instance
* EBS as a primary storage device is recommended for data that requires frequent and granular updates 
  _for e.g. running a database or filesystems_
* An EBS volume behaves like a raw, unformatted, external block device that can be attached to a single EC2 instance at a time
* EBS volume persists independently from the running life of an instance.
* An EBS volume can be attached to any instance within the **same Availability Zone**, and can be used like any other physical hard drive.
* EBS volumes allows encryption using the Amazon EBS encryption feature. All data stored at rest, disk I/O, and snapshots created from the volume are encrypted. Encryption occurs on the EC2 instance, providing encryption of data-in-transit from EC2 to the EBS volume
* EBS volumes can be backed up by creating a snapshot of the volume, which is stored in Amazon S3.  EBS volumes can be created from a snapshot can be attached to an another instance within the same region
* EBS volumes are created in a specific Availability Zone, and can then be attached to any instances in that same Availability Zone. To make a volume available outside of the Availability Zone, create a snapshot and restore that snapshot to a new volume anywhere in that region
* Snapshots can also be copied to other regions and then restored to new volumes, making it easier to leverage multiple AWS regions for geographical expansion, data center migration, and disaster recovery.
* EBS Magnetic volumes can be created from 1 GiB to 1 TiB in size; EBS General Purpose \(SSD\) and Provisioned IOPS \(SSD\) volumes can be created up to 16 TiB in size
* General Purpose \(SSD\) volumes support up to 10,000 IOPS and 160 MB/s of throughput and Provisioned IOPS \(SSD\) volumes support up to 20,000 IOPS and 320 MB/s of throughput.

## Benefits

* Data Availability
  * EBS volume is automatically replicated in an Availability Zone to prevent data loss due to failure of any single hardware component.
* Data Persistence
  * EBS volume persists independently of the running life of an EC2 instance
  * EBS volume persists when an instance is stopped and started or rebooted
  * Root EBS volume is deleted, by default, on Instance termination but can be modified by changing the DeleteOnTermination flag
  * All attached volumes persist, by default, on instance termination
* Data Encryption
  * EBS volumes can be encrypted by EBS encryption feature
  * EBS encryption uses 256-bit Advanced Encryption Standard algorithms \(AES-256\) and an Amazon-managed key infrastructure.
  * Encryption occurs on the server that hosts the EC2 instance, providing encryption of data-in-transit from the EC2 instance to EBS storage
  * Snapshots of encrypted EBS volumes are automatically encrypted.
* Snapshots
  * EBS provides the ability to create snapshots \(backups\) of any EBS volume and write a copy of the data in the volume to Amazon S3, where it is stored redundantly in multiple Availability Zones
  * Snapshots can be used to create new volumes, increase the size of the volumes or replicate data across Availability Zones
  * Snapshots are incremental backups and store only the data that was changed from the time the last snapshot was taken.
  * Snapshots size can probably be smaller then the volume size as the data is compressed before being saved to S3
  * Even though snapshots are saved incrementally, the snapshot deletion process is designed so that you need to retain only the most recent snapshot in order to restore the volume.

## EBS Volume

### EBS Volume Types

Refer to My Blog Post about[EBS Volume Types](http://jayendrapatil.com/aws-ebs-volume-types/)

### EBS Volume Creation

* EBS volume can be created either
  * Creating New volumes
    * Completely new from console or command line tools and can then be attached to an EC2 instance in the same Availability Zone
  * Restore volume from Snapshots
    * EBS volumes can also be restored from a previously created snapshots
    * New volumes created from existing EBS snapshots load lazily in the background.
    * There is no need to wait for all of the data to transfer from S3 to the EBS volume before the attached instance can start accessing the volume and all its data.
    * If the instance accesses the data that hasn’t yet been loaded, the volume immediately downloads the requested data from Amazon S3, and continues loading the rest of the data in the background.
    * EBS volumes restored from encrypted snapshots are encrypted by default
  * EBS volumes can be created and attached to a running EC2 instance by specifying a block device mapping

### EBS Volume Detachment

* EBS volumes can be detached from an instance explicitly or by terminating the instance
* EBS root volumes can be detached by stopping the instance
* EBS data volumes, attached to an running instance, can be detached by unmounting the volume from the instance first. If the volume is detached without being unmounted, it might result the volume being stuck in the busy state and could possibly damaged the file system or the data it contains
* EBS volume can be force detached from an instance, using the Force Detach option, but it might lead to data loss or a corrupted file system as the instance does not get an opportunity to flush file system caches or file system metadata
* Charges are still incurred for the volume after its detachment

### EBS Volume Deletion

* EBS volume deletion would wipe out its data and the volume can’t be attached to any instance. However, it can be backed up before deletion using EBS snapshots

## EBS Volume Snapshots

Refer to My Blog Post about[EBS Snapshot](http://jayendrapatil.com/aws-ebs-snapshot/)

## EBS Encryption

* EBS volumes can be created and attached to a supported instance type, and supports following types of data
  * Data at rest
  * All snapshots created from the volume
  * All disk I/O
* Encryption occurs on the servers that host EC2 instances, providing encryption of data-in-transit from EC2 instances to EBS storage.
* EBS encryption **is supported with all EBS volume types**\(gp2, io1 and standard\), and has the same IOPS performance on encrypted volumes as with unencrypted volumes, with a minimal effect on latency
* EBS encryption is **only available on select instance types**
* **Snapshots of encrypted volumes and volumes created from encrypted snapshots are automatically encrypted using the same volume encryption key**
* EBS encryption uses AWS Key Management Service \(AWS KMS\) customer master keys \(CMK\) when creating encrypted volumes and any snapshots created from the encrypted volumes.
* EBS volumes can be encrypted using either
  * a default CMK is created for you automatically.
  * a CMK that you created separately using AWS KMS, giving you more flexibility, including the ability to create, rotate, disable, define access controls, and audit the encryption keys used to protect your data.
* Public or shared snapshots of encrypted volumes are not supported, because other accounts would be able to decrypt your data and needs to be migrated to an unencrypted status before sharing.
* **Existing unencrypted volumes cannot be encrypted **directly, but can be migrated by
  * create a unencrypted snapshot from the volume
  * create an encrypted copy of unencrypted snapshot
  * create an encrypted volume from the encrypted snapshot
* Encrypted snapshot can be created from a unencrypted snapshot by create an encrypted copy of the unencrypted snapshot
* Unencrypted volume cannot be created from an encrypted volume directly but needs to be migrated

## EBS Performance

Refer to My Blog Post about[EBS Performance](http://jayendrapatil.com/aws-ebs-performance)

---

---


