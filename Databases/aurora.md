# RDS Aurora

DB Engines

* Engines: MySQL/PostgreSQL
* Storage: auto-grows up to 64TB
* Read Replicas: up to 16 reader endpoint to access them all
* Cross-Region read replicas: entire database is copied
* Load/Offload data to S3

## Scalability

* 6 copies across 3 AZs
* 4 copies out of 6 needed for writes
* 3 of 6 needed for reads
* self-healing with peer to peer replication
* Storage is striped across 100s of volumes
* Automated failover in less than 30 seconds
* Support for cross-region replication

## Cluster

* Data is shared across the cluster
* Smallest is 10G in size

## Aurora Serverless

* Automated database instantiation and scaling
* Good for infrequent workloads
* No capacity planning
* Pay more per second

## Global Aurora

* Cross-region read replicas
* Aurora Global Database
  * 1 primary region read/write
  * up to 5 secondary regions
  * up to 15 read replicas per secondary region
  * promoting another region has RTO of < 1 minute

## Multi-master

* If you want immediate failover, every note can do read/write
* Newer feature
