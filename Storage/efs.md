# EFS - Elastic File System

* Linux based system
* POSIX complaint
* Encryption at rest with KMS

## Performance and Storage

* Scales to 1000 of concurrent NFS clients, 10 GB+/s throughput
* Grow to Petabyte scale
* Performance Mode
  * General Purpose - web server
  * MAX I/O - big data, media
* Throughput mode
  * Bursting Mode - intensive workload, then nothing
  * Provisioned I/O - high throughput to storage ratio
* Storage tiers
  * standard
  * infrequent access

## On-Premise & VPC Peering

* EFS available over VPC peering
* On-prem can access via Direct Connect or site to site VPN