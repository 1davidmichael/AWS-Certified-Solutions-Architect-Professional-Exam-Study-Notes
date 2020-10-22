# DynamoDB

* NoSQL database
* Similar to Cassandra
* Max object size is 400KB, store larger objects in S3 with ref to it in DynamoDB
* Capacity, provisioned or on-demand

## Basics

* Made of tables with primary keys
* Each table has infinite number of rows
* Each item has attributes

## Primary Keys

* Option 1, partition key only (HASH)
  * partition key mus tbe unique
* Option 2, Partition key + sort key
  * Combination must be unique
  * Grouped logically by partition key
  * example user_id + timestamp

## Indexes

* LSI - Local Secondary Index
  * Keep same primary key
  * Select an alternative sort key
  * Must be defined at table creation time
* GSI - Global Secondary Index
  * Change the primary and optional sort key
  * Can be defined after table creation

Need an index if you want to query a specific attribute in DynamoDB

## Important Features

* TTL - automatically expire row after specified epoch date
* DynamoDB streams - react to tables changes in real time
  * Can be read by Lambda, EC2
  * 24 hour retention of data
* Global tables - replicated across regions, can have many regions. Requires DynamoDB streams
  * Good for low latency or disaster recovery purposes

## Solution

* Index objects in S3 with DynamoDB

## Caching

* DAX
* Seamless cache for DynamoDB
* Micro-second latency for cached reads/queries
* Can help with hotspotting
* 5 minute TTL for cache by default
* Up to 10 nodes
* Multi-AZ

### DAX vs Elasticache

* If client directly access DynamoDB use DAX
* If client does computed results store output in Elasticache