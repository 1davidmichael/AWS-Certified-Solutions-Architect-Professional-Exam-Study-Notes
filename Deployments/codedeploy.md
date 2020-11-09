# CodeDeploy

* Assists in deploying to multiple AWS services
* Move from v1 -> v2 via CodeDeploy

## EC2

* Deploy to EC2 via `appspec.yml` and deployment strategy
* Will do inplace update to EC2
* Can use hooks to verify the deployment after each deployment phase

## ASG

* 2 kinds - in place and blue/green deploy
* In place - same as above
* blue/green - new ASG created, must be using an ELB

## Lambda

* Use traffic shifting feature of Lambda alias
* Pre/Post traffic hooks
* Easy rollbacks via CloudWatch Alarms
* SAM framework natively uses CodeDeploy

## ECS

* Support for blue/green deploys for ECS/Fargate
* Setup is done within ECS service definition
* A new task set is created and traffic is re-routed to the new task test
* If everything is stable for X minutes the old task set is terminated