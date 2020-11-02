# CloudWatch

## CloudWatch Metrics

* EC2 Default 5 minutes, detailed monitoring every 1 minute
* EC2 RAM not monitored by default
* Custom Metrics available down to 1 second resolution
* **triggers**
  * EC2 action, autoscaling, sns
  * Alarm events can be intercepted by CloudWatch Events

## CloudWatch Events

* Intercept events from AWS services
* EC2, code build, S3
* Can get any API call from CloudTrail integration
* **targets**
  * Lambda, Batch, ECS
  * Step functions, code build
  * SSM, ec2 actions
  * SQS, SNS, Kinesis data streams, fire hose

## CloudWatch Logs

* Sources - CloudWatch Logs Agent, CloudWatch Unified Agent, SDK
* Beanstalk
* ECS logs from containers
* Lambda
* VPC flow logs
* CloudTrail
* API Gateway
* Route 53 Dns queries

### How it works

* Log groups
* Log streams
* Define log expiration policies
* Can send logs to other locations
  * S3
  * Kinesis data stream
  * Kinesis fire hose
  * Lambda
  * ElasticSearch

### Metric Filter & Insights

* Use filter expressions to create metric and alarms
* Insights has ability to query logs and add to dashboards

### Export

* S3 Export must be encrypted with SSE-S3, not SSE-KMS
* Not real time, up to 12 hours to export
* API call

* Subscription filter to multiple outputs
  * Lambda
  * Kinesis data firehose -> S3 or -> ElasticSearch
  * Kinesis data streams