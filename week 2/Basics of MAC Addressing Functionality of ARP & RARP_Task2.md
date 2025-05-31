# Research Report

## Basics of MAC Addressing & Functionality of ARP & RARP


## Executive Summary

This report focuses on the essential roles of MAC addressing and the Address Resolution Protocols (ARP and RARP) within network communication. MAC addresses operate at the Data Link Layer and provide a hardware-based unique identity for network interfaces. Meanwhile, ARP and RARP bridge the gap between IP addresses and MAC addresses, allowing seamless communication in TCP/IP networks. Understanding these protocols is crucial for effective troubleshooting, address resolution, and efficient packet delivery across networks.

## Key Insights

**MAC Addressing Is Hardware-Based:**  
- MAC (Media Access Control) addresses are **unique 48-bit identifiers** assigned to network interfaces.  
- These addresses help deliver frames within the same local network segment.

**ARP Resolves IP to MAC:**  
- The **Address Resolution Protocol (ARP)** maps an IP address to a MAC address using broadcasting.  
- It’s essential for enabling communication in IPv4 networks.

**RARP Works in Reverse:**  
- The **Reverse Address Resolution Protocol (RARP)** maps MAC addresses back to IP addresses.  
- Though largely obsolete, RARP laid the groundwork for modern address discovery techniques.

**Data Link Layer Communication:**  
- MAC and ARP operate at **Layer 2** of the OSI model, enabling low-level, direct device communication.

## Recommendations

1. **Monitor ARP Tables and Cache:**  
   a. Regularly inspect ARP entries to detect spoofing or unexpected IP/MAC pairings.

2. **Use Static ARP Entries in Critical Systems:**  
   a. For servers or critical infrastructure, manually configure static ARP mappings to prevent spoofing.

3. **Implement ARP Security Measures:**  
   a. Use tools like Dynamic ARP Inspection (DAI) and Port Security on switches to mitigate ARP poisoning.

4. **Deprecate RARP Usage:**  
   a. Replace outdated RARP-based systems with DHCP or BOOTP.

5. **Document MAC and IP Mappings:**  
   a. Maintain updated records of hardware MAC addresses and corresponding IPs to support troubleshooting.

## Introduction

Every device in a network needs a way to be identified. While IP addresses provide a logical identity, MAC addresses offer a **permanent hardware identity**. The interplay between these two forms of addressing is managed by resolution protocols like ARP and RARP.

This report delves into **how MAC addresses function**, and how **ARP and RARP resolve or assign IP addresses based on MACs**. Despite their simplicity, these protocols are foundational to Layer 2/3 communication and are critical for any network professional to understand.

> “Without MAC addressing and ARP, IP-based communication would never leave the blueprint.”

## Significance

Understanding MAC addressing and ARP protocols allows organizations to:

● Troubleshoot network reachability issues.  
● Detect spoofing or man-in-the-middle attacks.  
● Improve address resolution and network transparency.  
● Manage and audit devices effectively across a LAN.  

## Implications

● Improper ARP management can lead to spoofing attacks.  
● MAC addresses help track devices in enterprise networks.  
● DHCP, ARP, and DNS together form the trio for endpoint discovery.  
● Awareness of ARP behavior is critical in VLANs and subnetting.

## MAC Addressing

**MAC (Media Access Control) Address**  
- A 48-bit address typically displayed as 6 hexadecimal octets (e.g., `00:1A:2B:3C:4D:5E`).  
- Assigned by manufacturers and globally unique.  
- Divided into:  
  - OUI (Organizationally Unique Identifier) – first 3 bytes  
  - Device Identifier – last 3 bytes  
- Operates at **Layer 2 (Data Link Layer)** of the OSI model.

**Example:**  

MAC: 00:0A:95:9D:68:16
OUI: 00:0A:95 (assigned to Apple Inc.)



## ARP (Address Resolution Protocol)

**Purpose:**  
- Resolves IPv4 addresses to MAC addresses.

**How it Works:**  
1. Host sends an **ARP Request** (broadcast) asking “Who has IP 192.168.1.10?”  
2. Device with that IP replies with an **ARP Reply** including its MAC address.  
3. The mapping is stored in an **ARP cache** for future use.

**Security Consideration:**  
- Vulnerable to ARP spoofing unless mitigated with security tools.

## RARP (Reverse Address Resolution Protocol)

**Purpose:**  
- Resolves MAC addresses to IP addresses (reverse of ARP).  

**Use Case:**  
- Legacy diskless systems that know only their MAC address used RARP to obtain an IP address.

**Obsolescence:**  
- Superseded by **BOOTP** and **DHCP**, which offer dynamic and richer configuration.

## Differences Between ARP and RARP

| Feature        | ARP                                | RARP                               |
|----------------|-------------------------------------|-------------------------------------|
| Function       | IP → MAC                           | MAC → IP                           |
| Direction      | Forward resolution                  | Reverse resolution                  |
| Usage Today    | Actively used in IPv4 networks      | Largely obsolete                    |
| Alternative    | N/A                                 | Replaced by DHCP/BOOTP             |

## Security Considerations

● **ARP Spoofing**: Attackers can impersonate IP-MAC mappings to intercept traffic.  
● **Solution**: Enable **Dynamic ARP Inspection (DAI)** on switches, use static ARP tables.  
● **MAC Filtering**: Used in Wi-Fi for basic access control, though not highly secure.  

## Conclusions

⬤ MAC addressing and ARP remain vital components of modern IPv4 networks.  
⬤ While RARP is outdated, understanding its function provides historical context.  
⬤ ARP resolution is automatic but can be exploited if not secured.  
⬤ Effective IP-MAC mapping helps maintain robust, secure, and efficient communication across network layers.  
⬤ Network engineers should be equipped to monitor, secure, and troubleshoot these foundational protocols.

