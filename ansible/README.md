## Ansible

### To set up ssh connection on remote host

* to generate and add ssh keygen:

https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/

* configure ssh then ssh-copy-id (follow the link below):

https://www.digitalocean.com/community/tutorials/how-to-use-ssh-to-connect-to-a-remote-server-in-ubuntu

* install python on remote host: `apt-get install python`

* to change aws root password:

https://aws.amazon.com/premiumsupport/knowledge-center/set-change-root-linux/

to change password:

`passwd username`

* To use Putty to connect to ec2 instance
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html

### To install ansible

https://docs.ansible.com/ansible/intro_getting_started.html

* to install python into linux:

`apt-get install python-minimal --no-install-recommends`

* to install pip:

- sudo apt install python-pip

personal package archived: ppa
https://launchpad.net/~ansible/+archive/ubuntu/ansible

[python OpenSSH protocol](https://docs.ansible.com/ansible/intro_getting_started.html):

- On these operating systems, Ansible will fallback into using a high-quality Python implementation of OpenSSH called ‘paramiko’.



### To setup environments


[to enable ssh in ubuntu](http://ubuntuhandbook.org/index.php/2016/04/enable-ssh-ubuntu-16-04-lts/)
`sudo apt-get install openssh-server`
`sudo service ssh status`
`sudo service ssh restart`

[to enable x11 in ubuntu](https://askubuntu.com/questions/73059/how-to-copy-paste-from-ubuntu-virtualbox-guest-to-windows-host)
to install git:
`sudo apt-get install git-core`

to create an ssh login:

to login with root account
`sudo -i`

to install [lxc](https://linuxcontainers.org/) (linux container which work the same as virtual box)
`apt-get update && apt-get install lxc`

to create an linux container:

`sudo lxc-create -t ubuntu -n db1`

to start an lxc:(-n: name)

`lxc-start -n db1 -d`

to login to an lxc:

`lxc-attach -n db1`
>> `root@dbl#`

to exit an lxc:
`exit`


### ansibile
configuration file:
`./etc/ansible/ansible.cfg`

host file:
`./etc/ansible/hosts`

to setup the custom hosts file:
`ansible-playbook -i <custom-hosts-file>`


ansible commands:

- `ansbile <group/machine> -m <module> -a <args> (-k for ask pass)`
- ex : `ansible 10.0.3.17 -m ping -u root`
- ex - install nginx module : `ansible web -a "apt-get -y install nginx" -i hosts -u root`
- start nginx: `ansible web -m service -a "name=nginx state=restarted" -i hosts -u root`

ansible playbook:

ansible modules:

- https://docs.ansible.com/ansible/list_of_all_modules.html
- lxc container: https://docs.ansible.com/ansible/lxc_container_module.html

ansible variables and facts:
* referenced by : {{varnames}} syntax
* there are 3 ansible variables scope: global, play, host
* facts: information about hosts in your inventory that's gathered by Ansible when it connects to a host.
    * `ansible host -m setup -u root`
ansible galaxy:

- https://galaxy.ansible.com/intro

ansible tower:

- https://www.ansible.com/tower


### ansible with aws
http://docs.ansible.com/ansible/guide_aws.html
https://aws.amazon.com/blogs/apn/getting-started-with-ansible-and-dynamic-amazon-ec2-inventory-management/

### Demo

#### Demo to setup on aws

* aws: to connect via ssh
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html?icmpid=docs_ec2_console

* yaml

* python

### AWS terminologies
* IAM roles: http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html

* Alarm: to make condition to send alarm methods
https://ap-southeast-1.console.aws.amazon.com/cloudwatch/home?region=ap-southeast-1#alarm:alarmFilter=ANY;name=awsec2-i-0d5791ba038769431-CPU-Utilization

### vim
* to force quit: q!
