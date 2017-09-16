

# lab 1

## lambda and S3

### steps

* aws cli instruction
* create function
* deploy version 1
* testing and debugging
* deploy version 2
* output and timeouts

### s3 bucket

* create an s3 to store .csv file

`
aws s3 mb s3://lab1-csv-storage
`

* upload `lab1\sample.csv` file

`
aws s3 cp sample.csv s3://lab1-csv-storage
`

* upload .zip source and assign source.js to lambda function

```
aws lambda update-function-code --zip-file=fileb://csv_parse.zip --function-name lab1
aws lambda update-function-configuration --function-name lab1 --handler csv_sum.handler
```

# lab 2: lambda and Kinesis

* read input from Kinesis
* track net profit
* log output to cloudwatch

* upload lambda kinesis function :
```
aws lambda update-function-code --zip-file=fileb://kinesis_sums.zip --function-name lab2-kinesis
aws lambda update-function-configuration --function-name lab2-kinesis --handler index.handler
```

* upload data to kinesis for testing:

```
aws kinesis put-records --stream-name lambda-kinesis --records file://sample_records.json
```
