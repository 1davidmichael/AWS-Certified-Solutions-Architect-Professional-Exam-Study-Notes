# AWS Key Management Service (KMS)

Similar to developer exam questions.
Easy way to control access to data encryption.

## Integrations

* S3
* EBS
* RDS
* Parameter Store
* etc

## KMS 101

* CMK is used to encrypt data, CMK can be rotated for extra security
* Encrypted secrets can be store in code/env vars
* KMS can only help in encrypting data up to 4KB of data per call
* if data > 4KB use envelope encryption

* Key Policy + IAM Policy to make API calls
* All KMS calls appear in Cloud Trail

## Types

* Customer Managed Key (CMK)
* AWS Managed CMK
  * Managed by AWS
  * Just used for specific services

## How does it work?

**API Calls:**
* `Encrypt`
* `Decrypt`
