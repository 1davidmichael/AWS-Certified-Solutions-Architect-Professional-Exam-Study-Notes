# Beanstalk

## Supported Environments

* golang
* Java SE
* Java with Tomcat
* .NET on Windows Server with IIS
* Nodejs
* PHP
* Python
* Ruby
* Packer Builder
* Single Docker Container
* Multi-Docker Container
* Preconfigured Docker
* Custom Platforms Available

Great solution to replatform application to cloud

## Overview

* Managed Service
* Deployment strategies done by beanstalk
* 3 arch models
  * single instance
  * LB + ASG
  * Just ASG (worker env)

## Web Server vs Worker

* Offload long, cpu heavy tasks to worker env
* decouple into two tier app
* Example: video, generating a zip, etc
* Can define periodic tasks in a file cron.yaml