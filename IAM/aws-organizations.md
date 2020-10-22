# AWS Organizations

A way to manage multiple AWS accounts

* Master account must invite all child accounts
* Master account can create accounts
* Master account can manage child accounts
  * CloudFormation StackSets to create IAm roles in target accounts
  * Assume the roles using the STS cross-account capabilities
* Strategy to create dedicated logging/security accounts
* API available to create AWS accounts
* Integration with AWS SSO


## Features

* Consolidated billing, single payment, aggregated costs
* Enable all features
  * consolidated billing
  * Use SCP
  * Invited accounts must approve all features
  * Can't swap back
  * SCP can restricts accounts from leaving

## Multi-Account Strategies

* Create accounts er department, environment, cost center, etc
* Multiple VPC vs One account VPC
* Use tagging standards for billing
* Send CloudWatch logs/CloudTrail to central logging account

### OUs

* Root OU is master account
* Divide accounts into various OUs (Organizational Units) for better management

## SCP

**Example:**

* Dev OU
* Prod OU
  * Finance OU
  * HR OU

* Apply SCP to accounts by OU, whitelist/blacklist various IAM actions
* Applied to all users/roles of the account, does not effect service linked roles
* Must have explicit `Allow`
* Explicit `Deny` overrides explicit `Allow`

## Reserved Instances

* All accounts can receive hourly cost benefits for Reserved Instances by any other accounts
* If you disable RI sharing RIs and Savings Plan is not shared
