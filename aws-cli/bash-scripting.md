# create ec2 + advanced details:
yum update -y
yum install httpd -y
service httpd start
chkconfig httpd on
aws s3 cp --recursive s3://acloudguru-useast1 /home/ec2-user