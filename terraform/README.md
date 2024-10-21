Project Overview



This repository contains AWS infrastructure and CI/CD pipeline setup for deploying the OpenSupports application using Terraform. The infrastructure spans across three environments: development, staging, and production, with automation to promote the application between these environments.

Prerequisites



AWS account and access configured credentials.
Terraform CLI.
AWS CLI.
GitHub repository forked from OpenSupports.
CI/CD tool GitHub Actions configured for automation.

Architecture Overview
The infrastructure consists of the following AWS components:

EC2 Instances
RDS (MySQL)
S3 Buckets
VPC, Subnets, and Security Groups: Provides network isolation and security.
IAM Roles and Policies: Ensures least-privilege access for the resources.
CloudWatch: Logs and monitors the application.
SNS


PARAMETERIZED ENVIRONMENTS 
![parameterized](https://github.com/user-attachments/assets/9c21a501-c5b8-462c-b831-7288f9a9ea34)

First, fork the OpenSupports repository 

 Infrastructure Setup (Using Terraform)
Initialize Terraform
If using Terraform for infrastructure setup, ensure Terraform is initialized with your AWS provider





DEVELOPMENT ENVIRONMENT success
![development-success1](https://github.com/user-attachments/assets/3bceaca6-3da4-4678-938a-a8f9c9eba543)


DEVELOPMENT EC2 CREATED

![Ec2-instance-dev-created](https://github.com/user-attachments/assets/e98745c6-b567-429e-a9ad-c874e59e6216)




