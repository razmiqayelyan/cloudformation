# AWS VPC Infrastructure with Bastion Host

This repository contains an AWS CloudFormation template to create a fully functional and secure VPC infrastructure. The infrastructure includes public and private subnets, NAT Gateways, Internet Gateway, and a Bastion Host for secure SSH access to private instances.

## Features

- **VPC Setup**: Creates a VPC with a CIDR block of `10.0.0.0/16`.
- **Subnets**:
  - Two public subnets for NAT Gateways and Bastion Host.
  - Two private subnets for secure workloads.
- **Routing**:
  - Internet Gateway for public subnets.
  - NAT Gateways for private subnet outbound internet access.
  - Separate route tables for each private subnet.
- **Bastion Host**:
  - Ubuntu Server 24.04 LTS.
  - T2.micro instance (Free Tier eligible).
  - Secure SSH access via a Security Group.
- **Highly Available**:
  - Resources are spread across two availability zones for redundancy.

## Getting Started

### Prerequisites
1. **AWS Account**: Ensure you have an active AWS account.
2. **AWS CLI**: Install and configure the AWS CLI with access to your AWS account.
3. **Key Pair**: Create an SSH Key Pair in the target region and download the `.pem` file.

### Deploying the Stack
To deploy the CloudFormation stack, use the AWS Management Console or the AWS CLI.

#### Using AWS CLI
```bash
aws cloudformation deploy \
  --template-file template.yaml \
  --stack-name MyVPCStack \
  --capabilities CAPABILITY_NAMED_IAM
