# STS

STS = AWS Security Token Service

STS can be used to provide time based access in AWS to an AWS IAM role. Either within your account or to other accounts/services.

* Can require MFA.
* Auditable via CloudTrail
* Time based limits for how long the role can be kept assumed

* External ID used for providing 3rd party access
  * Use IAM Access Analyzer to find which resources are exposed
  * External ID secret between you and third party
  * Confused deputy: <https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-user_externalid.html#external-id-purpose>

## Important APIs

* `AssumeRole`
* `AssumeRoleWithSAML`
* `AssumeRoleWithWebIdentity`
* `GetSessionToken`
* `GetFederationToken`
