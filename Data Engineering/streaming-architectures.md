# Streaming Architecture

## Cost

**Kinesis**
* 1MB/s per shard in Kinesis Data Streams
* 3 * $0.0.15/hr = $32.4/month
* Must use KDF for output to S3

**DynamoDB + Streams**
* 3000 WCU = 3MB/s = $1500/month
* Storage in DynamoDB