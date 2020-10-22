# AWS CloudTrail

* Logs API all AWS calls within AWS account
* Can log to CloudWatch Logs, S3
* 90 day retention by default
* UI only shows Create, Modify, Delete events
* Can enable S3 object level

* May take 15 minutes to reach deliver events
* CloudTrail delivery to CloudWatch Logs, events are streamed
* S3 events delivered every 3 minutes

## Solution Architecture

### Delivery to S3

* Setup CloudTrail -> S3 every 5 minutes with SSE-S3 or SSE-KMS encryption
* Lifecycle Policy to move objects to glacier
* S3 events to notify SQS, SNS, Lambda
* CloudTrail directly to SNS -> SNS or SNS -> Lambda

#### S3 Enhancements

* Enable Versioning
* MFA Delete Protection
* S3 Lifecycle
* S3 Object Lock
* KMS encryption
* Feature to perform CloudTrail validation

### Multi-Account/Multi-Region

* CloudTrail -> S3
* Need S3 bucket to allow then to put objects
* Put object via organization IAM condition on bucket policy

### Alert for API calls

* CloudTrail -> CloudWatch Logs
* Metrics filter -> CloudWatch Logs -> Metrics Filter -> CW Alarm -> SNS
* Count by API calls
  * High Deny API calls
  * API calls by user
