# ECS - Elastic Container Service

Container orchestration services for EC2 or Fargate

## Pieces

* ECS Core on EC2
* Fargate
* EKS
* ECR

Very popular for microservices. More efficent than virtual machines.

## Use Cases

* Microservices
  * multiple containers on same machine
  * ALB integration
  * service discovery
  * auto scalaing
* Batch processing/scheduled tasks
  * Schedule ECS to run on-demand/reserved/spot
* Migrate to AWS

## ECS Classic

* EC2 runs ECS agent
* ECS Service -> Task and definition
* Tasks have their own IAM roles for security
* Deep integration with ALB
  * Dynamic Port Mapping

## Fargate

* Don't need to manage EC2 instances, AWS managed, serverless
* Create task definition and AWS runs them for us
* Runs on firecracker

## ECS Security and Networking

* IAM security
  * EC2 instance role
  * ECS task level roles (maximum security)
  * Secrets/Config injected into env vars via SSM parameter store/secrets manager
* Task networking
  * none
  * bridge - dockers virtual container based network
  * host - uses underlying host network interface
  * awsvpc - every task gets its own ENI/private IP (default for Fargate)

## Autoscaling

* CPU and RAM tracked in Cloudwatch per ECS service level
* Can use target tracking, step scaling, scheduled scaling
* ECS Service Scaling != EC2 auto scaling
* Fargate auto sclaing is easier to setup

## ECS - Spot Instances

* ECS Classic
  * terminated instances go into draining mode
  * less reliable
* Fargate Spot
  * Specify minimum on-demand task
  * have baseline on-demand, then spot tasks can be reclaimed
* RIS also available for ECS classic