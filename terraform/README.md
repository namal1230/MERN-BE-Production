# AWS Terraform for blog-phost-be

This directory contains a starter Terraform configuration for deploying the backend service to AWS.

## What it provisions
- VPC, public subnets, internet gateway, and route table
- EKS cluster and managed node group
- ECR repository for container image storage
- CloudWatch log group for future cluster logging and diagnostics

## Prerequisites
- Terraform installed
- An ECR repository containing the container image, or a public image reference
- A MongoDB connection string
- Environment secrets such as JWT and external API keys

## Usage
1. Copy terraform.tfvars.example to terraform.tfvars
2. Fill in the required values
3. Run:
   - terraform init
   - terraform plan
   - terraform apply

## Notes
- The app expects environment variables such as MONGO_URI, SECRET_CODE, SENDGRID_API_KEY, CLOUD_NAME, CLOUD_API_KEY, CLOUD_API_SECRET, and UNSPLASH_ACCESS_KEY.
- For production, it is better to move secrets to AWS Secrets Manager and reference them from the task definition.
