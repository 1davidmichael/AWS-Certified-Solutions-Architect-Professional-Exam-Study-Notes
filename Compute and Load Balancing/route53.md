# Route 53

Managed DNS service

## Types

* A
* AAAA
* CNAME
* Alias
  * Can point to AWS services
  * Can point to apex domain
* SOA, MX, TXT not needed for exam

## TTL

* Time to live cache
* Measured in seconds
* TTL mandatory for each DNS record

## Routing Policies

* Simple - maps single hostname to resource
* Weighted - Control % to various specific endpoints
  * Split traffic
  * Can associate with health checks
  * Weights don't need to equal to 100
* Failover - active/passive
  * Health check on primary, optional on secondary
* Latency - directed to server with least latency
  * Failover with healthchecks
* Geolocation
  * Based on location
  * Create a default policy if there is no match
* Complex/Nested records
  * Latency Record -> Alias to Weighted Record
  * Can do complex records
* Multi-valued routing, not subsitute for ELB (not covered on exam)
  * multiple values for A record

## Good to know

* Private DNS
  * Used to route to internal private DNS
  * Enable DNSHostName, enableDnsSupport
  * DNSSEC, only for domain registration, not for service
* Can use 3rd party registrar

## Health Checks

* Used for automated DNS failovers
* Monitor
  * endpoint
  * calculated health checks
  * CloudWatch Alarms

### Good to know

* pass/fail or text in beginning of the response 5120 bytes
* pass only if 2xx or 3xx responses
* calculated health checks, specify how many need to pass
* Can trigger CW alarms

### Private hosted zones

* health checks are outside of VPC, can't access private endpoints
* Check within VPC by assigning public subnet
* or check resources
* or check cloudwatch metrics

### Share private zone across VPCs

* Can share private zone via peering links, must associate VPC with central hosted zone