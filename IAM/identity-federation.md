# Identity Federation in AWS

Federation lets users outside of AWS assume temporary role for accessing AWS resources. Users assume identity provided by access role.

## Flavors:

* SAML 2.0
* Custom Identity Broker
* Web Identity Federation with Amazon Cognito
* Web Identity Federation without Amazon Cognito
* SSO (Single Sign On)
* Non-SAML with AWS Microsoft AD

Don't need to create IAM users

## SAML 2.0/ADFS

* To integrate AD/ADFS with AWS (Or other SAML 2.0 provider)
* Provide access to AWS Console or CLI
* No need to create IAM user for every employee

**Setup**

* needs trust between AWS IAM and SAML (both ways)
* uses STS API with `AssumeRoleWithSAML`

## Custom Identity Broker Application

* Use only if IDP is not compatible with SAML 2.0
* Users login to identity broker, talks directly with STS API with `AssumeRole` or `GetFederationToken`

## Web Identity Federation

### Without Cognito - AssumeRoleWithWebIdentity

* Not recommended by AWS anymore, use Cognito instead

### With Cognito

* Preferred way for web identity federation
* Build trust between OIDC IDP and AWS
* Support for anonymous users
* Support for MFA (can force it)
* Data synchronization
* Cognito replaces Token Vending Machine (TVM)

### IAM Policy

* Can restrict policy with IAM policy variables in Conditions
* Examples graph.facebook.com, accounts.google.com, cognito-identity.amazonaws.com, can be used in IAM Conditions
