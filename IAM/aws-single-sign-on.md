# AWS Single-Sign-On (SSO)

* Centrally manage AWS account access, applications, etc
* Integrates with AWS Organizations
* Support SAML 2.0
* Integrates with on-prem AD
* Centralized Permission management
* CloudTrail logging

## Options for Integration

1. Stand-alone AWS managed Microsoft AD
1. AD Connector
1. AWS Managed Microsoft AD with two-way forest trust with on-prem AD

## Why SSO vs `AssumeRolewithSAML`

* Avoids 3rd party IDP login portal
* Avoids STS direct interaction, SSO does that for us
