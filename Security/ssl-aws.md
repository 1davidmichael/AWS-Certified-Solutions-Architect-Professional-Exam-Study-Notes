# SSL/TLS - Basics

SSL = Secure Socket Layer
TLS = Transport Layer Security

## How does TLS work?

* Asymmetric Encryption is expensive
* SSL only for Asymmetric
* Asymmetric handshake is used for handshake then it is symmetrical
* Possible to have two way authentication with both client and server keys

## SSL SNI - Server Name Indication

* Used to solve problem of loading multiple SSL certs on one web server
* Supported for ALB/NLB/CloudFront
* Not-Supported by ELBs (old-gen)

## Protect for MITM attacks

* Use https to avoid MITM
* CA trust used to validate HTTPS
* Don't trust unknown root CAs
* Use DNS that has DNSSEC, prevents forged DNS responses
  * DNSSEC not supported by Route 53

Why cover this?!? Stupid section.
