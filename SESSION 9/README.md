# SESSION 9

# OSI Model – Complete Overview

## What is the OSI Model?

The **OSI Model (Open Systems Interconnection Model)** is a conceptual framework that explains **how data travels across a network**.  
It breaks the network communication process into **7 distinct layers**, each responsible for a specific function in data transmission.

----------------------------------------------------------------------------

## The 7 Layers of the OSI Model

1. **Physical Layer**  
   Handles the physical medium: cables, signals, electrical pulses, bits.

2. **Data Link Layer**  
   Responsible for MAC addressing, frames, and switch operations.

3. **Network Layer**  
   Handles IP addressing, routing, and logical path selection.

4. **Transport Layer**  
   Ensures end-to-end delivery using TCP/UDP, flow control, and segmentation.

5. **Session Layer**  
   Manages sessions between communicating devices or applications.

6. **Presentation Layer**  
   Handles data formatting, encryption, decryption, and compression.

7. **Application Layer**  
   The layer closest to users; contains protocols like HTTP, FTP, DNS, SMTP.

---

It was created by the **International Organization for Standardization (ISO)** in the 1980s.

---

## How Do We Use the OSI Model Today?

Even though modern networking uses the **TCP/IP model**, the OSI model is still extremely useful for:

### ✔ Troubleshooting  
Engineers isolate issues by checking problems layer by layer.  
Examples:
- No internet? → Possibly Layer 1 (cables)  
- No IP? → Layer 3 issue  
- Website not loading? → Layer 7 (HTTP/DNS)

### ✔ Understanding Devices  
- Hubs → Layer 1  
- Switches → Layer 2  
- Routers → Layer 3  
- Firewalls → Layer 3/4/7 (depending on type)

### ✔ Designing Networks  
It provides a modular, organized approach to building network systems.

---

## Why Is the OSI Model Useful?

### ✔ 1. Common Language  
Helps engineers and companies understand each other.

### ✔ 2. Modularity  
Each layer is responsible for a specific task, making networks predictable and organized.

### ✔ 3. Vendor Compatibility  
Devices from different manufacturers can work together.

### ✔ 4. Simpler Troubleshooting  
By isolating issues at specific layers.

---

## 🔗 Are OSI Layers Interconnected?

### ✔ Yes, they depend on each other.  

Each layer passes data to the one above and below it.

Example data flow:
Layer 7 → Layer 6 → Layer 5 → Layer 4 → Layer 3 → Layer 2 → Layer 1


On the receiving end, the layers reverse the process.

### ✔ Do different applications use different layers?

Yes:
- Web browsers use **Layer 7 (HTTP)**  
- Voice/video apps use **Layer 4 (UDP)**  
- Routers operate at **Layer 3**  

But every application **ultimately relies on all layers working together** for end-to-end communication.

---
<img width="1024" height="838" alt="OSI-model-vs-TCPIP-model-1024x838" src="https://github.com/user-attachments/assets/7d34c146-726b-4b2f-98aa-64d42474d2ca" />

![Shutterstock_2160088225-2](https://github.com/user-attachments/assets/4ad2ad47-da91-4cee-9bdc-615a18c77169)


