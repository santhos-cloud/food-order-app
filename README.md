# 📘 Scalable Todo Application on AWS

A secure, highly available Todo Management Application built using real-time AWS enterprise architecture.  
Users authenticate with **Amazon Cognito**, interact with a **Flask REST API** running on private EC2 instances, and store task data in **Amazon RDS**.  
The backend auto-scales using **Auto Scaling Groups** and is exposed via an **Application Load Balancer**.

---

## 🚀 Architecture Overview

- **Authentication:** Amazon Cognito (User Pool + Hosted UI)
- **Backend:** Flask REST API on private EC2 instances
- **Load Balancing:** Application Load Balancer (public)
- **Database:** Amazon RDS (private subnet)
- **Networking:** VPC with public + private subnets, NAT Gateway
- **Scalability:** Auto Scaling Group integrated with ALB
- **Security:** JWT verification, IAM roles, layered security groups

---

## 🧩 Features

- Secure user signup + login using Cognito
- JWT-based authentication and authorization
- Users can create and view only their own todos
- RESTful API using Flask
- Private EC2 + private RDS architecture
- Highly available backend with auto scaling
- CloudWatch logs for API and infrastructure monitoring

---

## 🏗️ High-Level Architecture Diagram


---

## 📡 API Endpoints

### 🔹 Create Todo  
`POST /todo`  
Headers:  
`Authorization: Bearer <JWT>`

### 🔹 Get Todos  
`GET /todo`  
Headers:  
`Authorization: Bearer <JWT>`

---

## ⚙️ Technologies Used

- Amazon Cognito
- Amazon EC2
- Amazon RDS
- Application Load Balancer
- Auto Scaling Group
- VPC (public + private subnets)
- IAM Roles
- CloudWatch
- Flask (Python)

---

---

## 🔐 Security Highlights

- JWT authentication validated in backend
- EC2 + RDS placed inside private subnets
- Only ALB exposed publicly
- Principle of Least Privilege IAM policies
- Security groups restrict access layer-by-layer

---

## 🎯 Why This Project Matters

Demonstrates real cloud engineering skills:  
✔ Authentication  
✔ Networking (public/private subnets)  
✔ Load Balancing  
✔ Auto Scaling  
✔ Secure backend hosting  
✔ RDS integration  
✔ Enterprise-level architecture  

---

## 📁 Suggested Repository Name


**aws-scalable-todo-app**

---

## 📝 Author

Your Name  
AWS | DevOps | Cloud Engineer


