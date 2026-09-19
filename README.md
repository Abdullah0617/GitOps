# 🚀 VProfile GitOps Deployment Platform

A production-style **DevOps and GitOps deployment platform** for deploying a Java-based VProfile application on **Amazon EKS** using Terraform, Docker, Kubernetes, Helm, ArgoCD, GitHub Actions, SonarQube and Amazon ECR.

---

## 📌 Project Overview

This project implements an end-to-end **CI/CD and GitOps workflow** for a containerized Java application running on AWS.

The project combines **Infrastructure as Code, Continuous Integration, Containerization, Kubernetes orchestration and GitOps-based Continuous Deployment** into a single automated deployment workflow.

The implementation is divided into three repositories:

- **VP-App** → Application source code and CI pipeline
- **VP-Infra** → AWS infrastructure using Terraform
- **VP-Helm** → Kubernetes, Helm and ArgoCD deployment configuration

The complete workflow is:

```text
Developer
    │
    ▼
  GitHub
    │
    ▼
GitHub Actions
    │
    ├── Maven Build
    ├── SonarQube Analysis
    ├── Docker Build
    └── Docker Push
            │
            ▼
        Amazon ECR
            │
            ▼
      Update Image Tag
            │
            ▼
         VP-Helm
            │
            ▼
          ArgoCD
            │
            ▼
        Amazon EKS
            │
            ▼
    Kubernetes Workloads
            │
            ▼
     Running Application
```
🏗️ Architecture

Architecture Diagram Location
architecture/
└── architecture.png
🛠️ Tech Stack
☁️ Cloud
AWS
Amazon EKS
Amazon ECR
Amazon RDS
IAM
VPC
Security Groups
AWS Load Balancer / Ingress
⚙️ DevOps
Git
GitHub
GitHub Actions
CI/CD
Docker
Maven
SonarQube
Terraform
☸️ Kubernetes & GitOps
Kubernetes
Helm
ArgoCD
Kubernetes Ingress
💻 Programming
Java
✨ Features
Automated CI/CD Pipeline
Infrastructure as Code using Terraform
Docker Containerization
Automated Docker Image Build
Amazon ECR Container Registry
Amazon EKS Kubernetes Deployment
Helm-based Application Deployment
GitOps using ArgoCD
Continuous Kubernetes Synchronization
SonarQube Code Quality Analysis
Automated Application Delivery
Version-Controlled Infrastructure
Declarative Deployment Configuration
Cloud-based Application Hosting
Kubernetes Ingress for Application Access
🔄 Project Workflow
Developer pushes application code to GitHub.
GitHub Actions automatically triggers the CI pipeline.
Maven builds the Java application.
SonarQube performs static code analysis.
Docker builds the application container image.
The Docker image is pushed to Amazon ECR.
The deployment configuration is updated with the new image tag.
ArgoCD monitors the GitOps repository.
ArgoCD detects the change in the desired state.
ArgoCD synchronizes the Kubernetes resources.
Amazon EKS updates the application workload.
The updated application becomes available through the configured ingress/load balancer.
🔁 CI/CD Pipeline
Developer
    │
    ▼
GitHub
    │
    ▼
GitHub Actions
    │
    ├── Maven Build
    │
    ├── SonarQube
    │
    ├── Docker Build
    │
    └── Docker Push
            │
            ▼
        Amazon ECR
CI Pipeline Stages
1. Source Control

Application code is maintained in Git and stored in GitHub.

2. Maven Build

Maven is used for:

Dependency management
Compilation
Testing
Application packaging
3. SonarQube Analysis

SonarQube is integrated into the CI pipeline for static code analysis and code quality monitoring.

4. Docker Build

The application is packaged into a Docker image to provide a consistent runtime environment.

5. Amazon ECR

The generated Docker image is pushed to Amazon Elastic Container Registry.

🔁 GitOps Workflow

The deployment side of the project follows the GitOps model.

             Git Repository
                    │
                    │ Desired State
                    ▼
                 ArgoCD
                    │
             Reconciliation
                    │
                    ▼
               Amazon EKS
                    │
                    ▼
           Kubernetes Workloads
                    │
                    ▼
              Application

Git acts as the source of truth for the desired application deployment state.

ArgoCD continuously monitors the GitOps repository and synchronizes the Kubernetes cluster with the configuration stored in Git.

☸️ Kubernetes Deployment

The application is deployed on Amazon EKS using Kubernetes.

Example workloads:

Amazon EKS
│
├── VProfile Application
├── Database
├── Memcached
└── RabbitMQ

The Kubernetes configuration is maintained using Kubernetes manifests and Helm charts.

