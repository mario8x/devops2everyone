# Kinesis

is a streaming data server

* logs are ordered stream
* Event get batches or records
* Fast writes: up to 1Mb/secs or 1000 TPs( transaction per seconds)
* Easy reply data of 24hrs only
* Shard
* a kinesis stream  = group of shard

## commands

* end to end test with kinesis
- upload an kinesis stream

```
aws kinesis put-records --stream-name lambda-kinesis --records file://sample_records.json
```
