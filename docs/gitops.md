# GitOps Workflow

The project follows a GitOps deployment model where Git acts as the
source of truth for Kubernetes application configuration.

## Flow

Developer
↓
GitHub
↓
CI Pipeline
↓
Docker Build
↓
Amazon ECR
↓
Helm Configuration Update
↓
ArgoCD
↓
Amazon EKS
↓
Application

ArgoCD continuously monitors the Git repository and synchronizes the
desired Kubernetes state with the cluster.