⛵ Helm

Helm is used to package and manage the application's Kubernetes configuration.

Example structure:

helm/
└── vprofile/
    │
    ├── Chart.yaml
    ├── values.yaml
    │
    └── templates/
        ├── deployment.yaml
        ├── service.yaml
        └── ...
Helm provides
Reusable Kubernetes configuration
Parameterized deployments
Simplified application configuration
Version-controlled deployment templates
Easier Kubernetes resource management
🔄 ArgoCD

ArgoCD is used as the GitOps Continuous Delivery tool.

VP-Helm
   │
   │ Watches Git Repository
   ▼
ArgoCD
   │
   │ Synchronizes
   ▼
Amazon EKS

ArgoCD continuously checks the desired state stored in Git and reconciles the Kubernetes cluster with that configuration.

ArgoCD responsibilities
Monitor GitOps repository
Detect configuration changes
Synchronize Kubernetes resources
Maintain desired application state
Provide deployment visibility
Enable Git-based deployment management
🏗️ Infrastructure as Code

Terraform is used to provision and manage AWS infrastructure.

Terraform Code
      │
      ▼
Terraform Plan
      │
      ▼
Terraform Apply
      │
      ▼
AWS Infrastructure
Terraform manages infrastructure such as
Amazon EKS
AWS networking
IAM roles and policies
Security configuration
Amazon ECR
Ingress-related infrastructure
Supporting cloud resources
📂 Terraform Structure
terraform/
│
├── main.tf
├── variables.tf
├── outputs.tf
├── backend.tf
├── iam_policy.json
└── argocd-ingress.yaml
File Responsibilities
File	Purpose
main.tf	Main infrastructure resources
variables.tf	Configurable Terraform variables
outputs.tf	Terraform output values
backend.tf	Terraform backend/state configuration
iam_policy.json	IAM policy configuration
argocd-ingress.yaml	ArgoCD ingress configuration
📦 Repository Structure

The complete implementation is logically divided into three repositories.

GitOps Project
│
├── VP-App
│   ├── .github/
│   │   └── workflows/
│   ├── Docker-files/
│   ├── src/
│   ├── pom.xml
│   └── sonar-project.properties
│
├── VP-Infra
│   ├── main.tf
│   ├── variables.tf
│   ├── outputs.tf
│   ├── backend.tf
│   ├── iam_policy.json
│   └── argocd-ingress.yaml
│
└── VP-Helm
    ├── argocd/
    ├── helm/
    │   └── vprofile/
    └── kubedefs/
🔗 Repository Responsibilities
📁 VP-App

Contains:

Java application
Maven configuration
GitHub Actions workflow
Docker configuration
SonarQube configuration

Workflow:

Java Application
      │
      ▼
Maven
      │
      ▼
SonarQube
      │
      ▼
Docker
      │
      ▼
Amazon ECR
📁 VP-Infra

Contains Terraform-based infrastructure configuration.

Workflow:

Terraform
    │
    ▼
AWS Resources
    │
    ▼
Amazon EKS
📁 VP-Helm

Contains:

Helm charts
Kubernetes manifests
ArgoCD configuration

Workflow:

Helm + Kubernetes
        │
        ▼
      ArgoCD
        │
        ▼
    Amazon EKS
☁️ AWS Services Used
AWS Service	Purpose
Amazon EKS	Kubernetes cluster for application deployment
Amazon ECR	Container image registry
Amazon RDS	Managed database
IAM	Access control and permissions
VPC	Network isolation
Security Groups	Network traffic control
Load Balancer	Application traffic routing
🐳 Containerization

Docker is used to package the Java application together with its runtime requirements.

Application Source
       │
       ▼
    Maven Build
       │
       ▼
   Docker Build
       │
       ▼
 Docker Image
       │
       ▼
   Amazon ECR
       │
       ▼
    Amazon EKS

The same application image can then be deployed consistently through the Kubernetes environment.

🌐 Application Access

Application traffic is routed through Kubernetes ingress and AWS load-balancing infrastructure.

Users
  │
  ▼
Load Balancer
  │
  ▼
Kubernetes Ingress
  │
  ▼
VProfile Service
  │
  ▼
VProfile Application
🔐 Security

Security-related configuration is handled using AWS IAM, networking controls and restricted access to cloud resources.

Security practices
IAM-based access control
Security Groups for network filtering
Private credentials kept outside source control
Git-based configuration management
Controlled Kubernetes access
Sensitive configuration excluded from the public repository
Never commit
❌ AWS Access Keys
❌ AWS Secret Keys
❌ Private SSH Keys
❌ .pem files
❌ kubeconfig files
❌ Database passwords
❌ API Tokens
❌ GitHub Tokens
❌ SonarQube Tokens
❌ .env files containing secrets
❌ Terraform State containing sensitive information
📸 Screenshots
GitHub Actions

