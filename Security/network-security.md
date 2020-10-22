# Network Security


## Basics

* Security groups
  * attached to ENI
  * Stateful
  * Reference by CIDR/security group ids
  * Cross-account/VPC groups
  * default inbound denied, outbound allowed
* NACL (Network ACL)
  * Attached at subnet
  * Stateless
  * Only CIDR ranges
  * Default allow all in and out
  * New NAC denies all inbound denies all outbound
* Host Firewall
  * on EC2, customer configured

## DDOS

Distributed Denial-of-Service

* SYN Flood
* UDP reflection
* DNS flood attack
* Slow Loris
* Application Level Attacks

## DDOS Protection on AWS

* AWS Shield Standard - for all customers, no additional cost
* AWS Shield Advanced - 24/7 premium DDOS protection
* AWS WAF
* CloudFront/Route 53
* Be ready to scale
* Separate static/dynamic resources
* DDOS security whitepaper from AWS

## AWS Shield

* Standard, free, protects from layer 3/4 attacks
* Advanced, DDOS mitigation $3000 per month per org
* Protect against higher fees during usage spikes due to DDOS

## WAF

* Protects against common layer 7 exploits
* ALB, API Gateway, CloudFront
* Rules, size, geo, rate, http rules

## Firewall Manager

* Common set of security rules across AWS Organization
