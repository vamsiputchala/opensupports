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

DEVELOPMENT RDS CREATED




![RDS-DB-DEV-created](https://github.com/user-attachments/assets/0772500f-4171-417b-843f-039ea0e99bbd)


DEVELOPMENT S3 CREATED

![S3-BUCKET-DEV-created](https://github.com/user-attachments/assets/4427a990-20d0-4906-8da3-840fc9ba0a51)

DEVELOPMENT VPC CREATED

![VPC-DEV-crated](https://github.com/user-attachments/assets/ab98191a-d696-4420-913f-11bd692a0fce)



DEVELOPMENT CLOUD WATCH CREATED

![CLOWDWATCH-DEV-created](https://github.com/user-attachments/assets/c39bf451-6a23-486d-b390-8d34228cc6ff)

STAGING AND PRODUCTION ENVIRONMENTS ALSO CREATED


STAGING SUCCESS
![STAGING-CREATED-success](https://github.com/user-attachments/assets/136cb1f1-d570-41da-8497-a64787b2c215)



STAGING EC2
![EC2-STAGING-created](https://github.com/user-attachments/assets/d88c04d1-89f3-4c13-bf8d-f8c80f56f36a)


STAGING RDS
![RDS-STAGING-created](https://github.com/user-attachments/assets/397c623d-60ec-4756-94fe-37d69fc93582)



STAGING S3

![S3-STAGING-created](https://github.com/user-attachments/assets/105acd5e-3e44-46b3-805a-ba18a1eb72cf)

SATGING VPC
![VPC-STAGING-created](https://github.com/user-attachments/assets/07e94a46-d1dc-41aa-bd29-1bfb9d879b9d)


STAGING CLOUD WATCH

![CLOUDWATCH-STAGING](https://github.com/user-attachments/assets/10dcb227-b45e-46c0-a78e-e6ab7f41bb14)


PRODUCTION SUCCESS
![PROD-CREATED-success](https://github.com/user-attachments/assets/2a2db393-f8a9-4d7e-81bf-12d5712330bd)


PRODUCTION EC2

![EC2-PROD-created](https://github.com/user-attachments/assets/b44d042c-a985-4d68-ab4d-a7246fd77cbf)

PRODUCTION RDS
![RDS-PROD-created](https://github.com/user-attachments/assets/e70dcd73-4728-4918-8fd7-7883bf1db552)


PRODUCTION S3
![S3-PROD-created](https://github.com/user-attachments/assets/f372f467-b705-49ca-a738-0ea99eb78d4d)


PRODUCTION VPC

![VPC-PROD-created](https://github.com/user-attachments/assets/6254287e-d705-40fa-bf32-ee979ba44a6f)

PRODUCTION CLOUD WATCH
![CLOUDWATCH-PROD](https://github.com/user-attachments/assets/124e3075-7121-43c9-98ff-efacbe13fcb0)




 Create the GitHub Actions Workflow
Now, create a GitHub Actions workflow in repository to automate the deployment.

Steps:
In your repository, go to .github/workflows/.
Create a new file called deploy.yml in that directory.





