# SESSION 16

# 📘 AWS Session Manager

## ✅ What is AWS Session Manager?

AWS Session Manager is a capability of AWS Systems Manager that allows secure remote access to Amazon EC2 instances without using SSH keys, bastion hosts, or opening inbound ports.

You can connect to servers directly from:

- AWS Management Console
- AWS CLI
- AWS SDK

Supported targets include:

- Linux EC2 Instances
- Windows EC2 Instances
- On-premises servers (Hybrid environments)

---

## ✅ Why is Session Manager Used?

Traditional server access methods require:

- SSH Keys
- RDP connections
- Public IP addresses
- Open inbound ports (22 or 3389)

These increase security risks.

Session Manager improves security by:

- Eliminating public IP requirements.
- Removing inbound port exposure.
- Using IAM-based authentication.
- Supporting logging and auditing.

### Benefits

- Secure access without SSH keys.
- Centralized access control using IAM.
- Session logging via CloudWatch or S3.
- Reduced operational overhead.

---

## ✅ When to Use Session Manager?

Use Session Manager when:

- Secure EC2 access is required.
- You want to avoid managing SSH keys.
- Production environments must not expose inbound ports.
- Centralized audit logging is required.
- Following Zero Trust Security principles.

### Example Use Cases

- Production server troubleshooting.
- Enterprise environments.
- DevOps remote debugging.
- Hybrid infrastructure management.

---

## ✅ Requirements

To use Session Manager:

- EC2 instance must have SSM Agent installed.
- IAM Role with SSM permissions must be attached.
- Internet Gateway, NAT Gateway, or VPC Endpoint connectivity required.

---

## ✅ Basic Workflow

1. Launch an EC2 instance.
2. Attach IAM Role with Systems Manager permissions.
3. Open AWS Systems Manager Console.
4. Navigate to Session Manager.
5. Start Session.

No SSH key or inbound rule required.

---

# 🌍 AWS CloudFront (CDN)

## ✅ What is AWS CloudFront?

AWS CloudFront is a Content Delivery Network (CDN) service that delivers websites, APIs, videos, and applications globally with low latency and high transfer speeds.

CloudFront uses AWS global Edge Locations to cache content closer to users.

Users receive content from the nearest Edge Location instead of the origin server.

---

## ✅ Why is CloudFront Used?

Direct server access may cause:

- High latency.
- Slow website performance.
- Increased origin server load.

CloudFront solves this by:

- Caching frequently accessed content.
- Serving users from nearby locations.
- Reducing origin infrastructure load.

### Benefits

- Faster website loading.
- Improved global performance.
- DDoS protection with AWS Shield.
- HTTPS encryption support.
- Reduced backend server load.

---

## ✅ When to Use CloudFront?

Use CloudFront when:

- Hosting static websites.
- Delivering images or videos worldwide.
- Accelerating APIs.
- Streaming media content.
- Protecting web applications behind CDN.

### Example Use Cases

- Static websites hosted on S3.
- Media streaming platforms.
- SaaS applications.
- E-commerce websites.

---

## ✅ Key Components

### Origin

The backend source where original content is stored.

Examples:

- Amazon S3 Bucket
- EC2 Instance
- Application Load Balancer
- External Web Server

---

### Edge Locations

AWS data centers that cache content closer to users for faster delivery.

---

### Distribution

Configuration that connects:

Users → CloudFront → Origin

---

## ✅ Basic Workflow

1. User requests a website or content.
2. Request goes to nearest Edge Location.
3. If cached → delivered immediately.
4. If not cached → fetched from origin.
5. Content cached for future requests.

---
