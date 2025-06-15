# R&D Report

## Title
**Creating VNets, Subnets, VMs, and Peering in Azure (Southeast Asia)**

---

## Introduction

This document guides you through:
- Setting up **two VNets (VNet1 and VNet2)** in **Southeast Asia**
- Configuring **subnets**
- Deploying **Windows and Linux VMs**
- Establishing **VNet Peering**
- Verifying **network connectivity** across subnets and VNets

---

## Prerequisites

- An **active Azure Subscription**
- Access to **Azure Portal**
- **Southeast Asia** selected as the deployment region
- Small VM sizes (B1s) for testing
- Basic understanding of **networking concepts**

---

## 1️⃣ Create VNet1 in Southeast Asia

- **Go to Azure Portal → Create a resource → Virtual Network**
- **Name:** `VNet1`
- **Address space:** `10.0.0.0/16`
- **Location:** Southeast Asia
- **Subnet1:** `10.0.1.0/24`
- **Subnet2:** `10.0.2.0/24`

![Create VNet1](https://example.com/screenshot_vnet1.png)

---

## 2️⃣ Deploy Windows VM in Subnet1 of VNet1

- **Create a VM**
- **Name:** `WinVM`
- **Size:** `B1s`
- **Image:** Windows Server
- **VNet:** VNet1
- **Subset:** 10.0.1.0/24

![Creating Windows VM](https://example.com/screenshot_windows_vm.png)

---

## 3️⃣ Deploy Linux VM in Subnet2 of VNet1

- **Create a VM**
- **Name:** `LinuxVM`
- **Size:** `B1s`
- **Image:** Ubuntu
- **VNet:** VNet1
- **Subset:** 10.0.2.0/24

![Creating Linux VM](https://example.com/screenshot_linux_vm.png)

---

## 4️⃣ Validate Communication Between VMs in VNet1

- **Login into Windows VM**
- **Open cmd or PowerShell**
- **Ping Linux VM's private IP (10.0.2.x)**  
- **ping 10.0.2.4

- **Login into Linux VM (SSH)**
- **Ping Windows VM's private IP (10.0.1.x)**  

- **ping 10.0.1.4


✅ Successful pings validate **intra-vnet communication**.

---

## 5️⃣ Create VNet2 in Southeast Asia

- **Create another VNet:** `VNet2`
- **Address space:** `10.1.0.0/16`
- **Subset:** `10.1.1.0/24`

![Creating VNet2](https://example.com/screenshot_vnet2.png)

---

## 6️⃣ Deploy Linux VM in VNet2's Subnet

- **Create VM:** `LinuxVM2`
- **Size:** `B1s`
- **Image:** Ubuntu
- **VNet:** VNet2
- **Subset:** 10.1.1.0/24

![Creating Linux VM in VNet2](https://example.com/screenshot_vnet2_linux.png)

---

## 7️⃣ Establish VNet Peering Between VNet1 and VNet2

- **Go to VNet1 → Peerings → Add peering**
- **Peering name:** `VNet1ToVNet2`
- **Remote VNet:** `VNet2`
- Repeat from VNet2 side: `VNet2ToVNet1`

![Peering configuration](https://example.com/screenshot_peering.png)

---

## 8️⃣ Validate Communication Between VNets

- **SSH into Linux VM in VNet2**
- **Ping Linux VM in VNet1 (10.0.2.4)**

- **ping 10.0.2.4


✅ Successful pings validate **VNet peering is working**.

---

## Summary

✅ We successfully:
- Created 2 VNets in Southeast Asia
- Launched Windows and Linux VMs in their subnets
- Established peering between VNets
- Verified communication across subnets and VNets

---

## Conclusion:

✅ **CIDR block** lets you efficiently allocate IP space.  
✅ **Subnets** help you segregate workloads and control resources.  
✅ **VNet Peering** lets you connect VNets securely and efficiently, whether in the same or different regions.  
✅ Proper planning of **address spaces and peering** is key to designing scalable, flexible, and multiregion Azure networks.
