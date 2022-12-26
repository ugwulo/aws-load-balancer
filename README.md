# Altschool Christmas Challenge

Design infrastructure ->
# Create VPC
Name: johnpaul-vpc
IPv4 CIDR Block: 10.0.0.0/16

# Create Subnets

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

# Create private route table

Name: Private-RT
VPC: johnpaul-vpc
Subnet associations: Private-1A, Private-1B

# Create Internet Gateway

Name: johnpaul-IGW
VPC: johnpaul-vpc

#Create NAT Gateway

Name: johnpaul-NAT
#connect the private route to the NAT gateway

#create a security group
Name: Public-Web
Description: Public Web Access 
[attach to VPC]

inbound/outbound rules [all traffic to all destination]
