# SESSION 14

# Elastic Beanstalk & RDS

In this demo, we learn how to deploy an application using **AWS Elastic Beanstalk** and store application data using **Amazon RDS**.

---

# 📌 What You Will Learn

- What is Elastic Beanstalk
- What is Amazon RDS
- Why we use these AWS services
- Deploy application using Elastic Beanstalk
- Create managed database using RDS
- 
---

# ☁️ AWS Elastic Beanstalk

AWS Elastic Beanstalk is a **Platform as a Service (PaaS)** that allows developers to deploy and manage applications without managing infrastructure manually.

AWS automatically handles:

- EC2 instance creation
- Load balancing
- Auto scaling
- Monitoring
- Software installation

Developers only upload application code.

---

## ✅ When Do We Use Elastic Beanstalk?

Elastic Beanstalk is used when:

- We want fast application deployment.
- We do not want to manage servers manually.
- We need automatic scaling.
- We want simplified DevOps management.

Example Use Cases:

- Web Applications
- APIs
- Student Projects
- Startup Applications

---

## ✅ Why Use Elastic Beanstalk?

Benefits:

- Easy deployment
- Automatic infrastructure provisioning
- Auto scaling support
- Health monitoring
- 
---

# 🗄 Amazon RDS (Relational Database Service)

Amazon RDS is a **managed relational database service** provided by AWS.

It allows users to create and manage relational databases without installing or maintaining database software.

Supported Databases:

- MySQL
- PostgreSQL
- MariaDB
- Oracle
- SQL Server

---

## ✅ When Do We Use RDS?

RDS is used when:

- Applications require relational databases.
- We want automatic backups.
- High availability is required.
- Database patching and maintenance should be automated.

Example Use Cases:

- E-commerce Applications
- Banking Systems
- Student Management Systems
- Enterprise Applications

---

## ✅ Why Use RDS?

Benefits:

- Automatic backups
- Software patching
- Multi Availability Zone support
- Easy scaling
- Secure database access

---

# 🏗 Architecture Overview

User → Elastic Beanstalk Application → Amazon RDS Database

Elastic Beanstalk hosts the application.

RDS stores application data securely.

---
