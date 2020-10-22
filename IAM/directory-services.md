# Directory Services

## What is Microsoft Active Directory?

* Found on any Windows Server with AD Domain Services
* Database of objects, users, computers, printers
* Grouped into Tree, Group of Trees if forest
* Directory service used for centralized logins

## What is ADFS

* Provides single sign on across applications
* SAML across 3rd party applications, AWS, Dropbox, Office 365, etc

## AWS Directory Services

1. AWS Managed Microsoft AD
  * Create own AD in AWS, manage users locally, supports MFA
  * Establish "trust" connections with your on-prem AD
  * Two places where users are defined
1. AD Connector
  * Proxy to on-prem AD
  * Users manged in the on-prem AD
  * One places where users are defined
1. Simple AD
  * AD compatible managed directory on AWS
  * Cannot be joined to on-premise AD
  * Some limits not in place in other AD solutions

## AWS Managed Microsoft AD

* Managed Service, Microsoft AD in your AWS VPC
* EC2 Windows Instances can join domain
* Integrations:
  * RDS for SQL server, AWS Workspaces, amazon connect, workdocs, AWS SSO
  * AWS SSO for 3rd party apps, dropbox, github, etc
  * 2 way forest trusts with on-prem AD
* Multi AZ deployment of AD
* Automated Backups
* Connect to AD
  * Direct Connect or VPN
  * 3 kind of forest trust
    1. one way AWS -> On-Prem
    1. one way On-Prem -> AWS
    1. Two way forst trust AWS <-> On-Prem
    * Forest trust is different than synchronization (replication not supported)

### Solution Architecture

Need to minimize latency of AD on EC2 in the cloud, create a replica of AD on EC2 in case Direct Connect (DX) or VPN goes down.

* Establish trust between AD forests
* Need to deploy AD on EC2 and replica from on-prem -> EC2 AD
* 2 way forest trust between EC2 AD and AWS Managed Microsoft AD DC

## AD Connector

* Gateway to proxy AD request to on-prem AD
* Requires VPN or DX
* Doesn't support seamless joining, SQL Server, etc
* No caching capability, if DX or VPN is down, it is down

## Simple AD

* Supports joining of EC2, manages users/groups
* Limits 500 -> 5000 users
* Lower cost, low scale, no trust
* No MFA, RDS, AWS SSO support
