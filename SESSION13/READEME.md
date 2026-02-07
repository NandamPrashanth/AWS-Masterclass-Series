# SESSION 13

Hello Everyone, In this video we will discuss the following topics

- AWS Systems Manager (SSM)
- Amazon EventBridge
- Cloudwatch Monitoring

-----------------------------------------------------------------------------------------------------------------

## 📌 What is AWS Systems Manager?

AWS Systems Manager (SSM) is a management service that helps you securely manage, monitor, and automate operational tasks across AWS resources such as EC2 instances.

It allows you to:
- Run commands remotely (without SSH)
- Automate operational workflows
- Patch instances
- Manage configurations
- Maintain compliance

---

## 🎯 Why is Systems Manager Used?

- No need to open port 22 (SSH)
- Centralized server management
- Automation of operational tasks
- Secure instance access
- Production-grade DevOps management

---

SSM Agent is a software agent that runs on your EC2 instance and enables AWS Systems Manager to communicate with that instance.

### Official AWS document link to install SSM Agent
https://docs.aws.amazon.com/systems-manager/latest/userguide/ssm-agent.html

## ✅ Prerequisites

- AWS Account
- EC2 Instance (Amazon Linux 2 recommended)
- IAM Role attached to EC2:
  - `AmazonSSMManagedInstanceCore`
- Internet access for the instance

----------------------------------------------------------------------------------------------------------------------------------------------------------


---

### Amazon EventBridge

## 📌 What is Amazon EventBridge?

Amazon EventBridge is a serverless event bus that connects AWS services using events.

It enables event-driven architectures where services react automatically to changes.

Example:
- EC2 stops → Trigger automation
- S3 upload → Start processing
- Alarm triggered → Send notification

---

## 🎯 Why is EventBridge Used?

- Automates workflows
- Enables event-driven architecture
- Reduces manual operations
- Connects multiple AWS services
- Real-time system reactions

-------------------------------------------------------------------------------------------------------------

### Amazon CloudWatch Monitoring

## 📌 What is Amazon CloudWatch?

Amazon CloudWatch is a monitoring and observability service for AWS resources and applications.

It collects:
- Metrics (CPU, memory, network)
- Logs
- Events

It allows you to:
- Monitor performance
- Create alarms
- Trigger automated actions

---

## 🎯 Why is CloudWatch Used?

- Monitor infrastructure health
- Detect performance issues
- Enable alerting system
- Improve system reliability
- Production monitoring

---

### To Generate CPU Load

Connect to EC2 and install stress tool:

- sudo yum install stress -y

-----------------------------------------------------------------------------------------------

## 📌 What is Amazon SNS?

Amazon SNS (Simple Notification Service) is a fully managed messaging service that enables you to send notifications and messages to multiple subscribers using a publish-subscribe (Pub/Sub) model.

With SNS:
- A publisher sends a message to a topic
- All subscribers to that topic receive the message

---

## 📌 What is an SNS Topic?

An SNS Topic is a communication channel that allows messages to be sent from publishers to multiple subscribers.

Example:
CloudWatch Alarm → SNS Topic → Email + SMS + Lambda

---

## 🎯 Why is SNS Used?

SNS is commonly used for:

- Sending CloudWatch alarm notifications
- Application alerts
- SMS notifications
- Triggering Lambda functions
- Event-driven architectures
- Fan-out messaging to multiple systems

In production:
- High CPU usage → Send alert email
- Payment successful → Notify billing + shipping
- Security alert → Trigger automated response

---

## 🧠 How SNS Works (Architecture Flow)

1. Event occurs (e.g., CPU > 70%)
2. CloudWatch triggers alarm
3. Alarm sends message to SNS Topic
4. SNS delivers message to all subscribers

---
