# AWS SESSION 4

## 1.Virtual Private Cloud (VPC)
A **VPC (Virtual Private Cloud)** is a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network you define.

### Key Components:
- CIDR block (e.g., 10.0.0.0/16)
- Subnets (public and private)
- Route Tables
- Internet Gateway / NAT Gateway
- Security Controls

---

## 2.Subnets
A **subnet** is a range of IP addresses in your VPC. Subnets allow you to divide your VPC into smaller network sections.

### Types:
- **Public Subnet**: Connected to the internet via an Internet Gateway.
- **Private Subnet**: Has no direct internet access.

## 3.Route Tables
A **Route Table** contains rules (routes) that determine where network traffic is directed.

### Why do we use them?
- Controls how traffic flows between subnets, to the internet, or to a VPN.
- Every subnet must be associated with a route table (explicitly or implicitly).

## 4.Internet Gateway (IGW)
An **Internet Gateway** is a horizontally scaled, redundant, and highly available VPC component that allows **communication between instances in your VPC and the internet.
**

### Why do we use it?
- Required for any resource in the VPC that needs to access the internet directly (e.g., web servers).

- Must be attached to your VPC.
- Public subnet must route `0.0.0.0/0` traffic to the IGW.

## 5.NAT Gateway
A **NAT (Network Address Translation) Gateway** allows instances in a **private subnet** to connect to the internet **without exposing them** to inbound internet traffic.

- Enables secure internet access for private resources (e.g., to download OS updates or connect to AWS services).

## 6.Elastic IPs (EIP)
An **Elastic IP** (Public IP) is a static IPv4 address designed for dynamic cloud computing.

## 7.Security Groups
A **Security Group** acts as a virtual firewall for your EC2 instances to control inbound and outbound traffic.

### Example Rules:

**Inbound:**
| Type   | Protocol | Port | Source         |
|--------|----------|------|----------------|
| HTTP   | TCP      | 80   | 0.0.0.0/0      |
| SSH    | TCP      | 22   | Your IP only   |

**Outbound:**
| Type   | Protocol | Port | Destination     |
|--------|----------|------|-----------------|
| All    | All      | All  | 0.0.0.0/0       |

---

## Summary

| Component       | Purpose                                         |
|-----------------|-------------------------------------------------|
| VPC             | Virtual network in the cloud                    |
| Subnet          | Logical separation within a VPC                |
| Route Table     | Controls traffic routing                        |
| Internet Gateway| Enables internet access for public subnets      |
| NAT Gateway     | Internet access for private subnets (outbound)  |
| Elastic IP      | Static public IP                                |
| Security Groups | Firewall for instances                          |



