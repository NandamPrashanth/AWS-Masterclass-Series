# SESSION 10

## What is a Load Balancer?

A **Load Balancer** is a component that sits **between users and servers** and distributes incoming traffic across multiple backend servers.

**Goals of a load balancer:**

- ✅ Improve **availability** – if one server fails, others can still serve traffic.  
- ✅ Improve **scalability** – you can add more servers behind the load balancer.  
- ✅ Improve **security** & **abstraction** – users hit one public endpoint instead of many servers.

---

## AWS Elastic Load Balancing (ELB)

In AWS, the service that provides load balancers is called **Elastic Load Balancing (ELB)**.

### Main Types of Load Balancers

1. ### Application Load Balancer (ALB)
   - Operates at **Layer 7 (HTTP/HTTPS)**.
   - Can inspect HTTP requests (URLs, headers, hostnames).
   - Best for **web applications**.

2. ### Network Load Balancer (NLB)
   - Operates at **Layer 4 (TCP/UDP)**.
   - Designed for **high performance** and **low latency**.
   - Best for:
     - Non-HTTP protocols
     - Very high traffic or real-time systems

3. ### Gateway Load Balancer (GWLB) (Advanced – optional)
   - Used to deploy **third-party security appliances** (e.g., firewalls) at scale.


## Key Concepts

When working with AWS Load Balancers, remember these key pieces:

### Targets
These are the **actual resources** that receive traffic, such as:

- EC2 instances
- IP addresses
- Lambda functions (for ALB)

---

### Target Group

A **Target Group** is a **group of targets**.

- The load balancer sends traffic to the **target group**, not directly to instances.
- You can have:
  - **One load balancer → multiple target groups**
  - Each target group can have its own **health checks** and **routing rules**.

**Health checks** are used to:
- Regularly ping targets (e.g., `/health` endpoint)
- Mark them as **healthy** or **unhealthy**
- Ensure traffic only goes to **healthy** targets

---

### Listeners

A **Listener** defines:

- **Protocol** (HTTP / HTTPS / TCP)
- **Port** (e.g., 80, 443)

Example:
- An ALB may have:
  - `HTTP : 80` listener
  - `HTTPS : 443` listener

Each listener can have one or more **rules** to decide how the traffic is routed.

---

### Listener Rules

Rules define **how** requests are routed:

- Based on **URL path**  
  `/app1/*` → Target Group 1  
  `/app2/*` → Target Group 2

- Based on **host name**  
  `api.example.com` → API target group  
  `shop.example.com` → Shop target group

---

## Request Flow (What Actually Happens?)

Here is a simple view of how a request flows through an **Application Load Balancer**:

1. User enters `http://my-app.example.com` in their browser.
2. DNS resolves that name to the **load balancer’s address**.
3. The request reaches the **ALB listener** (e.g., HTTP on port 80).
4. The listener applies its **rules** and chooses a **target group**.
5. That target group selects a **healthy target** (e.g., EC2 instance).
6. The target processes the request and sends response back via the ALB to the user.

```text
Client → DNS → AWS ALB → Target Group → EC2 Instances
