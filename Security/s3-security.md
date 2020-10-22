# S3 Security

## Encrypt objects in S3

1. SSE-S3, AWS managed keys
1. SSE-KMS use KMS to encrypt objects
1. SSE-C manage own encryption keys, can come from CloudHSM
1. Client side encryption
* Glacier all AES-256 encrypted

## Events in S3 buckets

* S3 access logs
* S3 event notifications
* S3 CloudTrail object logs
* Trusted advisor, check bucket permissions

## S3 Security

* IAM permissions
* Resource Based bucket policies
  * Cross-account access
  * grant public access
  * force objects to be encryped at upload
  * optional conditions, by elastic IP
  * Source VPC/VPC endpoint
  * CloudFront OAI
  * MFA
* S3 pre-signed URLS
  * for download/upload
  * valid for default 1 hr
  * users inherit permissions of users who created pre-signed url

## VPC endpoint gateway for S3

* By default S3 access from VPC is done over public internet
* Create VPC endpoint for S3 to access S3 via VPC endpoint gateway, all traffic stays in private network

## S3 object lock/glacier vault lock

* Adopt WORM (write once read many)
* block an object deletion for a specified amount of time
