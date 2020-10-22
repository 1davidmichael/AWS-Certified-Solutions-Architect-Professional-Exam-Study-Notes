# Cloud HSM (Hardware Security Module)

* KMS -> AWS managed encryption keys
* CloudHSM -> dedicated encryption hardware
* You manage your own encryption keys
* Supports symmetric and asymmetric encryption
* No free tier
* Redshift supports CloudHSM for database encryption and key management
* Good to use SSE-C
* AWS managed hardware
* IAM CRUD to create HSM Cluster
* Clusters are multi-AZ, good for HA/durability
