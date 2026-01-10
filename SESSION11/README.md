# SESSION 11

# AWS VPC Peering

## 📌 What is AWS VPC Peering?

**VPC Peering** is a networking connection between **two VPCs** that allows them to **communicate privately** using **private IP addresses**, as if they are part of the same network.

- Traffic does **not** go over the public internet
- Communication happens through the **AWS global private network**

---

## 🧠 Why Do We Need VPC Peering?

In real-world DevOps and cloud environments:

- Multiple teams use **separate VPCs**
- Applications follow **microservices architecture**
- Databases are isolated in different VPCs
- Dev / QA / Prod environments must be separated

## VPC Peering enables:
- Secure communication between VPCs
- Sharing common services (DB, LDAP, monitoring)
- Low latency and high bandwidth
- Reduced cost compared to public access

---

## 🏗️ VPC Peering Architecture

### Example Use Case

| VPC | Purpose |
|----|--------|
| VPC-A | Web / Application Tier |
| VPC-B | Database / Backend Tier |

**Requirement:**  
Web servers in **VPC-A** must securely connect to a database in **VPC-B** using private IPs.

---

## 🔑 Key Characteristics of VPC Peering

- ✔ Private IP communication
- ✔ High bandwidth, low latency
- ✔ Works across AWS accounts and regions
- ❌ No transitive routing
- ❌ CIDR blocks must not overlap

---
## 🛠️ AWS VPC Peering – STEPS TO CREATE

1. Create **VPC-A** with CIDR `10.0.0.0/16`.
2. Create **VPC-B** with CIDR `192.168.0.0/16` (CIDR must not overlap).
3. Create required **subnets** in both VPCs.
4. Launch **EC2 instances** in each VPC for connectivity testing.
5. Create a **VPC Peering Connection** from VPC-A to VPC-B.
6. Accept the **peering request** in VPC-B.
7. Update **VPC-A route table** to route `192.168.0.0/16` via peering connection.
8. Update **VPC-B route table** to route `10.0.0.0/16` via peering connection.
9. Configure **Security Groups** to allow required traffic between VPC CIDR ranges.
10. Test connectivity using **private IP addresses** (ping, telnet, curl).
