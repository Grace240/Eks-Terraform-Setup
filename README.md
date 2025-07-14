# 🚀 Terraform Installation And Setup In AWS EC2 Linux Instances. Using Terraform to provision a fully managed Amazon EKS Cluster

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=aws,bash,git,kubernetes,terraform,vim" />
  </a>
</p>

Welcome to the **Amazon EKS Cluster!** This module helps you set up eks cluster which is provision from terraform. Once configured, you'll receive notifications when your AWS charges exceed specified amounts, helping you stay on top of your costs. 

## 🛠️ Prerequisites 

> [!IMPORTANT]
> **Before you begin, make sure you have the following:**
>
> - 🧰 **Terraform (v1.5.0 or later)** installed on your local machine.
> - 🌐 **An AWS account** with appropriate permissions:
> - + Create an ubuntu EC2 Instnace.
    + Create IAM Role With Required Policies.
    + VPCFullAccess
    + EC2FullAcces
    + S3FullAccess
    + Administrator Access
    + Attach IAM Role to EC2 Instance.

---

## 📦 Setup Instructions

### 1️⃣ Clone the Repository  

1. Open your terminal or command prompt.  
2. Navigate to the directory where you'd like to place the project:  

   ```bash  
   cd /path/to/your/directory  
   ```  

3. Clone the repository:  

   ```bash  
   git clone https://github.com/Grace240/Aws-Billing-Alert.git  
   ```  

4. Move into the directory:  

   ```bash  
   cd Aws-Billing-Alert  
   ```  

---



### CREATE an admin user to manage our EKS Cluster
```sh
sudo adduser eksadmin
sudo echo "eksadmin  ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/eksadmin
sudo su - eksadmin
```

### 2️⃣ Install Terraform  
There are several methods to install terraform
Follow the steps in your system documentation to install **Terraform** or use the quick instructions for Ubuntu:  
### Install terraform by running the commands below:
```
$ sudo apt-get update && sudo apt-get install -y gnupg software-properties-common

# Install the HashiCorp GPG key.
$ wget -O- https://apt.releases.hashicorp.com/gpg | \
  gpg --dearmor | \
$ sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg > /dev/null

# Verify the key's fingerprint.
$ gpg --no-default-keyring \
  --keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg \
  --fingerprint
 
# The gpg command will report the key fingerprint:
$ /usr/share/keyrings/hashicorp-archive-keyring.gpg
-------------------------------------------------
pub   rsa4096 XXXX-XX-XX [SC]
AAAA AAAA AAAA AAAA
uid           [ unknown] HashiCorp Security (HashiCorp Package Signing) <security+packaging@hashicorp.com>
sub   rsa4096 XXXX-XX-XX [E]

# Download the package information from HashiCorp.
$ sudo apt update

# Install Terraform from the new repository.
$ sudo apt-get install terraform
```

### Run via macOS terminal:
``` Package manager
brew tap hashicorp/tap
brew install hashicorp/tap/terraform
```

### Run via Script:
``` sh
$ git clone https://github.com/Grace240/Eks-Terraform-Setup
$ cd eks-terraform-setup
# install terraform using a bash shell script
$ sh terraform-install.sh

# run the scripts https://github.com/Grace240/Eks-Terraform-Setup/blob/main/terraform-install.sh
```

#### <span style="color:orange">Update Your Key Name in variables.tf file before executing terraform script.</span>
## Infrastructure As A Code using Terraform
#### Create Infrastructure(Amazon EKS, IAM Roles, AutoScalingGroups, Launch Configuration, LoadBalancer, NodeGroups,VPC,Subnets,Route Tables,Security Groups, NACLs, ..etc) As A Code Using Terraform Scripts
``` sh
# Initialise to install plugins
$ terraform init 

# Validate terraform scripts
$ terraform validate 

# Plan terraform scripts which will list resources which is going  be created.
$ terraform plan 

# Apply to create resources with 
$ terraform apply --auto-approve
```

```sh
##  Destroy Infrastructure  
$ terraform destroy --auto-approve

## create the kubeconfig file  
$ mkdir .kube/ 
$ vi .kube/config
$ kubectl get pod
$ #!/bin/bash 
$ sh iam-authenticator.sh 
$ kubectl get pod
## deploy cluster auto scaler
$ kubectl apply -f clusterautoscaler.yml
```

##  Destroy Infrastructure  
```sh
$ terraform destroy --auto-approve 
```


# EKS Getting Started Guide Configuration

This is the full configuration from https://www.terraform.io/docs/providers/aws/guides/eks-getting-started.html

See that guide for additional information.

NOTE: This full configuration utilizes the [Terraform http provider](https://www.terraform.io/docs/providers/http/index.html) to call out to icanhazip.com to determine your local workstation external IP for easily configuring EC2 Security Group access to the Kubernetes servers. Feel free to replace this as necessary.


$ kubectl create deployment autoscaler-demo --image=nginx

$ kubectl get pods --all-namespaces | grep Running | wc -l

$ kubectl get pods --all-namespaces --no-headers | wc -l

$ kubectl get nodes -o yaml | grep pods

$ kubectl scale deployment autoscaler-demo --replicas=20

$ https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html

$ aws-iam-authenticator help
