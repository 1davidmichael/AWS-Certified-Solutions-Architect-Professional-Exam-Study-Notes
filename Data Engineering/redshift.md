# RedShift

* Postgres -> OLAP, MPP, Columnar
* Integrated with multiple AWS services
* Launched Feb 2013
* Fully managed AWS service

## What is it?

* Relational data warehouse
* Massively parallel, petabyte scale
* HDD & SDD platforms
* Massively Parallel, shared nothing columnar architecture
* Used for data analytics, along with EMR (EMR is managed Hadoop)
* $1,000/TB/Year, starts at $0.25

## Why use it?

* Cheaper than traditional datawarehousing tools
* No programming standard SQL interface
* Integrates well with Hadoop, machine learning and streaming tools
* Can load data directly from S3 with a role

## Architecture

* **Leader node** that you use to access cluster
  * Simple SQL endpoint
  * Stores Metadata
* **Compute Nodes**
  * local columnar storage
  * parallel distributed execution of all queries, loads, backups, restores and resizes

## Benefits

### Fast

* Less I/O
* column storage
* data compression
* direct-attached storage
* large data block sizes
* zone maps
* Need to review sort keys for Redshift

#### Parallel and Distributed

* Performance grows linearly as you add nodes
* Load data into Redshift via S3 in parallel, other operations as well
* Can handle data in multiple ways
  * Distribute data evenly
  * Distribute data on all nodes
  * Distribute data via key, so queries stay on a single node

#### Runs on optimized hardware

* SSD vs HDD
* Can easily migrate between hardware types for upgrades or better performance

### Inexpensive

* No cost for leader node

### Fully Managed

* **Continous/Incremental backups**
  * backed up to S3
  * Streaming restore, create a cluster from backup and start querying in > 3 minutes

* **Fault tolerant**
  * Disk failures
  * Node failures
  * Network failures
  * AZ/Region level disasters

### Security

* Designed with enterprise level security
* load encrypted from S3
* VPC for isolation
* Encrypted data at rest
* Audit logging
* Lots of compliances met

### Powerful

* Python, R, SAS, Machine Learning support