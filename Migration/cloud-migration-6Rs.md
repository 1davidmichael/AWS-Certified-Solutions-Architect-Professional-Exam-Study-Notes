# Cloud Migration the 6 Rs

* Rehost - lift and shift
  * Move from on-prem to AWS as is
  * No optimizations
  * AWS VM Import/Export or AWS Server Migration Service
* Replatforming
  * Example: Migrate database to RDS
  * Example: Migrate app to Elastic Beanstalk (Java with Tomcat)
  * Not changing core architecture, but some cloud optimizations leveraged
* Repurchase
  * Drop and Shop
  * Moving to another product while moving to the cloud
  * Expensive but faster to deploy
* Refactoring/Rearchiteting
  * Rebuild application using cloud native services
  * Driven by need of the business to scale, features, performance...
* Retire
  * Turn off things that are unneeded
* Retain
  * Keep what is there
  * Too complicated/expensive to move
