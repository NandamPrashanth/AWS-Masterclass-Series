# SESSION 5

## 1.Introduction to AMI

### What is an AMI?
An **Amazon Machine Image (AMI)** is a pre-configured template that contains the software configuration (operating system, application server, and applications) required to launch an EC2 instance.

### Why is it important?
- It acts as the **blueprint** for your EC2 instance.
- You can create **custom AMIs** to standardize configurations and quickly scale environments.

## 2.What Does an AMI Include?

An AMI includes:

1. **A root volume image** — typically an OS like Linux or Windows.
2. **Launch permissions** — who can use the AMI to launch instances.
3. **Block device mappings** — defines volumes to attach when instance launches.

## 3.Types of AMIs

There are several types of AMIs you can choose from:

| Type                 | Description                                           |
|----------------------|-------------------------------------------------------|
| **AWS-provided**     | Maintained by AWS (e.g., Amazon Linux, Ubuntu, etc.) |
| **Marketplace AMIs** | Pre-configured images provided by vendors             |
| **Community AMIs**   | Shared by other AWS users (free or public use)        |
| **Custom AMIs**      | Created by you, tailored to your needs                |

## 4.How to Select an AMI

When choosing an AMI, consider:

- **Operating System**: Linux or Windows?
- **Region Availability**: Not all AMIs are available in all regions.
- **Architecture**: 64-bit vs. 32-bit, ARM vs. x86.
- **EBS or Instance Store-backed**: EBS allows persistent storage.
- **Software Requirements**: Some AMIs come with pre-installed software.

## 5.Introduction to EC2 Instances

### What is EC2?
**Amazon EC2 (Elastic Compute Cloud)** is a web service that provides secure, resizable compute capacity in the cloud. You can think of it as a virtual machine in the cloud.

### Key Features:
- Choose instance types based on CPU, memory, storage, and networking.
- Integrate with AMIs to control what software is installed.
- Scalable: Launch one or thousands of instances on demand.


