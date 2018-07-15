# Deploy an EC2 Instance with Nginx and display EC2 Instance ID

## Setup required for Ubuntu Linux Machine:

sudo yum install python
sudo yum update
sudo yum install python-pip
sudo pip install --upgrade pip
sudo pip install boto
sudo pip install botocore
sudo pip install boto3

## Install ansible >=2.4 on ubuntu host

sudo apt-get update
sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible

## CentOS

sudo subscription-manager repos --enable rhel-7-server-ansible-2.6-rpms

# Setup access AWS with Access keys:

## You will need to run this from the host that is running ansible:

export AWS_ACCESS_KEY_ID="NUHKOIJFOJF9GFJDO"
export AWS_SECRET_ACCESS_KEY="LSDJKFODSJF9SDJF8UH3U3HFKW"

## Configure ansible.cfg

You will need to set the remote user name and the location for the private key

[defaults]
private_key_file=~/testingkey.pem
remote_user = ubuntu

## Configure Host File in home director ~/hosts

[local]
localhost

[webserver]

# To deploy an EC2 Instance:

`ansible-playbook -i ./hosts create-ec2.yml nginx.yml`

When a connection is made to the new host you will be prompted for authenticity; type 'yes'

## To allow single input the follow can be applied(although not recommended):

https://stackoverflow.com/questions/32297456/how-to-ignore-ansible-ssh-authenticity-checking
