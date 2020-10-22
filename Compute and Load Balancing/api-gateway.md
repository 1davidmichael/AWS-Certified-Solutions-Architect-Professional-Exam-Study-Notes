# API Gateway

* Exposes REST API to clients
  * Lambda
  * HTTP
  * Services

## Why

* API versioning
* Authorization
* Traffic management (API keys, throttling)
* Scale
* Serverless
* req/resp transformations
* OpenAPI Spec
* CORS

## Limits

* 29 second timeout
* 10 MB max payload size

## Deployment Stags

* API changes are deployed to stages
* Can have as many stages as we want
* Stages can be rolled back as a history of deployments is kept

## Integrations

* HTTP
  * On-prem, ALB, etc
  * Why? ratelimiting, caching, user auth
* Lambda Function
* AWS Service
  * Step functions workflow
  * SQS
  * Add auth and rate control

### Example

API Gateway in front of S3

* Will hit 10 MB payload limit
* Better option
  * API gateway -> Lambda -> generate presigned S3 URL -> Upload directly to S3

## Endpoint Types

* Edge Optimized - routed through CloudFront, API gateway lives in one region
* Regional - for clients in one region, can combine with CloudFront
* Private - only deployed in VPC, need to use resource policy to define access

## Caching API responses

* Reduces calls to backend
* Default TTL 300 seconds, can set to 0 -> 3600
* Caches are defined per stage
* Can override cache setting per method
* Clients can invalidate cacheed objects
* Can wipe out entire cache
* Encryption options and 0 - 237G

## Errors

* 4XX client error
  * 400 bad req
  * 403 access denied
  * 429 throttling
* 5XX server error
  * 502 incompatible output from lambda and occasional out of order invocations due to heavy load
  * 503 service unavailable
  * 504 integration failure, example is 29 second timeout

## Security

* Can load SSL certs and use Route 53 to define endpoint domain
* Resource Policy
* CORS
* IAM execution roles

### Authentication

* IAM based access, uses sigv4
* Lambda based authorizers
* Cognito User Pools
  * Client must auth with cognito

## Logging, monitoring and tracing

* CloudWatch logs
* Can send to Kinesis Data Firehose
* CW Metrics by stage, latency, cache hit/miss
* X-Ray