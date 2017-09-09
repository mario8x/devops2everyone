# Lambda handler

## js

* path to the function to run
* must accept 3 arguments
* event, context, and callback
* uses index.js by default
* ex:

```
export.handler = function(event, context, callback) {
  console.log('hi everyone');
  return callback(null, 'hello');
}
```

## memory & performance

* cpu scales with memory
* more memory, more $$$
* up to 1.5GB of Ram

## Logs

* automatically collected and stored
* searchable
* timedstamp automatically

## lambda function handler

* http://docs.aws.amazon.com/lambda/latest/dg/nodejs-prog-model-handler.html

## commands

* upload function code:
 fileb: binary file

`
aws lambda update-function-code --zip-flie=fileb://csv_parse.zip --function-name lab1
`

* update function source

`
aws lambda update-function-configuration --function-name lab1 --handler csv_read.handler
`
