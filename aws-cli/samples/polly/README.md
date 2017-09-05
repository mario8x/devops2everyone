## Steps to do

* create dynamo db

`
create table name: posts
primary key: id
`


* create s3 bucket

`
create 1 s3 bucket: s3-polly-website
replace your api gateway into res
copy resources/bucketpolicypermissions.json into bucket policy

`


`
create 1 s3 bucket: s3-polly-audio-files
`

* messaging > simple notification service (SNS)

`
creat a sns topic : new_posts
display name: new posts
`

* iam role

`
create role name: LambdaPostReaderRole
assign policy: inline policy > custom policy
copy resources/lambdapolicy.json into custom policy

`


* lambda function

create new post

`
create a lamda function with author from scratch with name: PostReader_NewPost
copy resources/newposts.py with python 2.7
add envrionment:
DB_TABLE_NAME= posts ,
SNS_TOPIC = arn link:new_posts
assign an existing role: LambdaPostReaderRole
`

convert to audio file

`
create a lambda function from scratch with enable trigger from sns with name: PostReader_ConverToAudio
copy resources/convertoaudio.py with python 2.7
add environment
DB_TABLE_NAME= posts ,
BUCKET_NAME = s3-aws-polly-audio-files
assign an existing role: LambdaPostReaderRole
`

post reader get post

`
create a lamda function with author from scratch with name: PostReader_GetPosts
copy resources/getposts.py with python 2.7
add envrionment:
DB_TABLE_NAME= posts ,
SNS_TOPIC = arn link:new_posts
assign an existing role: LambdaPostReaderRole
`

* api gateway

`
Creat api gate way which integrated with lambda function: PostReader_NewPost
`

`
Creat api gate way which integrated with lambda function: PostReader_GetPosts
Add template for integration request:
{
    "postId": "$input.params('postId')"
}
`


## References
http://boto3.readthedocs.io/en/latest/