# AWS Systems Manager

* Helps to manage EC2 and On-prem systems at scale
* Get operational insights about the state of infra
* Patching automation for enhanced compliance
* Free service

## Features

* Resource Groups
* Insights
  * Insights Dashboard
  * Inventory
  * Compliance
* Parameter Store
* Actions
  * Automation
  * Run Command
  * Session Manager
  * Patch Manager
  * Maintenance Windows
  * State Manager

## Systems Manager - How It Works

* Need to install SSM agent on to systems we control
* Installed by default on AMZNL1/2 some Ubuntu
* If instance can't be controlled probably issue with SSM agent or role

## Run Command

* Document, script or single command
* Run across multiple instances using resource groups
* Rate Control/Error Control
* Integrated with IAM * CloudTrail
* **No SSH needed**
* Results displayed in console

## Patching

* Need to define patch baseline to determine which patches should be installed
* Linux
  * `AWS-AmazonLinux2DefaultPatchBaseline`
  * `AWS-CentOSDefaultPatchBaseline`
  * `AWS-RedHatDefaultPatchBaseline`
  * `AWS-SuseDefaultPatchBaseline`
  * `AWS-UbuntuDefaultPatchBaseline`
* Windows
  * Patches auto-approved 7 days after release
  * `AWS-DefaultPatchBaseline`
  * All critical/security updates
  * Other baseline that includes Microsoft applications
* Can define custom patch baseline

### Steps

1. define patch baseline
1. define patch groups, based on tags
1. define maintenance window
  * schedule, duration, registered targets/patch groups
1. Add `AWS-RunPatchBaseline` Run Command
1. define rate control
1. monitor patch compliance using SSM

## Parameter Store

* Secure storage for config/secrets
* Optional seameless encryption with KMS
* Serverless, scalable, durable, easy SDK, free
* Version tracking
* Config management using path & IAM
* Notification with CloudWatch Events
* Integration with CloudFormation