## manual
http://docs.aws.amazon.com/cli/latest/reference/ec2/index.html

## describe

* to display all of ec2 instances

`
aws ec2 describe-instances
`
* to display images

`
aws ec2 describe-imagess
`

* terminate an instance

`
aws ec2 terminate-instances --instance-ids i-010d1a11b9b3b54a9
`


* run a new instance

`
aws ec2 run-instances --image-id ....
`

### Warnings
* do not confuse `start-instances` with `run-instances` (create new instances)