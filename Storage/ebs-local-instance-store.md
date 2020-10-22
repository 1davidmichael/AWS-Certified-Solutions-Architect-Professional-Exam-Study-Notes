# EBS & Local Instance Storage

* network drive attached to single instance only
* per az, moved by snapshotting
* volumes can be resized
* choose EBS type to enjoy maximum throughput

## Types

* GP2, 3 IOPS/GiB, 100 IOPS, bursts to 3000 IOPS, max 16000 IOPS
* io 1, choose amount of IOPS 100 IOPS min -> 64000 Nitro or 32000 on other
  * 4 GB -> 16TB
* st 1, throughput optimized HDD
* sc 1 cold HDD

## EBS RAID config

* Raid0, stripe
* Raid1, mirror


## Snapshots

* Incremental
* stored in S3
* Use IO, so don't do while busy
* Not necessary to detach but recommended
* Can make AMI from EBS snapshot

## Local EC2 Instance Store

* Very High IOPS
* Physical disk attached to EC2
* Up to 7.5 TB
* Can stripe
* No resizing
* Risk of data loss

## EBS vs Instance Store

* Some instances do not have root EBS volume
* Instance store = ephemeral
* Instance store is great for cache, scratch data, etc
* Instance store data survives reboots
* Instance store stop/terminate data is lost