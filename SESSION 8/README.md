# SESSION 8

## What is Amazon S3?

**Amazon S3 (Simple Storage Service)** is an object storage service from AWS that lets you store and retrieve any amount of data at any time, from anywhere on the web.

**Key points:**

- **Object storage** (not block, not file)
- Virtually **unlimited storage**
- Designed for **11 nines of durability** (99.999999999%)
- Pay-as-you-go: you pay for **storage, requests, and data transfer**
- Used heavily for **backups, logs, static websites, data lakes, and CI/CD artifacts**

## Key Concepts & Terminology

### Buckets

- A **bucket** is a **container for objects** in S3.
  
**- Bucket names:**
  - Must be **globally unique** across all AWS accounts.
  - Must follow **DNS-compliant naming** rules (lowercase, no spaces, etc.).
  - Buckets are created in a specific **AWS Region**, e.g. `ap-south-1` (Mumbai).

### Objects & Keys

- An **object** is the actual data you store in S3.
- Each object consists of:
  - **Object data** (your file content)
  - **Metadata** (key–value pairs about the object)
  - **Key** (the full path/name inside the bucket)
  - Optional: **Version ID** (if versioning is enabled)
- The **key** is like the full file path:
  - Example: `projects/dev/app1/logs/2025-11-24.log`

### Regions

- When you create a bucket, you **must pick a Region**.
- Data is stored and replicated **within that Region** (across multiple AZs).
- Choose Region based on:
  - **Latency** to users
  - **Cost**
  - **Compliance / data residency**

### Storage Classes

S3 offers multiple **storage classes** optimized for different access patterns and cost profiles. 

**Examples:**

- **S3 Standard**  
  - For **frequently accessed** data  
  - Low latency, high throughput  

- **S3 Intelligent-Tiering**  
  - Automatically moves data between frequent and infrequent access tiers  
  - Good when access patterns are **unknown or changing**

- **S3 Standard-IA (Infrequent Access)**  
  - Lower cost than Standard  
  - For data that is **accessed less often**, but needs **fast access** when required  
  - Has a **retrieval cost**

- **S3 One Zone-IA**  
  - Like Standard-IA but stored in **a single AZ**  
  - Cheaper, but less resilient than multi-AZ  

- **S3 Glacier / Glacier Instant Retrieval / Glacier Deep Archive**  
  - For **archive data**  
  - Very low storage cost, higher **retrieval time/cost**

You can **move objects between classes** manually or via **Lifecycle rules**.


### Durability vs Availability

- **Durability**: Probability that your data **will not be lost**.
  - S3 is designed for **99.999999999% durability**.
- **Availability**: Percentage of time S3 is **accessible**.
  - S3 Standard targets **99.99% availability**.
  - 

## Security & Access Control

### IAM Policies

- **IAM (Identity and Access Management)** manages **who** can access **what**.
- IAM policies are **JSON documents** attached to:
  - Users
  - Groups
  - Roles
- They specify:
  - **Effect**: `Allow` or `Deny`
  - **Action**: e.g. `s3:PutObject`, `s3:ListBucket`
  - **Resource**: e.g. `arn:aws:s3:::my-bucket/*`

IAM policies are usually attached to **users/roles**, not buckets.


### Bucket Policies

- A **bucket policy** is attached **directly to a bucket**.
- Used to **control access at bucket level**, e.g.:
  - Allow another AWS account to access the bucket
  - Allow public read for a static website
  - Enforce TLS-only access
  

### Block Public Access

- AWS provides **“Block Public Access”** settings at:
  - Account level
  - Bucket level
- This helps **prevent accidental public exposure** of S3 data.
- Typically, keep **Block Public Access = ON**  
  Only disable highly selectively for **static websites** or specific use cases.
  

## Data Management Features

### Versioning

- When **versioning** is enabled on a bucket:
  - Each object has multiple versions (with **version IDs**).
  - `DELETE` does not remove data immediately; it creates a **delete marker**.
  - You can **restore older versions**.
- Used for:
  - **Accidental deletions/overwrites protection**
  - Compliance and auditing


### Replication (CRR & SRR)

- **Cross-Region Replication (CRR)**:
  - Replicates objects between **buckets in different Regions**.
  - Useful for **disaster recovery**, **latency**, and **compliance**.

- **Same-Region Replication (SRR)**:
  - Replicates between **buckets in the same Region**.
  - Useful for data protection, multi-account setups.

Replication is **not retroactive** by default; it applies from the time you enable it (unless you choose to replicate existing objects).

