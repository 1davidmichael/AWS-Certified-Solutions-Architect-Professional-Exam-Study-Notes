# Kinesis

* managed data streaming sevice
* great for application logs, metrics, IoT and clickstreams
* real-time big data
* Spark, NiFi
* Automatically replicated to 3 az

## Types

* Kinesis Streams - low latency streaming ingest at scale
* Kinesis Analytics - perform real-time analytics on streams using SQL
* Kinesis Firehose - loads streams into S3, Redshift, ElasticSearch & Splunk

## Kinesis Streams

* Used to ingest data
* Analyzed by Kinesis Analytics
* Kinesis Firehose then used to ingest data to S3, Redshift, etc...

* Streams are divided into shards/partitions
* Data retention per shard is 24 hours by default, up to 7 days
* Ability to reprocess/replay data
* Multiple applications can consume same stream
* Once data is inserted it can't be deleted (immutable)

* One stream is made of many shards
* Billing is per shard provisioned
* Can create/remove shards reshard/merge
* Records are ordered per shard

### Producers

* AWS SDK - simple producer
* Kinesis Producer Library (KPL) - provides batch, compression, retries, C++, java
* Kinesis Agent
  * Monitor log files and sets them to Kinesis directly
  * Can write to Kinesis Data Stream **AND** Kinesis Data Firehose

### Consumers

* AWSK SDK - simple consumer
* Lambda - event source mapping
* KCL (Kinesis Client Library) - checkpointing, coordinated reads
  * Records progress checkpoints in DynamoDB

### Limits to know

* Producer
  * 1 MB/s or 1000 messages at write PER SHARD
* Consumer Classic
  * 2 MB/s at read PER SHARD across all consumers
  * 5 API calls per second PER SHARD across all consumers
* Consumer Enhanced Fan-Out
  * 2 MB/s at read PER SHARD, PER ENHANCED CONSUMER
  * No API calls needed (push model)
* Data Retention
  * 24 hours by default, max 7 days

## Kinesis Data Firehose

* Fully managed service, autoscaling, serverless
* Near real-time (60 second latency minumum for non full batches)
* Load data into Redshift, S3, ElasticSearch, Splunk
* Supports data formats, conversions, transformations, compression

## Consumers

* SDK
* KPL
* Kinesis data streams
* CloudWatch Logs
* IoT Rules Actions

* Can then be transformed by Lambda

### Destinations

The following destinations ARE THE ONLY ONE SUPPORTED

1. S3
1. Redshift
1. ElasticSearch
1. Splunk

###  Delivery

* Source -> Firehose -> Transformations by Lambda -> Destination (S3)
* Can output source records, transform failures and deliver failures to S3

### Firehose Buffer Sizing

* Firehose accumulates data records into a buffer
* Buffer is flushed based on time and size rules
  * Buffer size, example 32 MB
  * Buffer time, example 1 minute
  * Data is flushed when one of these limits are hit
  * Can automatically increase buffer size to increase throughput

* If real-time flush from Kinesis Data Streams to S3 is needed, use Lambda

## Kinesis Data Streams vs Firehose

* Streams
  * Write custom code for producer/consumer
  * Or use Agents
  * Real-time, 200 ms or 70ms for enhanced
  * Must manage shards for scaling
  * 1 -> 7 day retention
  * Insert data into ElasticSearch requires Lambda
* Firehose
  * Fully managed, no need to manage scaling, sends to S3, Redshift, ElasticSearch, Splunk
  * Serverless data transforms with Lambda
  * Near real-time, lowest buffer time is 1 minute
  * No data storage, once data is flushed it is gone

## Analytics

* Use Data Analytics to work with Streams or Firehose for input streams
* Use reference table in S3
* Create query using stream and reference table
* Create output stream results of the query
  * Output stream
  * Error stream

### Use Cases

* Streaming ETL
* Continous Metric Generation
* Responsive Analytics

Features

* Pay for resource use only, but is expensive
* Serverless
* SQL or Flink