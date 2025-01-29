# IP Addressing and Subnetting 🌐  

Welcome to this comprehensive guide on **IP Addressing and Subnetting**. This document will help you understand **how IP addresses work, the structure of IPv4 and IPv6, subnetting concepts, and how to divide networks efficiently**.  

---

## Table of Contents  
1. [What is an IP Address?](#what-is-an-ip-address)  
2. [IPv4 Addressing](#ipv4-addressing)  
3. [IPv6 Addressing](#ipv6-addressing)  
4. [Subnetting in IPv4](#subnetting-in-ipv4)  
5. [Subnet Mask and CIDR Notation](#subnet-mask-and-cidr-notation)  
6. [Subnetting Examples](#subnetting-examples)  
7. [Conclusion](#conclusion)  
8. [Author](#author)  

---

## What is an IP Address? 📜  

An **IP address (Internet Protocol address)** is a unique identifier assigned to each device connected to a network. It allows devices to **send and receive data** over the internet or a local network.  

### Types of IP Addresses  
- **Public IP**: Used to identify devices on the internet.  
- **Private IP**: Used within local networks (e.g., homes, offices).  
- **Static IP**: Manually assigned and does not change.  
- **Dynamic IP**: Assigned automatically by DHCP servers and may change over time.  

---

## IPv4 Addressing 🌍  

### 🔹 What is IPv4?  
IPv4 (Internet Protocol version 4) is the most widely used version of IP. It is a **32-bit address** written in **dotted decimal notation**:  

**Example:** `192.168.1.1`  

### 🔹 IPv4 Address Structure  
IPv4 addresses consist of **four octets** (each 8 bits), separated by dots. Each octet ranges from `0` to `255`:  

```
192. 168.  1.  1  
11000000.10101000.00000001.00000001 (Binary)
```

### 🔹 IPv4 Address Classes  
IPv4 addresses are divided into **five classes** (A, B, C, D, E):  

| Class | Starting Address | Ending Address | Default Subnet Mask | Usage |  
|-------|----------------|---------------|---------------------|--------|  
| **A** | 1.0.0.0        | 126.255.255.255 | 255.0.0.0          | Large networks |  
| **B** | 128.0.0.0      | 191.255.255.255 | 255.255.0.0        | Medium networks |  
| **C** | 192.0.0.0      | 223.255.255.255 | 255.255.255.0      | Small networks |  
| **D** | 224.0.0.0      | 239.255.255.255 | N/A                 | Multicasting |  
| **E** | 240.0.0.0      | 255.255.255.255 | N/A                 | Experimental |  

### 🔹 Private and Public IPv4 Addresses  
Certain IP ranges are **reserved for private use**:  

| Class | Private IP Range |  
|-------|-----------------|  
| **A** | 10.0.0.0 – 10.255.255.255 |  
| **B** | 172.16.0.0 – 172.31.255.255 |  
| **C** | 192.168.0.0 – 192.168.255.255 |  

💡 **Private IPs are not routable on the internet and require Network Address Translation (NAT) to connect to public networks.**  

---

## IPv6 Addressing 🔢  

### 🔹 What is IPv6?  
IPv6 (Internet Protocol version 6) was introduced to address **IPv4 exhaustion**. It uses **128-bit addresses**, represented in **hexadecimal**:  

**Example:** `2001:0db8:85a3:0000:0000:8a2e:0370:7334`  

### 🔹 IPv6 Features  
✅ **Larger Address Space** (340 undecillion addresses)  
✅ **No Need for NAT** (Each device can have a unique global IP)  
✅ **Built-in Security** (IPSec for encryption and authentication)  
✅ **Better Multicasting and QoS Support**  

### 🔹 IPv6 Address Types  
- **Unicast** – For a single device.  
- **Multicast** – For a group of devices.  
- **Anycast** – For the nearest device in a group.  

🔍 **Unlike IPv4, IPv6 does not use subnet masks but instead uses prefix lengths (e.g., `/64`).**  

---

## Subnetting in IPv4 📏  

### 🔹 What is Subnetting?  
Subnetting is the process of **dividing a larger network into smaller sub-networks (subnets)**. This improves efficiency and security by:  
- **Reducing network congestion**  
- **Optimizing IP address usage**  
- **Enhancing security and performance**  

### 🔹 Subnet Mask and CIDR Notation  
A **subnet mask** determines which portion of an IP address is the **network** and which part is the **host**.  

| Subnet Mask | CIDR Notation | Number of Hosts |  
|-------------|--------------|-----------------|  
| 255.0.0.0 | /8 | 16,777,214 |  
| 255.255.0.0 | /16 | 65,534 |  
| 255.255.255.0 | /24 | 254 |  

Example:  
- **IP Address:** `192.168.1.10`  
- **Subnet Mask:** `255.255.255.0` (or `/24`)  
- **Network Portion:** `192.168.1.0`  
- **Host Portion:** `10`  

🔹 **CIDR Notation (Classless Inter-Domain Routing)** represents subnet masks in **"/" format** (e.g., `/24` instead of `255.255.255.0`).  

---

## Subnetting Examples 🔢  

### Example 1: Creating 4 Subnets from a Class C Network  
- **Given:** `192.168.1.0/24`  
- **New Subnet Mask:** `255.255.255.192` (`/26`)  
- **Each Subnet Has:** `62 usable hosts`  

| Subnet | First IP | Last IP | Broadcast |  
|--------|---------|---------|-----------|  
| **1st** | 192.168.1.0 | 192.168.1.63 | 192.168.1.63 |  
| **2nd** | 192.168.1.64 | 192.168.1.127 | 192.168.1.127 |  
| **3rd** | 192.168.1.128 | 192.168.1.191 | 192.168.1.191 |  
| **4th** | 192.168.1.192 | 192.168.1.255 | 192.168.1.255 |  

### Example 2: Finding the Subnet for an IP  
- **Given IP:** `10.0.5.34/16`  
- **Subnet Mask:** `255.255.0.0`  
- **Network Address:** `10.0.0.0`  
- **Broadcast Address:** `10.0.255.255`  

🔹 **Use the AND operation between IP and Subnet Mask to find the network address.**  

---

## Conclusion ✅  

IP addressing and subnetting are **fundamental networking concepts** that allow for efficient data routing and resource allocation. IPv6 is gradually replacing IPv4 due to its expanded address space and security features. Understanding these topics is crucial for **network engineers, IT professionals, and cybersecurity experts**.  

---

## Author ✍️  
This README was written by **[Mahan Rahmani](https://github.com/Mahan-Rahmani)**. If you found this helpful, feel free to reach out! 🚀  

---

Let me know if you need further explanations or modifications! 🚀