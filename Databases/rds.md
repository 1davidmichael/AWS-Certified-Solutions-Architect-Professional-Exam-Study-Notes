# RDS

## Engines
  * PostgreSQL
  * MariaDB
  * MySQL
  * Oracle
  * Microsoft SQL Server

* Managed DB
* Launched in VPC
* Stored by EBS, can increase by autoscaling gp2 vs io1
* Backups - automated point-in-time recovery
* Snapshots, can copy across regions
* RDS Events, get notified via SNS

## Multi-AZ & Read Replicas

* Automated failover, not active/active
* Read-Replicas, async, can be cross-region

## Security

* Oracle/SQL Server for transparent data encryption
* No IAM permissions
* Create encrypted from unencrypted RDS
* CloudTrail cannot track queries
* IAM auth for MySQL and PostgreSQL