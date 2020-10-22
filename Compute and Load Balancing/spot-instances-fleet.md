# Spot Instances and Spot Fleet

## EC2 Spot Instances

* Large discount over ec2
* Define max spot price and get instance while current spot price < max spot
* Can/stop terminate with 2 minute grace period
* Spot Block
  * Block spot instance during a specified time range 1-6 hours no interruptions
  * In rare situations the instance maybe reclaimed
* Use for batch jobs, data analysis or workloads resilient to failure

## Spot Fleet

* Collection of spot/on-demand instances
* Mix of instance types
* Supports ec2 stand alone, ASG, ECS, AWS batch
* Soft limits
  * up to 10K instances
  * target capacity across all in a region 100K