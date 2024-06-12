# Terraform-AWS

**Overview**

This project uses Terraform to provision and manage an AWS infrastructure, including VPC, subnets, internet gateway, route tables, security groups, EC2 instances, S3 bucket, and an Application Load Balancer (ALB). The setup is designed to deploy a web application with high availability across multiple availability zones.

**Prerequisites**

Before you begin, ensure you have the following:

- An AWS account with necessary permissions.
    
- Terraform installed on your local machine.
    
- AWS CLI installed and configured with your credentials.

**Project Structure**
~~~
css
├── main.tf
├── provider.tf
├── userdata1.sh
├── userdata2.sh
├── variables.tf
└── outputs.tf
~~~

**`main.tf`** 

Defines the resources for the VPC, subnets, internet gateway, route tables, security groups, EC2 instances, S3 bucket, and ALB with its target groups and listeners.

**`provider.tf`**

Specifies the required provider and the AWS region to be used.

**`userdata1.sh`** **`and`** **`userdata2.sh`**
Bootstrap scripts for the EC2 instances, installing necessary packages, and configuring the web server.

**`variables.tf`**
Defines the input variables used in the project.

**`outputs.tf`**
Defines the outputs, such as the DNS name of the load balancer.

**Usage**

Step 1: Initialize Terraform
Initialize the Terraform working directory.
~~~
terraform init
~~~
Step 2: Plan the Deployment
Generate and review the execution plan.
~~~
terraform plan
~~~
Step 3: Apply the Configuration
Apply the configuration to create the resources.
~~~
terraform apply
~~~
Step 4: Access the Application
After the resources are created, you can access your application using the DNS name of the load balancer provided in the output.

Step 5: Clean Up
To destroy the infrastructure when you no longer need it.

~~~
terraform destroy
~~~
### Components

**VPC and Subnets**

 - A VPC with a customizable CIDR block.
 - ATwo public subnets in different availability zones.
 
**Internet Gateway and Route Tables**

 - An internet gateway for VPC.
 - Route tables to direct traffic to the internet gateway.
 
**Security Group**

 - A security group allowing HTTP and SSH access.
 
**EC2 Instances**

 - Two EC2 instances in different subnets, running a web server with a simple HTML page.
 
**S3 Bucket**

 - An S3 bucket for storing project-related files.
 
**Application Load Balancer**

 - An ALB to distribute traffic across the EC2 instances.
 
 - Target groups and listeners configured for HTTP traffic.
 
### **Configuration Details**

**Variable Configuration**

The following variables can be customized in variables.tf:

 - cidr: The CIDR block for the VPC (default: 10.0.0.0/16).
 
**User Data Scripts**

 - userdata1.sh and userdata2.sh: Scripts to configure the web server on each EC2 instance.
 
**Outputs**

 - loadbalancerdns: The DNS name of the load balancer.
 
**Notes**

 - Ensure your AWS credentials are properly configured.
 - Modify variables.tf to customize the VPC CIDR block or other settings as needed.
 - Review security group settings to ensure they meet your security requirements.
 
**Conclusion**

This Terraform project sets up a scalable and highly available web application infrastructure on AWS. By following the steps and understanding the components, you can adapt and extend the configuration to fit your specific needs. 
