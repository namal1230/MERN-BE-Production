# AWS Terraform for blog-phost-be

This directory contains a minimal Terraform configuration for creating an EKS cluster on AWS.

## What it provisions
- VPC, public subnets, internet gateway, and route table
- EKS cluster with a managed node group

## Prerequisites
- Terraform installed
- AWS credentials configured locally

## Usage
1. Copy terraform.tfvars.example to terraform.tfvars
2. Update the AWS region if needed
3. Run:
   - terraform init
   - terraform plan
   - terraform apply

## Notes
- This configuration creates the infrastructure needed for an EKS cluster only.
- Application deployment and Kubernetes manifests should be managed separately.
