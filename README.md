# Deploy an EC2 Instance with Nginx and display EC2 Instance ID

### To deploy an EC2 (Ubuntu) Instance:

1.  [Clone repository](https://github.com/scottgbailey/create-ec2)
1.  Change to cloned repository directory
1.  Set prerequisites: Install python, pip, boto, botocore, boto3, ansible >=2.4 configure AWS Access keys, ansible.cfg (match user name with AMI chosen)
1.  `ansible-playbook -i ./hosts create-ec2.yml nginx.yml`

When a connection is made to the new host you will be prompted for authenticity; type 'yes'

## Setup required for Ubuntu/Localhost Linux Machine:

1.  sudo yum install python
1.  sudo yum update
1.  sudo yum install python-pip
1.  sudo pip install --upgrade pip
1.  sudo pip install boto
1.  sudo pip install botocore
1.  sudo pip install boto3

## Install ansible >=2.4 on Ubuntu/Localhost:

1.  sudo apt-get update
1.  sudo apt-get install software-properties-common
1.  sudo apt-add-repository ppa:ansible/ansible
1.  sudo apt-get update
1.  sudo apt-get install ansible

## CentOS:

1.  sudo subscription-manager repos --enable rhel-7-server-ansible-2.6-rpms

# Setup access AWS with Access keys:

## You will need to run this from the host that is running ansible:

```
export AWS_ACCESS_KEY_ID="NUHKOIJFOJF9GFJDO"
export AWS_SECRET_ACCESS_KEY="LSDJKFODSJF9SDJF8UH3U3HFKW"
```

## Configure ansible.cfg

You will need to set the remote user name and the location for the private key

```bash
[defaults]
private_key_file=~/testingkey.pem
remote_user = ubuntu
```

## Configure Host File in home directory ~/hosts:

```bash
[local]
localhost

[webserver]
```

## To allow single input the following can be applied(although not recommended):

https://stackoverflow.com/questions/32297456/how-to-ignore-ansible-ssh-authenticity-checking
