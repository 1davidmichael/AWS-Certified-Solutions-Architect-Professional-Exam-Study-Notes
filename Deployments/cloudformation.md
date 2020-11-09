# CloudFormation

* IAC in AWS
* Portable across accounts/regions
* Backbone of SAM, Service Catalog, Elastic Beanstalk
* Must know service as developer, sysop, architect

## Need to know

* ASG - CFN manages the ASG, not the underlying EC2
  * Define success conditions for launch of EC2 instances `CreationPolicy`
  * Update strategies for EC2 called `UpdatePolicy`

* Retaining Data
  * Can set `DeletionPolicy` on all resources
  * `Retain`
  * `Snapshot`
  * `Delete`

## Security

* Uses permissions of our own IAM principal
* Can assign an IAM role to a stack to perform the actions
* If creating IAM resources must provide capabilities
  * `CAPABILITY_IAM`
  * `CAPABILITY_NAMED_IAM`

## Custom Resources

* Custom resources can be created with Lambda

## Cross/Nested Stack References

* Cross Stacks - helpful when stacks have different lifecycles
  * Use Import/Exports

* Nested Stacks
  * Helpful when reusing components