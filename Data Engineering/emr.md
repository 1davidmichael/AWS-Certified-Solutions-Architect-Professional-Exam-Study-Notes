# AWS EMR

* Elastic Map Reduce to do Hadoop Cluster for Big Data
* Made of 100s of EC2 instances potentially
* Supports Apache Spark, HBase, Presto, Flink
* EMR handles provisioning and configuration of EC2
* Autoscaling with CloudWatch

## Integrations

* Launched in VPC, in single AZ
* Use EMRFS (S3) for permanent storage


## Node types and purchasing

* Master node, manages cluster
* Core Nodes, running tasks and storing data
* Task Node (optional), just run tasks

## Purchasing Options

* On-demand, most expensive
* RIs for EMR
* Spot Instances, terminated occasionally and less reliable

## Instance Configuration

* Uniform instance groups
* Instance fleet, set target capacity
  * No autoscaling
  * mix and match instance types and purchase options
  * spot fleet for EMR