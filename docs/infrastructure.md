# Infrastructure

Terraform is used to provision and manage the AWS infrastructure
required by the application platform.

## Main Components

- Amazon EKS
- IAM
- Kubernetes access configuration
- Networking components
- Application ingress
- AWS supporting resources

## Terraform Structure

main.tf       → Infrastructure resources
variables.tf  → Configurable variables
outputs.tf    → Infrastructure outputs
backend.tf    → Terraform state configuration
iam_policy.json → IAM permissions