ArgoCD

Amazon EKS

Amazon ECR

Deployed Application

📊 Complete Deployment Flow
                     DEVELOPER
                         │
                         ▼
                      GitHub
                         │
                         ▼
                GitHub Actions
                         │
             ┌───────────┼───────────┐
             │           │           │
             ▼           ▼           ▼
          Maven      SonarQube     Docker
          Build       Analysis      Build
                                      │
                                      ▼
                                Amazon ECR
                                      │
                                      ▼
                                Image Tag
                                      │
                                      ▼
                                  VP-Helm
                                      │
                                      ▼
                                    ArgoCD
                                      │
                                      ▼
                                 Amazon EKS
                                      │
                                      ▼
                              Kubernetes Pods
                                      │
                                      ▼
                                Application
🌱 Infrastructure Flow
             VP-Infra
                 │
                 ▼
              Terraform
                 │
                 ▼
          AWS Infrastructure
                 │
       ┌─────────┼──────────┐
       │         │          │
       ▼         ▼          ▼
      EKS       ECR        IAM
       │
       ▼
   Kubernetes
✨ Project Highlights
End-to-End DevOps Implementation
Infrastructure as Code with Terraform
AWS Cloud Deployment
Amazon EKS Kubernetes Cluster
Docker-based Application Containerization
Automated CI using GitHub Actions
Maven Build Automation
SonarQube Integration
Amazon ECR Container Registry
Helm-based Kubernetes Deployment
GitOps with ArgoCD
Declarative Infrastructure
Automated Application Delivery
Version-Controlled Deployment Configuration
Kubernetes Ingress
IAM-based Access Management
🎓 Learning Outcomes

Through this project, I gained practical experience in:

AWS Cloud Infrastructure
Terraform
Infrastructure as Code
Amazon EKS
Kubernetes
Docker
Amazon ECR
Helm
ArgoCD
GitOps
GitHub Actions
CI/CD
Maven
SonarQube
Kubernetes Networking
IAM
Cloud Deployment
Containerized Application Deployment
DevOps Automation
📌 Key DevOps Concepts

This project demonstrates practical implementation of:

Infrastructure as Code
        ↓
     Terraform
        ↓
   AWS Infrastructure
        ↓
      Amazon EKS
        ↓
    Kubernetes
        ↓
       Helm
        ↓
      ArgoCD
        ↓
       GitOps

Alongside the CI pipeline:

Developer
    ↓
GitHub
    ↓
GitHub Actions
    ↓
Maven
    ↓
SonarQube
    ↓
Docker
    ↓
Amazon ECR
📈 Project Outcome

The final architecture provides a repeatable and automated path from source code to a running application on Kubernetes.

Code
 ↓
CI Pipeline
 ↓
Container Image
 ↓
GitOps Configuration
 ↓
ArgoCD
 ↓
Amazon EKS
 ↓
Application

The project reduces manual deployment steps and keeps infrastructure and deployment configuration version controlled through Git.

🚀 Future Improvements

Possible future improvements include:

Automated infrastructure deployment through CI/CD
Terraform module restructuring
Multi-environment deployments
Automated security scanning
Centralized monitoring and observability
Prometheus and Grafana integration
Automated rollback strategies
Kubernetes resource optimization
Secret management using AWS Secrets Manager
Advanced deployment strategies such as Blue-Green or Canary deployments
📁 Showcase Repository Structure
vprofile-gitops/
│
├── README.md
│
├── architecture/
│   └── architecture.png
│
├── terraform/
│   ├── main.tf
│   ├── variables.tf
│   ├── outputs.tf
│   ├── backend.tf
│   └── iam_policy.json
│
├── kubernetes/
│   └── ...
│
├── helm/
│   └── vprofile/
│       ├── Chart.yaml
│       ├── values.yaml
│       └── templates/
│
├── argocd/
│   └── ...
│
├── ci-cd/
│   ├── pipeline.yml
│   ├── Dockerfile
│   └── sonar-project.properties
│
└── screenshots/
    ├── github-actions.png
    ├── argocd.png
    ├── eks.png
    ├── ecr.png
    └── application.png
👨‍💻 Author
Abdullah Zahid

B.Tech Computer Science Engineering

Cloud & DevOps Enthusiast

Areas of Interest
AWS
Cloud Computing
DevOps
Cloud Security
Kubernetes
Infrastructure as Code
GitOps
CI/CD
Cloud-Native Technologies
