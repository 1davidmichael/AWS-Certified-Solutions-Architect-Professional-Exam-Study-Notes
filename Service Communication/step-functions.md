# Step Functions

* Build serverless visual workflow to orchestrate lambda functions
* Json state machine
* Max workflow is 1 year
* Has human approval feature

## Phases

* Success
* Failed
* Cancelled
* In Progress

## Applications

* If you need to chain and orchesrate stuff use step functions

## Tasks

* Lambda Task
  * Invoke Lambda
* Activity Task
  * poll step function service
* Service Task
  * Connect to a supported AWS service
  * Lambda, ECS Task, Fargate, DynamoDB, Batch, SNS, SQS
* Wait task
  * Wait

!! Step Functions does not integrate with Mechanical Turk