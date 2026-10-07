Secure AWS Infrastructure on AWS

A secure and scalable AWS infrastructure project designed to demonstrate practical knowledge of AWS networking, IAM, EC2, S3, monitoring, logging, and cloud security best practices.

📌 Project Overview

This project implements a secure AWS cloud environment using multiple AWS services.

The infrastructure includes:

Amazon VPC
Public and Private Subnets
Internet Gateway
Route Tables
Amazon EC2
Security Groups
Amazon S3
AWS IAM
AWS CloudTrail
Amazon CloudWatch

The main objective is to build an AWS environment that provides secure network connectivity, controlled access, data protection, and monitoring.


☁️ AWS Services Used
Service	Purpose
Amazon VPC	 	Creates the isolated cloud network
Subnets	       	 	Separates public and private resources
Internet Gateway	Provides internet connectivity to public resources
Route Tables		Controls network traffic flow
Amazon EC2		Hosts the cloud compute workload
Security Groups		Controls inbound and outbound traffic
Amazon S3		Provides secure object storage
AWS IAM			Manages identities and permissions
AWS CloudTrail		Records AWS API activity
Amazon CloudWatch	Provides monitoring and metrics

🌐 Network Design
VPC

The project uses a dedicated VPC:  10.0.0.0/16

This provides a private network space for the AWS resources.

Public Subnet
CIDR: 10.0.1.0/24

The public subnet contains the EC2 instance and uses an Internet Gateway for internet connectivity.

Private Subnet
CIDR: 10.0.2.0/24

The private subnet is designed for resources that should not be directly accessible from the internet.

🔒 Security Implementation
Security Groups

The EC2 security group follows a restrictive access model.

Inbound:
SSH (TCP 22) → My IP
HTTP (TCP 80) → 0.0.0.0/0

SSH access is restricted to the administrator's IP address instead of allowing unrestricted internet access.

🔑 IAM Least Privilege

An IAM role is used to provide the EC2 instance with controlled access to AWS resources.

Instead of storing AWS access keys on the EC2 server, the instance uses an IAM role.


🪣 Secure S3 Storage

The S3 bucket is configured with security in mind.

Security settings include:

✅ Block Public Access enabled
✅ ACLs disabled
✅ Server-side encryption enabled
✅ Versioning enabled
✅ Access controlled through IAM
❌ No unnecessary public access

The bucket is intended to remain private and accessible only to authorized AWS resources and users.

📊 Monitoring and Logging
AWS CloudTrail

CloudTrail is used to record AWS API activity.

It can help identify:

Who performed an action
What action was performed
When the action occurred
Which AWS resource was affected

This improves auditing and security visibility.

Amazon CloudWatch

CloudWatch is used to monitor AWS resources and collect metrics.

Example EC2 metrics include:

CPU Utilization
Network In
Network Out
Status Checks
Disk activity

Monitoring helps identify performance and availability problems.

🖥️ EC2 Instance

The EC2 instance acts as the compute resource within the public subnet.

Access is performed using:

EC2 Instance Connect / SSH

The instance is protected using a Security Group that restricts SSH access.

🧪 Testing and Verification

The following checks were performed during the implementation:

Network Connectivity
EC2 → Internet

Verified through the public subnet and Internet Gateway.

SSH Access
Client → Security Group → EC2 :22

Verified using EC2 Instance Connect.

S3 Access

Verified that the S3 bucket remains private and that access is controlled through IAM permissions.

Security Verification

Checked:

Security Group rules
Route tables
Public/private subnet configuration
S3 Block Public Access
IAM permissions
CloudTrail logging
CloudWatch monitoring

📚 Key Concepts Learned

Through this project, I gained practical experience with:

AWS VPC architecture
CIDR and subnetting
Route tables
Internet Gateway
EC2
Security Groups
IAM roles and policies
S3 security
CloudTrail
CloudWatch
Cloud security
Least privilege
Public vs private networking
