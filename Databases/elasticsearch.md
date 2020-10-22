# ElasticSearch

* May be called Amazon ES
* Not a serverless offering

## ELK stack

* Elasticsearch provides search/index
* Kibana provides dashboards
* Logstash, log ingestion mechanism

## Patterns

* DynamoDB Table -> DynamoDB Stream -> Lambda Function -> Amazon ES
* Log analytics CLoudWatch Logs -> Subscription Filter -> Lambda (realtime)/Kinesis Data Firehose (near realtime) -> Amazon ES