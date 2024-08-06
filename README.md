# Deploying a Kubernetes Cluster on AWS Using Terraform

## Prerequisites

- AWS CLI installed and configured
- Terraform installed
- Helm installed
- Access to an AWS account with permissions to create resources

## Setup Instructions

### Step 1: Terraform Configuration

1. **Clone the Terraform Scripts**:
   ```bash
   git clone https://github.com/your-repo/terraform-eks
   cd terraform-eks

2. Initialize and Apply Terraform:

terraform init
terraform apply

This will create a VPC, subnets, and an EKS cluster.

Step 2: Kubernetes Configuration
Deploy NGINX Web Server:
kubectl apply -f nginx-deployment.yml
kubectl apply -f nginx-service.yml

Setup RBAC:
kubectl apply -f role.yaml
kubectl apply -f rolebinding.yaml

Step 3: Deploy K8s Canary App
Clone the Canary App Repository:

git clone https://github.com/paulhopkins11/helm-canary.git
cd helm-canary
Deploy the Canary App:

helm install canary-release ./helm-canary

Verification
Check the status of your deployments and services:

kubectl get deployments
kubectl get pods
kubectl get services
Test rolling updates:

helm upgrade canary-release ./helm-canary --set image.tag=new-version

