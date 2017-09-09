

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
aws lambda update-function-code --zip-flie=fileb://csv_parse.zip --function-name lab1
aws lambda upate-function-configuration --function-name lab1 --handler csv_sum.handler
```
