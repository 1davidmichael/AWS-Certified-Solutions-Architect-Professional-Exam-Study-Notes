# Storage Gateway

* Bridge between on-prem data and cloud data in S3

## Types

* File Gateway
* Volume Gateway
* Tape Gateway

## File Gateway

* Virtual appliance bridge between on-prem and S3 via NFS/SMB
* Metadata and dir structure preserved
* Bucket access using IAM role for S3
* Most recently used data cached in file gateway
* Mounted on many servers

### Backup/Lifecycle Policies

* Define lifecycle policies for backup/cost savings
* Object versions
* Must use RefreshCache API to notify gateway about restore
* S3 Object Lock
  * write once, read many (WORM) data
  * might be needed for compliance reasons

## Volume Gateway

* Block storage backed by iSCSI backed by S3
* Cached volumes: Low latency to most recent data, full data on S3
* Stored volumes: entire data set is on-prem, scheduled backups to S3
* Can create EBS snapshots ffrom the volumes and restore as EBS
* Up to 32 volumes per gateway
  * Each volume up to 32 TB in cached mode or 16 TB in stored mode

## Tape Gateway

* Virtual Tape Library (VTL) backed by S3
* Once tapes are in S3 you need to restore the entire tape to access a single file