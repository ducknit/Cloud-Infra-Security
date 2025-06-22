# R&D Report: Azure Networking Concepts

## Title
**Working of NSG & ASG, IP Management, and Security Controls in Azure**


---

## Executive Summary

This document explores the core Azure networking components essential for managing VM communication, controlling traffic, assigning IPs, and enforcing security. Key focus areas include NSG (Network Security Groups), ASG (Application Security Groups), Public IP types, static IP allocation, service tags, and network interfaces. These components form the backbone of a scalable, secure, and well-architected Azure environment.

---

## Key Insights

- **NSG controls traffic** via rules on NICs and subnets.
- **ASG allows grouping of VMs** logically to apply security rules at scale.
- **Static IPs prevent reassignment**, while **dynamic IPs** change on VM stop/start.
- **Service Tags simplify NSG rules** by referencing Azure services.
- Public IPs are used for **internet access**, and can be **associated or disassociated** with VMs as needed.

---

## Concepts Covered

- Network Security Groups (NSG)
- Application Security Groups (ASG)
- Public IP Types (Basic vs Standard, Static vs Dynamic)
- Service Tags
- IP Allocation (Static IP assignment to VMs)
- Network Interface (NIC) creation

---

## 1. Network Security Group (NSG)

- NSGs contain **inbound and outbound rules** that allow or deny traffic.
- Applied to **subnets or NICs**.
- Example rule: Allow RDP (TCP 3389) from specific IP.

### Deny Internet Access with NSG:
- Create a **deny outbound rule** to `Internet` with destination as `0.0.0.0/0`.
- Allow only private subnet access.

---

## 2. Application Security Group (ASG)

- ASGs group VMs logically (e.g., WebServerGroup, DBGroup).
- Used in **NSG rules** instead of IPs.
- Simplifies rule management.

Example:
```json
Source: WebServerASG
Destination: DBASG
Port: 1433
Action: Allow


---

## 3. Public IPs

### Types

- **Basic** (no zone resiliency, for dev/test)  
- **Standard** (secure by default, zone-redundant)

### Allocation

- **Dynamic:** Assigned at VM start; changes on stop.  
- **Static:** Assigned permanently until released.

### Use Case

- **Web Servers** often need Static IPs for DNS and firewall whitelisting.

---

## 4. Allocate Static IP to VMs

**Steps:**

1. Go to **VM → Networking → Network Interface → IP Configuration**  
2. Click on **IP config name**  
3. Change Assignment to **Static**  
4. Assign a private IP

---

## 5. Create a Network Security Group (NSG)

1. Azure Portal → Create Resource → Network Security Group  
2. Add **inbound rule**: Allow SSH (port 22), RDP (port 3389), or HTTP (80)  
3. Associate with subnet or NIC

---

## 6. Create Public IP

1. Azure Portal → Create Resource → Public IP Address  
2. Choose **IPv4**, **Standard**, and **Static**  
3. Name it (e.g., `MyPublicIP`)

---

## 7. Associate / De-associate Public IP with VM

### Associate

- Go to **VM → Networking → NIC → IP Configurations**  
- Select Public IP and choose an existing one or create a new one

### De-associate

- Set Public IP to `"None"`

---

## 8. Creating Network Interface

1. Azure Portal → Create Resource → Network Interface  
2. Choose VNet, subnet, and static private IP (if needed)  
3. Attach to VM during or after VM creation

---

## Conclusion

Azure provides powerful networking tools to enforce **granular security**, **custom IP management**, and **high availability**. By using NSGs, ASGs, public IP configurations, and NIC controls, organizations can create secure and flexible architectures tailored to specific workloads.

---

## Recommendations

- Use **NSG + ASG** combo for scalable and secure VM communication.  
- Always assign **Static Private IPs** to key VMs (Web, DB).  
- Deny internet access to back-end tiers using **custom NSG rules**.  
- Use **Standard Static Public IPs** for production exposure.  
- Keep IP and NIC configurations documented and monitored via **Azure Network Watcher**.

