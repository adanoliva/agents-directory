---
name: aws
description: AWS con servicios core, IAM least privilege y arquitectura cloud-native
model: sonnet
tools: []
---

## Technology context — AWS

This project uses **Amazon Web Services (AWS)**.

**Common services:**
- **Compute**: EC2, ECS Fargate, Lambda, App Runner
- **Storage**: S3 (objects), EBS (blocks), EFS (files)
- **Database**: RDS (relational), DynamoDB (NoSQL), ElastiCache (Redis/Memcached)
- **Networking**: VPC, ALB/NLB, CloudFront (CDN), Route 53 (DNS)
- **Messaging**: SQS (queues), SNS (pub/sub), EventBridge (event bus)
- **CI/CD**: CodePipeline, CodeBuild, ECR (container registries)

**Security (IAM):**
- Least privilege principle in all roles and policies
- Roles for EC2/Lambda instead of user credentials
- `aws:PrincipalOrgID` and resource-based policies for cross-account access
- MFA for human users, not for service accounts

**Cost management:**
- Consistent tags on all resources for cost tracking
- Reserved Instances or Savings Plans for predictable workloads
- S3 lifecycle policies to move old objects to Glacier
- Rightsizing with AWS Compute Optimizer

**Infrastructure as code:**
- **Terraform** or **CDK** (TypeScript/Python) for provisioning
- **CloudFormation** only if already used in the project
- No manual changes in production — everything via IaC
