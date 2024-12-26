# Overall Structure

![img.png](asset/ops-flows.png)

## 1. AWS Infrastructure
Provision AWS Infrastructure using terraform 
(see [terraform](https://github.com/duylv-devops-todo-app/sd5232_aws_infrastructure/tree/main/terraform/infrastructure/cluster)). 
Generally, resources to be created are:
- VPC, Subnets, Security Group
- EKS, ECR
- EC2: includes `Jenkins`, `Git`, `Java 17`, `kubectl`

## 2. Repository
- [Application](https://github.com/duylv-devops-todo-app/sd5232_msa): 
  - 1 backend.
  - 1 frontend.
  - 1 database.
  - CI Jenkins files for above.
  - K8s scripts for above.
- [DevOps](https://github.com/duylv-devops-todo-app/sd5232_aws_infrastructure):
    - Terraform script to define AWS Infrastructure.
    - CD Jenkins files.

## 3. How to
**Prerequisite:**
- AWS account.
- Terraform available on your machine.
### 3.1. Init infrastructure
Check out [DevOps](https://github.com/duylv-devops-todo-app/sd5232_aws_infrastructure), then run below command:
```bash
terraform init
terraform validate
terraform plan
```
If everything looks good, let's run
```bash
terraform apply
```
After all, open your AWS account to see created resources.
**Note:** please run `terraform destroy` after your work done.

### 3.2. Setup EC2
#### Install Docker
Connect to your EC2 instance. 
```
sudo yum install docker
sudo systemctl start docker
sudo usermod -a -G docker jenkins
```

### 3.3. Setup Jenkins
#### Plugins:
- Docker Pipeline
- Pipeline Utility Steps
- Stage View
- AWS Credentials
- Amazon EC2
- Amazon ECR
#### Credentials
- Github
- AWS
#### CI Pipeline
#### CD Pipeline