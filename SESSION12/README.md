# SESSION 12
# Amazon Route 53

## Introduction
Amazon Route 53 is a **highly available, scalable, and fully managed Domain Name System (DNS) service** provided by Amazon Web Services (AWS). It is used to translate **human-readable domain names** (like `www.example.com`) into **machine-readable IP addresses** (like `192.0.2.1`) and route end-user traffic efficiently and reliably.

The name **Route 53** comes from **port 53**, the standard port used by DNS services over TCP and UDP.

---

## 🌐 Why DNS is Important
Computers communicate using IP addresses, but humans prefer names.

```text
User types: www.example.com
DNS resolves: 203.0.113.10
Browser connects to server
````

Without DNS:

* Users must remember IP addresses
* Applications would not scale globally
* High availability would be difficult

Route 53 solves this by providing:

* Fast DNS resolution
* Global traffic routing
* Fault tolerance

---

## 🧠 Key Features of Route 53

* Domain registration and management
* Public and private DNS hosting
* Multiple traffic routing policies
* Built-in health checks and failover
* Integration with AWS services
* Hybrid cloud DNS support
* High availability backed by AWS global infrastructure

---

## 🏗️ Core Components of Amazon Route 53

---

## Domain Registration

Route 53 allows you to:

* Register new domain names
* Transfer existing domains from other registrars
* Manage domain lifecycle (renewal, expiration)

### Supported Domains

Examples:

```text
.com
.in
.org
.net
.io
.dev
```

AWS automatically:

* Assigns Name Servers (NS)
* Creates SOA (Start of Authority) records

---

## Hosted Zones

A **Hosted Zone** is a container for DNS records for a domain.

### Types of Hosted Zones

---

### 🔹 Public Hosted Zone

* Resolves DNS queries from the internet
* Used for public websites and applications

📌 Example:

```text
example.com
www.example.com
api.example.com
```

---

### 🔹 Private Hosted Zone

* Resolves DNS queries **only inside a VPC**
* Used for internal applications and microservices

📌 Example:

```text
db.internal.example.com
service.internal.example.com
```

Private hosted zones can be associated with:

* One or multiple VPCs
* Same or different AWS accounts

---

## DNS Record Types

### Common DNS Records

| Record Type | Description                            |
| ----------- | -------------------------------------- |
| A           | Maps domain name to IPv4 address       |
| AAAA        | Maps domain name to IPv6 address       |
| CNAME       | Alias to another domain name           |
| Alias       | AWS-specific alternative to CNAME      |
| MX          | Mail exchange servers                  |
| TXT         | Text records for verification/security |
| NS          | Name servers for the domain            |
| SOA         | Start of authority record              |
| PTR         | Reverse DNS lookup                     |
| SRV         | Service discovery                      |

---

### 🔍 CNAME vs Alias Record (Important for Interviews)

| Feature                  | CNAME          | Alias         |
| ------------------------ | -------------- | ------------- |
| Works with AWS resources | ❌              | ✅             |
| Supports root domain     | ❌              | ✅             |
| Extra cost               | DNS query cost | No extra cost |
| AWS recommended          | ❌              | ✅             |

📌 Alias records can point to:

* Application Load Balancer
* Network Load Balancer
* CloudFront
* S3 static websites
* API Gateway

---

## Routing Policies in Route 53

Routing policies control **how Route 53 responds to DNS queries**.

---

### Simple Routing

* Default routing
* Single resource
* No health checks

📌 Use case:

```text
example.com → Single EC2 instance
```

---

### Weighted Routing

* Distributes traffic based on percentages

📌 Example:

```text
Version A → 80%
Version B → 20%
```

Use cases:

* A/B testing
* Canary deployments
* Gradual rollouts

---

### Latency-Based Routing

* Routes traffic to the **lowest latency region**
* Improves performance for global users

📌 Example:

```text
US users → us-east-1
India users → ap-south-1
```

---

### Failover Routing

* Active–Passive architecture
* Uses health checks

📌 Example:

```text
Primary → ALB (Healthy)
Secondary → Backup ALB
```

If the primary fails, traffic is automatically routed to the secondary.

---

---

## Health Checks

Route 53 health checks monitor endpoint health and enable failover.

### Health Check Types

* HTTP
* HTTPS
* TCP
* CloudWatch alarm-based

### Health Check Features

* 30-second or 10-second intervals
* Multiple check locations
* Automatic DNS failover

---

## Route 53 and AWS Integration

| AWS Service | Usage                   |
| ----------- | ----------------------- |
| EC2         | Direct DNS mapping      |
| ALB / NLB   | Alias routing           |
| CloudFront  | Global content delivery |
| S3          | Static website hosting  |
| API Gateway | API routing             |
| EKS         | Service discovery       |
| VPC         | Internal DNS            |

---

## Route 53 Architecture Example

```text
User
 ↓
Route 53
 ↓
CloudFront
 ↓
Application Load Balancer
 ↓
EC2 / EKS
```
