# AWS Batch

* Run batch jobs as docker images
* Dynamic provisioning of EC2/Spot instances in VPC
* Optimal quantity/type
* No need to manage clusters
* You pay for underlying EC2
* Schedule jobs with CloudWatch events
* Orchestrate with Step Functions

## Architecture

* Creates ECS or spot fleet cluster
* Docker image runs based on calls from Lambda or CloudWatch events trigger
* Pulls from ECR

## Batch vs Lambda

* No time limit for batch
* Any runtime
* More disk space, EBS/instance store
* Relies on EC2

## Compute Environments

* Managed Compute Environments
  * Managed by AWS, you choose spot/ec2
  * Runs in your VPC
* Unmanaged Compute Environment
  * You control/manage instance config/scaling

## Managed Compute Environment

* set min/max vCPU
* Spot Instances based off min/max vCPU
* Batch Job Queue -> AWS Batch instances
* Can enable autoscaling to handle changes in demands

## Multi-Node Mode

* Good for large scale high performance computing
* Leverages multiple EC2/ECS instances at the same time
* 1 main node manages many child nodes
* Works better if you use cluster mode for placement group