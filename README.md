# ☁️ Aurora Digital CloudFormation Project

## 📖 Overview
Aurora Digital, a luxury home goods retailer, is expanding its digital operations to AWS.  
This project demonstrates how to use **AWS CloudFormation** to build a **secure, scalable, and automated cloud infrastructure** — from a single EC2 instance to a fully load-balanced, auto-scaling environment.

---

## 🎯 Goal
Design and deploy a **reliable, high-performing web architecture** that can automatically scale during peak traffic events while maintaining strong security and cost efficiency.

Using AWS CloudFormation, this project provisions:
- A **custom VPC** with multiple public subnets  
- An **Auto Scaling Group** of EC2 instances running **Apache**  
- An **Application Load Balancer (ALB)** distributing incoming traffic  
- Security Groups enforcing **least-privilege access**  
- Infrastructure-as-Code templates for easy reuse and version control

---

## 🧩 Requirements

### Foundational
- Deploy an EC2 instance with Apache installed via **User Data**
- Use a Security Group allowing:
  - Port **22 (SSH)** for administration
  - Port **80 (HTTP)** for web traffic
- Verify web access through the public IP of the EC2 instance

### Advanced
- Create a **Launch Template** defining EC2 settings (t2.micro + Apache)
- Build an **Auto Scaling Group**:
  - Min instances: **2**
  - Max instances: **5**
  - Spread across **three public subnets**
- Configure Security Groups to allow web and SSH access
- Verify Apache serves a custom “Welcome to Aurora Digital” page

### Complex
- Create a **custom VPC (10.10.0.0/16)**  
- Add **three public subnets**:
  - 10.10.1.0/24  
  - 10.10.2.0/24  
  - 10.10.3.0/24  
- Attach an **Internet Gateway** and public route tables  
- Deploy an **Auto Scaling Group** across the three subnets  
- Add an **Application Load Balancer (ALB)** to distribute traffic  
- Configure:
  - **Web Server SG:** allows HTTP only from ALB SG  
  - **ALB SG:** allows HTTP from 0.0.0.0/0  
- Verify access via the **ALB DNS URL**

---

## ⚙️ How To Use

### 1️⃣ Prerequisites
- AWS account with IAM permissions for CloudFormation, EC2, and VPC
- Existing **Key Pair** for SSH access

### 2️⃣ Deploy the Stack
1. Open the **AWS CloudFormation Console**
2. Click **Create Stack → With new resources (standard)**
3. Upload the template file 
5. Click **Next → Next → Create Stack**
6. Wait until the status changes to **CREATE_COMPLETE**

### 3️⃣ Verify Deployment
- Go to the **Outputs** tab in CloudFormation
- Copy the **Public IP** or **ALB DNS Name**
- Open it in a browser to confirm the custom welcome page:
