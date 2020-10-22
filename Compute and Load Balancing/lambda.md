# AWS Lambda

Lot of details on Lambda in exam

## Integrations

* AWS gateway
* Kinesis
* DynamoDB
* S3
* AWS IoT
* CloudWatch Events
* CloudWatch Logs
* AWS SNS
* AWS Cognito
* AWS SQS

## Use case

* S3 image manipulation
* Serverless `cron` jobs

## Language Support

* NodeJS
* Python
* Ruby
* Java
* Golang
* .NET Core, C#, Powershell
* Custom runtimes available via layers

If you see docker use ECS/Fargate/Batch, not Lambda!

## Limits

* RAM: 128MB -> 3G
* CPU: Linked to RAM but not directly controlled, +1.5 RAM adds a vCPU, So must be multithreaded to take advantage of it
* Timeout: 15 minutes
* /tmp, 512M, can't process large files
* Deploy package limit of 250MB
* Concurrency execution, 1000 - soft limit that can be increased

## Latency Consideration

* Cold Lambda ~ 100ms
* Warm Lambda ~ ms
* Provisioned Concurrency to reduce # of cold starts
* API Gateway ~ 100ms
* All these add up...
* X-Ray can help visualize end-to-end latency

## Security

* IAM roles grant access to other services
* Resource-based Policies for Lambda
  * Allows resources to invoke Lambdas
  * Allow other accounts to invoke Lambdas

## In a VPC

* Default not in VPC
* Lambda needs to be in VPC to access VPC resources
* Needs ENI/Security Group in VPC
* Also needs NAT->IGW to access internet when in VPC
* If in VPC use VPC endpoint gateway to reduce cost
* CloudWatch logs works with/without endpoint/gateway

## Logging, Monitoring and Tracing

* Logs in Cloudwatch Logs
* CloudWatch Metrics
* Lambda needs role that authorizes access to CloudWatch
* X-Ray
  * Tracing

## Synchronous Invocations

* CLI, SDK, API Gateway
* Code waits for results, error handling must happen client side

## Asynchronous Invocation

* SNS, S3, CloudWatch events
* Lambda will retry 3 times if there is a failure
* Make sure processing is idempotent
* Define DLQ SNS/SQS for failed events

## Event Source Mapping Invocation

* SQS, Kinesis Data Streams, DynamoDB streams
* Must pull data from source
* All records are processed in correct order except SQS
* Polls data source, then invoke lambda with event
* Failures will stop processing until resolved or DLQ

## Lambda Destinations

AWS recommends you use destinations instead of DLQ

* Nov 2019 release
* Async - destination for successful or failed events
  * SNS, SQS, Lambda, Event Bridge destinations
* Event source mapping
  * only for discarded event batches
  * SQS, SNS destinations
  * Can create DLQ directly from SQS

## Lambda Versions

* Always work on `$LATEST` (mutable)
* Versions are immutable
* Increasing numbers, each has their own ARN

## Aliases

* Pointers to Lambda function versions
* Alias are mutable, point to various versions
* Enable Blue/Green deployments
* Aliases can point to multiple versions and be weighted

## Api Gateway with Aliases

* Api gateway points to Alias
* Alias can then be modified to point to tags

## Lambda + CodeDeploy

* Used to automate traffic shift for Lambda aliases, mentioned above
* Feature integrated with SAM framework
* Strategies
  * Linear, 10% every X minutes
  * Canary, try X% for given time period
  * AllAtOnce, immediate
* Create pre/post traffic hook for migration
* Automated rollback possible