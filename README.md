# AWS-EC2-INSTANCE
My first cloud project as I start my cloud career path

# AWS Cloud Networking Project

Project Overview

This project demonstrates the design and implementation of a secure AWS network infrastructure using a custom Virtual Private Cloud (VPC). The environment consists of public and private subnets, routing components, network security controls, and EC2 instances deployed across the network.

The objective was to provide secure internet connectivity to public resources while keeping backend resources isolated from direct internet access.


## Network Architecture

Components created:

- Custom VPC
- Public Subnet
- Private Subnet
- Internet Gateway
- NAT Gateway
- Elastic IP
- Public Route Table
- Private Route Table
- Public Network ACL
- Private Network ACL
- Bastion Host EC2 Instance
- Private EC2 Instance


## Subnet Configuration

### Public Subnet

- Name: DM-Public-Subnet
- Purpose: Hosts internet-facing resources
- Resources:
  - DM-Bastion
  - NAT Gateway

### Private Subnet

- Name: DM-Private-Subnet
- Purpose: Hosts internal resources
- Resources:
  - DM-Private-Server

## Internet Gateway

Internet Gateway (DM-IGW) was attached to the VPC to provide communication between AWS resources and the public internet.


## NAT Gateway

A NAT Gateway was deployed within the Public Subnet and assigned an Elastic IP address.

Purpose:

- Allow outbound internet access from the Private Subnet
- Prevent direct inbound internet access to private resources

## Route Tables

### Public Route Table

Routes:

- Local VPC Route
- 0.0.0.0/0 → Internet Gateway

Associated Subnet:

- DM-Public-Subnet

### Private Route Table

Routes:

- Local VPC Route
- 0.0.0.0/0 → NAT Gateway

Associated Subnet:

- DM-Private-Subnet


## Security Groups

### Bastion Host Security Group

Allowed:

- SSH (Port 22)

### Private Server Security Group

Allowed:

- SSH access from Bastion Host


## Network ACLs

Custom Network ACLs were created and associated with the corresponding subnets.

Allowed traffic:

- HTTP (80)
- HTTPS (443)
- SSH (22)
- Ephemeral Ports (1024–65535)

## EC2 Instances

### DM-Bastion

- Deployed in Public Subnet
- Assigned Public IP

### DM-Private-Server

- Deployed in Private Subnet
- No Public IP assigned


## Security Design

The architecture follows security best practices by:

- Separating resources into public and private subnets
- Using route tables for controlled traffic flow
- Using NAT Gateway for outbound access
- Restricting administrative access through a Bastion Host
- Applying subnet-level filtering with NACLs

## Conclusion

The project successfully implemented a secure cloud networking environment using AWS services. The architecture provides controlled internet access, network segmentation, and protection of private resources while maintaining operational functionality.
