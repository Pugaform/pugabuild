# Infrastructure Overview

This Terraform configuration sets up the essential AWS infrastructure for **Pugabuild**, providing a robust and scalable environment tailored for deploying Kubernetes workloads. Below is a summary of the key AWS resources being provisioned and their purposes.

## Key AWS Resources

### 1. **Networking**

- **VPC (Virtual Private Cloud)**
  - **Purpose:** Creates an isolated network environment for your AWS resources.
  - **Example CIDR Block:** `10.0.0.0/16`

- **Subnets**
  - **Public Subnets**
    - **Purpose:** Hosts resources that could be accessible from the internet, or need external access.
    - **Example CIDR Blocks:** `10.0.10.0/24`, `10.0.11.0/24`
  
  - **Private Subnets**
    - **Purpose:** Hosts resources in a secure subnet, inaccessible from the internet, useful for sensitive resources.
    - **Example CIDR Blocks:** `10.0.100.0/24`, `10.0.101.0/24`

- **Internet Gateway**
  - **Purpose:** Enables internet access for resources in public subnets.

- **NAT Gateway**
  - **Purpose:** Allows instances in private subnets to connect to the internet while preventing inbound internet traffic.

- **Route Tables**
  - **Public Route Tables:** Direct internet-bound traffic from public subnets to the Internet Gateway.
  - **Private Route Tables:** Direct internet-bound traffic from private subnets to the NAT Gateway.

### 2. **Compute and Kubernetes**

- **Amazon EKS Cluster**
  - **Purpose:** Managed Kubernetes service for deploying, managing, and scaling containerized applications.
  - **Configuration:** Configured with public endpoint access and integrated with the specified VPC and subnets.

- **EKS Node Group**
  - **Purpose:** Manages the EC2 instances that run your Kubernetes workloads.
  - **Instance Type Example:** `t3a.large`
  - **Scaling Configuration:** Configured with a minimum and desired size of 1 for cost efficiency.

### 3. **Identity and Access Management (IAM)**

- **IAM Roles**
  - **EKS Cluster Role:** Grants the EKS service permissions to manage AWS resources.
  - **Node Group Role:** Grants permissions to the EC2 instances in the node group to interact with other AWS services.
  - **External Secrets Role:** Allows Kubernetes External Secrets to access AWS Secrets Manager.
  - **External DNS Role:** Allows External DNS to manage DNS records.
  - **AWS Load Balancer Controller Role:** Manages AWS load balancers for Kubernetes services.

- **IAM Policies**
  - **Cluster and Service Policies:** Attach necessary permissions for EKS operations.
  - **Custom Policies:** Define specific permissions for External Secrets, External DNS, and AWS Load Balancer Controller.

### 4. **Secrets Management**

- **AWS Secrets Manager**
  - **Purpose:** Securely stores and manages sensitive information such as GitOps repository credentials.
  - **GitOps Secret:** GitOps repository URL and SSH private key. This secret is read by your ArgoCD in order to connect to your private repository to deploy applications and micro-services.

### 5. **Kubernetes Integration**

- **Kubernetes Provider**
  - **Purpose:** Connects Terraform with your Kubernetes cluster using the kubeconfig file.
  
- **OpenID Connect Provider (OIDC)**
  - **Purpose:** Enables Kubernetes service accounts to assume IAM roles for secure access to AWS resources.

### 6. **Access Management**

- **EKS Access Entries**
  - **Purpose:** Grants administrative access to specified IAM roles for managing the EKS cluster.
  - **Policies Attached:** Admin and Cluster Admin policies to provide necessary permissions.

## Summary

This configuration establishes a secure and scalable AWS environment for deploying Kubernetes workloads with Amazon EKS. Key features include:

- **Robust Networking:** VPC with configurable public and private subnets, Internet and NAT Gateways, and properly configured route tables.
- **Managed Kubernetes:** EKS cluster with a dedicated node group for running containerized applications.
- **Secure IAM Roles:** Fine-grained access control through dedicated IAM roles and policies for cluster management, external secrets, DNS management, and load balancing.
- **Secrets Management:** Secure storage of GitOps repository credentials using AWS Secrets Manager.

By deploying this infrastructure, **Pugabuild** ensures a ready-to-use, secure, and efficient environment for managing Kubernetes applications, facilitating smooth onboarding and scalable operations.

---
For any questions or support, please reach out to [support@pugaform.com](mailto:support@pugaform.com).