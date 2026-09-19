# Deployment Flow

## 1. Application Build

The Java application is built using Maven.

## 2. Code Quality

SonarQube performs static code analysis.

## 3. Containerization

The application is packaged into a Docker image.

## 4. Image Registry

The Docker image is pushed to Amazon ECR.

## 5. GitOps Update

The Kubernetes/Helm configuration is updated with the new image tag.

## 6. ArgoCD Synchronization

ArgoCD detects the Git change and synchronizes the application.

## 7. Kubernetes Deployment

The updated application is deployed to Amazon EKS.
