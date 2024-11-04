## Project Overview



This repository contains AWS infrastructure and CI/CD pipeline setup for deploying the OpenSupports application using Terraform. The infrastructure spans across three environments: development, staging, and production, with automation to promote the application between these environments.

## Prerequisites



AWS account and access configured credentials.

Terraform CLI.

AWS CLI.

GitHub repository forked from OpenSupports.

CI/CD tool GitHub Actions configured for automation.


## Architecture Overview
The infrastructure consists of the following AWS components:

EC2 Instances

RDS (MySQL)

S3 Buckets

VPC, Subnets, and Security Groups: Provides network isolation and security.

IAM Roles and Policies: Ensures least-privilege access for the resources.

CloudWatch: Logs and monitors the application.

SNS


## PARAMETERIZED ENVIRONMENTS 
![parameterized](https://github.com/user-attachments/assets/9c21a501-c5b8-462c-b831-7288f9a9ea34)

First, fork the OpenSupports repository 

 Infrastructure Setup (Using Terraform)
 
Initialize Terraform  terraform init after that based on required environment need to enter into environment folder and pass the command terraform apply -var-file="terraform.tfvars"

If using Terraform for infrastructure setup, ensure Terraform is initialized with your AWS provider





## DEVELOPMENT ENVIRONMENT success
![development-success1](https://github.com/user-attachments/assets/3bceaca6-3da4-4678-938a-a8f9c9eba543)


## DEVELOPMENT EC2 CREATED

![Ec2-instance-dev-created](https://github.com/user-attachments/assets/e98745c6-b567-429e-a9ad-c874e59e6216)

## DEVELOPMENT RDS CREATED




![RDS-DB-DEV-created](https://github.com/user-attachments/assets/0772500f-4171-417b-843f-039ea0e99bbd)


## DEVELOPMENT S3 CREATED

![S3-BUCKET-DEV-created](https://github.com/user-attachments/assets/4427a990-20d0-4906-8da3-840fc9ba0a51)

## DEVELOPMENT VPC CREATED

![VPC-DEV-crated](https://github.com/user-attachments/assets/ab98191a-d696-4420-913f-11bd692a0fce)



## DEVELOPMENT CLOUD WATCH CREATED

![CLOWDWATCH-DEV-created](https://github.com/user-attachments/assets/c39bf451-6a23-486d-b390-8d34228cc6ff)

STAGING AND PRODUCTION ENVIRONMENTS ALSO CREATED


## STAGING SUCCESS
![STAGING-CREATED-success](https://github.com/user-attachments/assets/136cb1f1-d570-41da-8497-a64787b2c215)



## STAGING EC2
![EC2-STAGING-created](https://github.com/user-attachments/assets/d88c04d1-89f3-4c13-bf8d-f8c80f56f36a)


## STAGING RDS
![RDS-STAGING-created](https://github.com/user-attachments/assets/397c623d-60ec-4756-94fe-37d69fc93582)



## STAGING S3

![S3-STAGING-created](https://github.com/user-attachments/assets/105acd5e-3e44-46b3-805a-ba18a1eb72cf)

SATGING VPC
![VPC-STAGING-created](https://github.com/user-attachments/assets/07e94a46-d1dc-41aa-bd29-1bfb9d879b9d)


## STAGING CLOUD WATCH

![CLOUDWATCH-STAGING](https://github.com/user-attachments/assets/10dcb227-b45e-46c0-a78e-e6ab7f41bb14)


## PRODUCTION SUCCESS
![PROD-CREATED-success](https://github.com/user-attachments/assets/2a2db393-f8a9-4d7e-81bf-12d5712330bd)


## PRODUCTION EC2

![EC2-PROD-created](https://github.com/user-attachments/assets/b44d042c-a985-4d68-ab4d-a7246fd77cbf)

## PRODUCTION RDS
![RDS-PROD-created](https://github.com/user-attachments/assets/e70dcd73-4728-4918-8fd7-7883bf1db552)


## PRODUCTION S3
![S3-PROD-created](https://github.com/user-attachments/assets/f372f467-b705-49ca-a738-0ea99eb78d4d)


## PRODUCTION VPC

![VPC-PROD-created](https://github.com/user-attachments/assets/6254287e-d705-40fa-bf32-ee979ba44a6f)

## PRODUCTION CLOUD WATCH
![CLOUDWATCH-PROD](https://github.com/user-attachments/assets/124e3075-7121-43c9-98ff-efacbe13fcb0)


## RECIEVED SNS NOTIFICATIONS TO EMAIL



![SNS](https://github.com/user-attachments/assets/1919607c-9b29-4f95-acd4-63aa23dd2e1f)




##  Create the GitHub Actions Workflow
    Now, create a GitHub Actions workflow in repository to automate the deployment.

## Steps:
In github repository, go to .github/workflows/.

Create a new file called deploy.yml in that directory.





![deploy yml](https://github.com/user-attachments/assets/003452af-7b37-43bf-a4e7-07a2e6bf072e)





## Explanation of the Workflow:

GitHub Events: The pipeline triggers when changes are pushed to main, staging, or development branches.

Global Environment Variables: AWS credentials are securely accessed using ${{ secrets.AWS_ACCESS_KEY_ID }} and ${{ secrets.AWS_SECRET_ACCESS_KEY }}.

Dynamic Environment: The TF_VAR_environment variable is dynamically set based on the branch (main, staging, or development).

## Steps:
Checkout the repository to access the latest code.

Set up Terraform using hashicorp/setup-terraform@v1.

Initialize Terraform with terraform init.

Terraform Plan checks the changes that will be applied.

Terraform Apply applies the changes automatically.







## Pipeline Flow
On any push to the main branch:

The application will first be deployed to the development environment.

After successful deployment, the pipeline automatically promotes the application to the staging environment.

Once staging is verified, the pipeline promotes the application to production.

This pipeline sets up an automated workflow for deploying OpenSupports to AWS across multiple environments, ensuring smooth transitions between dev, staging, and production. Let me know if you need more help with setting up specific steps.








## Best Practices for Security and Cost Optimization
Security:

Sensitive Data Management:


Store sensitive information such as RDS database credentials, API keys, and access tokens securely using AWS Secrets Manager or AWS Systems Manager Parameter Store.

Ensure that these secrets are accessed only by necessary resources (e.g., EC2 instances) and are encrypted using AWS KMS (Key Management Service).

IAM Roles and Policies:


Follow the principle of least privilege by creating restrictive IAM policies that only allow resources to access what is required for their specific functionality. Avoid using overly permissive policies (e.g., AdministratorAccess).

Use IAM Roles to provide EC2 instances with temporary credentials to access other AWS services like S3 and RDS, instead of embedding long-term access keys in code.


Data Encryption:

Enable encryption at rest for both EC2 and RDS resources. For RDS, ensure the database storage is encrypted using AWS-managed keys in KMS. Similarly, encrypt EBS volumes attached to EC2 instances.

Use encryption in transit (SSL/TLS) for all connections between EC2 instances and the RDS database, and when accessing S3.

Network Security:

Utilize security groups to control inbound and outbound traffic for EC2 instances, allowing only the necessary ports and IP ranges (e.g., restrict SSH access to your IP and allow only required ports like HTTP/HTTPS).

Consider setting up VPC Peering or AWS Transit Gateway to securely interconnect environments, and use NAT Gateways for internet access in private subnets.

Enable VPC Flow Logs to monitor network traffic for suspicious activity.

