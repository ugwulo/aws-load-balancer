[live load balanced url](http://ugwulo.me/)

<h1><p align="center">
Background
</p></h1>
You are required to perform the following tasks

Set up 2 EC2 instances on AWS(use the free tier instances).
Deploy an Nginx web server on these instances(you are free to use Ansible)
Set up an ALB(Application Load balancer) to route requests to your EC2 instances
Make sure that each server displays its own Hostname or IP address. You can use any programming language of your choice to display this.

Important points to note:

Your web servers should not be accessed through their respective IP addresses. Access must be only via the load balancer
You should define a logical network on the cloud for your servers.
Your EC2 instances must be launched in a private network.
Your Instances should not be assigned public IP addresses.
You may or may not set up auto scaling(I advice you do for knowledge sake)
You must submit a custom domain name(from a domain provider e.g. Route53) or the ALB’s domain name.

<h1><p align="center">
Design Infrastructure
</p></h1>

NB: I used Ansible to automate the whole process and then used bash script to setup my Nginx server from aws userdata config file
## Create VPC
Name: altschool-vpc
IPv4 CIDR Block: 10.0.0.0/16

![Altchool VPC](screenshots/vpc-dashboard.png)

## Create Subnets
Name: Public-1A
Availability Zone: us-east-1a
IPv4 CIDR Block: 10.0.1.0/24

Name: Public-1B
Availability Zone: us-east-1b
IPv4 CIDR Block: 10.0.2.0/24

Name: Private-1A
Availability Zone: us-east-1a
IPv4 CIDR Block: 10.0.3.0/24

Name: Private-1B
Availability Zone: us-east-1b
IPv4 CIDR Block: 10.0.4.0/24

![Subnets](screenshots/subnet-dashboard.png)

## Create private route table
Name: Private-RT
VPC: altschool-vpc
Subnet associations: Private-1A, Private-1B
![Altchool route Table](screenshots/route-tables.png)

## Create Internet Gateway
Name: altschool-igw
VPC: altschool-vpc

## Create NAT Gateway
Name: altschool-NAT
connect the private route to the NAT gateway

## create a security group
Name: Public-Web
Description: Public Web Access 
[attach to VPC]

## Create the 2 private instances
## Create Target group
## Setup Autoscaling

## Run the playbook
![Playbook](screenshots/successful-plays1.png)
![Playbook](screenshots/successful-plays2.png)

## Private ec2 Instances
![Server1](screenshots/server1-dashboard.png)
![Server2](screenshots/server2-dashboard.png)

## Load Balancer Dashboard
![Server2](screenshots/loadbalancer-dashboard.png)
