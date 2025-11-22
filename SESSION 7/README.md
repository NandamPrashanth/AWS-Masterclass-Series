# SESSION 7


## What is IAM?

**Identity and Access Management (IAM)** is AWS’s security layer that controls:
- **Who** can access AWS
- **What** they can access
- **How** they can access it

---

## IAM Core Components

### 👤 Users
IAM Users represent **individual people or applications** that need access to AWS.  
Users can have:
- Console login (username/password)
- Programmatic access (access key/secret key)

---

### 👥 Groups
Groups allow you to bundle users together and assign policies once.  
Example:
- `Developers` group → EC2 Full Access  
- `Viewers` group → Read-only permissions  

All users inside the group inherit those permissions.

---

### 📜 Policies
Policies are **JSON documents** that define what actions are allowed or denied.

A typical policy contains:
- **Effect**: Allow or Deny
- **Action**: What actions can be performed
- **Resource**: Where the action applies

## IAM Roles

An **IAM Role** is a temporary and flexible identity in AWS that provides permissions **without** needing a username, password, or access keys.

Roles are used when:
- AWS **services** need permissions  
- You need **temporary access**  
- You want **cross-account access**  
- Applications want secure, short-lived credentials  

Roles are more secure than IAM Users because they use **temporary STS credentials** that automatically expire and rotate.

---

## 🔥 Why Use a Role?

- IAM Users = permanent identity  
- IAM Roles = temporary, assumable identity  

Roles are ideal when:
- EC2 instances need access to S3  
- Lambda functions need to access DynamoDB  
- An engineer needs temporary admin access  
- One AWS account needs access to another account’s resources  

No passwords. No long-term access keys. Just secure, short-lived access.

---

## Creating an IAM Role – Step-by-Step

### **1. Choose Trusted Entity**
Select who or what will **assume** the role:
- AWS Service (EC2, Lambda, ECS, etc.)
- Another AWS Account
- Web Identity / OIDC provider
- SAML provider

### **2. Attach Permissions**
Attach the policies that define what the role can do.

Example:  
Attach `AmazonS3ReadOnlyAccess` so EC2 can read from S3.

### **3. Name the Role**
Give a clear name like:
- `EC2-S3-ReadOnly`

---

## 🖥️ Example: EC2 Role to Access S3

This is one of the most common IAM tasks.

### Steps:
1. IAM → Roles → **Create Role**
2. Trusted entity → **AWS Service**
3. Choose **EC2**
4. Attach policy → `AmazonS3ReadOnlyAccess`
Now, inside the EC2 instance, you can run:

```bash
aws s3 ls





