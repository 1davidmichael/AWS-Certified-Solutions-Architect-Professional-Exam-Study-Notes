# Load Balancers

## 3 types

* Classic ELB HTTP, HTTPS, TCP
* ALB, HTTP HTTPS, WebSocket
* NLB, TCP TLS, UDP
* Use ALB/NLB

* Can be public or private

## Classic Load Balancer (ELB)

* Health check can be http or tcp
* Only 1 SSL cert but multiple SAN on cert
* Use ALB with SNI if needed
* Could create multiple ELB
* TCP -> TCP, only way to do 2-way SSL auth

## ALB

* Just layer 7 (http)
* Load balanced to multiple applications, target groups
* Multiple apps on same machine containers
* Redirects
* Can route based on path, hostname, query string, headers
* Good for ECS, Docker
* Can use ALB to invoke Lambda function

### Target Groups

* EC2 - HTTP
* ECS Tasks - HTTP
* Lambda - JSON events
* IP addresses - VPC, on-prem
* Health checks done at target group level

## NLB

* Layer 4 load balancer, TCP/UDP support
* Handle millions of req per second
* one static IP per AZ, helpful for whitelisting
* less latency
* Support for TLS & WebSockets
* Used for extreme performance or TCP/UDP traffic
* AWS Privatre Link

### Target Groups

* EC2
* ECS tasks
* IP addresses
* Proxy Protocol support src, dest, proxy protocol header for source client IP address info

## Cross-Zone Load Balancing

* Distributes traffic evenly across all registered instances in all AZs
* Otherwise it distributes traffic evenly across all instances in the AZ only
* Better load balancing across all instances evenly, but more expensive

* Classic ELB - Disabled by default, no charge
* ALB - Always on, no charge
* NLB - Disabled by default,  you pay for cross-az load balancing

## Stickiness

* Works for ELB/ALB
* Cookie used for stickiness
* Clients won't use data
* May bring some imbalance over instances
* Alternative is to cache session data in ElastiCache/DynamoDB