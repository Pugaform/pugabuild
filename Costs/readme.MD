# Pugaform Infrastructure Cost Estimation

This document provides detailed monthly cost estimations for the Pugaform infrastructure deployments. The estimations are categorized into two versions to cater to different performance and availability requirements.

## Table of Contents

- [Introduction](#introduction)
- [Cost Estimations](#cost-estimations)
  - [Cost Efficient Version](#cost-efficient-version)
  - [High Availability Version](#high-availability-version)
- [Additional Sections](#additional-sections)
- [Contact](#contact)

---

## Introduction

Pugaform is a scalable infrastructure solution designed to meet varying performance and availability needs. This document outlines the cost estimations for deploying Pugaform in both cost-efficient and high-availability configurations. Understanding these costs helps in making informed decisions based on your project's requirements and budget constraints.

## Cost Estimations

### Cost Efficient Version

This section provides a detailed monthly cost estimation for the Pugaform infrastructure deployed in a cost-efficient manner.

#### Resources and Costs

1. **Amazon EKS Control Plane**
    - **Description:** Managed Kubernetes control plane for orchestrating containers.
    - **Cost:** $0.10 per hour
    - **Monthly Total:**
      - $0.10/hour * 730 hours/month = **$73.00/month**

2. **EC2 Instances (t3a.large)**
    - **Description:** General-purpose EC2 instance providing 8 GB of memory, suitable for supporting up to 34 pods.
    - **Instance Type:** t3a.large
    - **Cost per Instance:** $0.0752 per hour
    - **Number of Instances:** 1
    - **Monthly Total:**
      - $0.0752/hour * 730 hours/month * 1 = **$54.80/month**

3. **NAT Gateway**
    - **Description:** Provides internet access to instances in private subnets.
    - **Number of NAT Gateways:** 1
    - **Cost per NAT Gateway:** $0.045 per hour
    - **Monthly Total:**
      - $0.045/hour * 730 hours/month = **$32.85/month**
    - **Notes:**
      - Data Transfer Costs: Additional usage-based charges may apply depending on data throughput.

4. **AWS Secrets Manager**
    - **Description:** Securely stores and manages secrets such as API keys, passwords, and other sensitive information.
    - **Number of Secrets:** 1
    - **Cost per Secret:** $0.40 per month
    - **Monthly Total:**
      - 1 * $0.40 = **$0.40/month**

5. **Elastic Block Store (EBS) Storage**
    - **Description:** Persistent block storage for EC2 instances.
    - **Storage Type:** gp2
    - **Storage Size:** 20 GB
    - **Cost per GB:** $0.10 per GB-month
    - **Monthly Total:**
      - 20 GB * $0.10 = **$2.00/month**

#### Total Estimated Cost

- **$162.05/month** without additional usage-based charges.

---

#### 📈 EC2 Scale Cost Structure

While the current estimation is based on a single t3a.large instance, costs will scale linearly with the number of instances:

| Number of EC Instances | Calculation                      | Total Cost |
|------------------------|----------------------------------|------------|
| 1                      | $162.05                           | $162.05    |
| 2                      | $162.05 + $54.80                  | $216.85    |
| 3                      | $162.05 + ($54.80 × 2)             | $271.65    |
| 4                      | $162.05 + ($54.80 × 3)             | $326.45    |

And so on.

*Adjust the number of EC2 instances based on needs and workload demands.*

---

#### ✅ Summary

The Pugaform setup with **1 NAT Gateway** and **1 t3a.large EC2 instance** incurs an estimated monthly cost of **~$162.05**. This setup provides a balanced approach between performance and cost, suitable for supporting up to 34 pods per instance. Costs are scalable based on the number of EC2 instances, allowing clients to adjust resources as their application demands grow.

- **Estimated Base Cost:** $162.05/month
- **Scalability:** Linear increase with the number of EC2 instances
- **Optimization:** Utilize Reserved Instances, right-sizing, and Spot Instances for further cost savings

---

### High Availability Version

This section provides a detailed monthly cost estimation for the Pugaform infrastructure deployed with high availability.

#### Resources and Costs

1. **Amazon EKS Control Plane**
    - **Description:** Managed Kubernetes control plane for orchestrating containers.
    - **Cost:** $0.10 per hour
    - **Monthly Total:**
      - $0.10/hour * 730 hours/month = **$73.00/month**

2. **EC2 Instances (t3a.large)**
    - **Description:** General-purpose EC2 instance providing 8 GB of memory, suitable for supporting up to 34 pods.
    - **Instance Type:** t3a.large
    - **Cost per Instance:** $0.0752 per hour
    - **Number of Instances:** 1
    - **Monthly Total:**
      - $0.0752/hour * 730 hours/month * 1 = **$54.80/month**

3. **NAT Gateway**
    - **Description:** Provides internet access to instances in private subnets.
    - **Number of NAT Gateways:** 2
    - **Cost per NAT Gateway:** $0.045 per hour
    - **Monthly Total:**
      - $0.045/hour * 730 hours/month * 2 = **$65.70/month**
    - **Notes:**
      - Data Transfer Costs: Additional usage-based charges may apply depending on data throughput.

4. **AWS Secrets Manager**
    - **Description:** Securely stores and manages secrets such as API keys, passwords, and other sensitive information.
    - **Number of Secrets:** 1
    - **Cost per Secret:** $0.40 per month
    - **Monthly Total:**
      - 1 * $0.40 = **$0.40/month**

5. **Elastic Block Store (EBS) Storage**
    - **Description:** Persistent block storage for EC2 instances.
    - **Storage Type:** gp2
    - **Storage Size:** 20 GB
    - **Cost per GB:** $0.10 per GB-month
    - **Monthly Total:**
      - 20 GB * $0.10 = **$2.00/month**

#### Total Estimated Cost

- **$194.90/month** without additional usage-based charges.

---

#### 📈 EC2 Scale Cost Structure

While the current estimation is based on a single t3a.large instance, costs will scale linearly with the number of instances:

| Number of EC Instances | Calculation                        | Total Cost |
|------------------------|------------------------------------|------------|
| 1                      | $194.90                             | $194.90    |
| 2                      | $194.90 + $54.80                    | $249.70    |
| 3                      | $194.90 + ($54.80 × 2)               | $304.50    |
| 4                      | $194.90 + ($54.80 × 3)               | $359.30    |

And so on.

*Adjust the number of EC2 instances based on needs and workload demands.*

---

#### ✅ Summary

The Pugaform setup with **2 NAT Gateways** and **1 t3a.large EC2 instance** incurs an estimated monthly cost of **~$194.90**. This setup provides a balanced approach between performance and cost with high availability running on two availability zones, suitable for supporting up to 34 pods per instance. Costs are scalable based on the number of EC2 instances, allowing clients to adjust resources as their application demands grow.

- **Estimated Base Cost:** $194.90/month
- **Scalability:** Linear increase with the number of EC2 instances
- **Optimization:** Utilize Reserved Instances, right-sizing, and Spot Instances for further cost savings

---

## Additional Sections

*You can add more sections here as needed, such as:*

- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Contributing](#contributing)
- [License](#license)

---

## Contact

For any questions or support, please contact [support@pugaform.com](mailto:support@pugaform.com).