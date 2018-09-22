backup

*   * preferred backup window
  * backup retention period
  * I/O suspension for single
  * Point-In-Time Recovery
* snapshot
 
  * DB Snapshots make entire DB instance
  * from one region to another region,a copy retain in that region
  * Because KMS encryption keys are specific to the region that they are created in, encrypted snapshot cannot be copied to another region
  * DB Snapshot Sharing
 
    * DB snapshot that uses an option group with permanent or persistent options cannot be shared
    * KMS key policy must first be updated by adding any accounts to share the snapshot with, before sharing an encrypted DB snapshot
* replication
 
  * routing read queries from applications to the Read Replica
  * Failover mechanism automatically changes the DNS record of the DB instance to point to the standby DB instance
  * Multi-AZ deployment
 
    * read-only traffic, use a Read Replica.
    * synchronous standby replica in a different Availability Zone
    * must be in same region
    * Read Replica
 
      * RDS sets up a secure communications channel between the source DB instance and the Read Replica, if that Read Replica is in a different AWS region from the DB instance
      * replication link is broken, A Read Replica can be promoted to a new independent source DB
      * use some tools like HAPROXY, with two url ,one for write one tor read
* security
 
  * Encryption enabled at creating, can not change key later
  * Once encryption, log,snapshot,autobackup, replica are encripted
  * Cross region replicas and snapshots copy does not work since the key is only available in a single region
  * Database security groups default to a “deny all” access mode
* monitor
 
  * 监控的metric 16 项, ReplicaLag
  * Backup not notify for snapshot
* maintenance
 
  * Multi-AZ deployment, preform standby, promote standby, preform old primary
  * RDS takes two DB snapshots , before upgrade, after upgrade



