# DDoS Attack Guide

**Author:** Karthik S Sathyan  
**Date:** October 2024  
**Project Description:** This guide provides an in-depth understanding of Distributed Denial of Service (DDoS) attacks, their various forms, how they impact different layers of the OSI model, and the strategies used to mitigate these attacks. It highlights the different traffic types attackers exploit, the technical details of DDoS attacks, and the tools available for defense.

---

## Table of Contents

- [Introduction](#introduction)
- [DDoS Attacks by OSI Layer](#ddos-attacks-by-osi-layer)
  - [Application Layer (Layer 7)](#application-layer-layer-7)
  - [Presentation Layer (Layer 6)](#presentation-layer-layer-6)
  - [Session Layer (Layer 5)](#session-layer-layer-5)
  - [Transport Layer (Layer 4)](#transport-layer-layer-4)
  - [Network Layer (Layer 3)](#network-layer-layer-3)
  - [Data Link Layer (Layer 2)](#data-link-layer-layer-2)
  - [Physical Layer (Layer 1)](#physical-layer-layer-1)
- [DDoS Traffic Types](#ddos-traffic-types)
  - [HTTP GET and POST Floods](#http-get-and-post-floods)
  - [SYN Flood](#syn-flood)
  - [UDP Flood](#udp-flood)
  - [ICMP Flood](#icmp-flood)
  - [MAC Flood](#mac-flood)
- [Mitigating DDoS Attacks](#mitigating-ddos-attacks)
  - [Infrastructure Defense](#infrastructure-defense)
  - [Application Layer Mitigation](#application-layer-mitigation)
  - [Rate Limiting](#rate-limiting)
- [Glossary](#glossary)
- [References](#references)

---

## Introduction

Distributed Denial of Service (DDoS) attacks have become one of the most common and disruptive types of cyberattacks, aimed at overwhelming a target's resources and rendering services unavailable. These attacks exploit vulnerabilities in different layers of the **OSI model**, impacting not only the network but also the application layer.

This guide explains the various types of DDoS attacks, highlights how they affect different OSI layers, and provides detailed mitigation strategies. It is designed for both cybersecurity professionals and organizations seeking to improve their defense against these attacks.

---

## DDoS Attacks by OSI Layer

### Application Layer (Layer 7)

- **Protocol**: HTTP, SMTP, FTP, POP3  
- **Attack Type**: HTTP GET/POST flood, which involves sending a large volume of GET/POST requests to exhaust server resources.
- **Impact**: Exhausts resources like CPU and memory, making websites or web services unresponsive.
- **Mitigation**: **Application monitoring** and rate limiting can detect and stop malicious activity more effectively than traditional DDoS defenses.

### Presentation Layer (Layer 6)

- **Protocol**: Compression, Encryption (e.g., SSL/TLS)  
- **Attack Type**: SSL flooding attacks that exhaust server resources by forcing it to process heavy encryption workloads.
- **Impact**: Systems stop accepting secure connections or crash.
- **Mitigation**: Offload SSL processing to a separate infrastructure, inspect traffic at an **Application Delivery Platform (ADP)**, and re-encrypt traffic back to the origin infrastructure.

### Session Layer (Layer 5)

- **Protocol**: Logon/Logoff, Session Management  
- **Attack Type**: Exploiting flaws in session management protocols (e.g., Telnet DDoS).
- **Impact**: Prevents system administrators from managing network devices or systems.
- **Mitigation**: Apply patches to affected session-layer protocols and check for firmware updates from hardware vendors.

### Transport Layer (Layer 4)

- **Protocol**: TCP, UDP  
- **Attack Type**: SYN flood and UDP flood attacks overwhelm network bandwidth and device resources.
- **Impact**: Saturates network bandwidth or overloads network devices, rendering them incapable of processing legitimate requests.
- **Mitigation**: Use SYN cookies, rate-limit UDP traffic, and enable **blackholing** to protect other users and devices on the network.

### Network Layer (Layer 3)

- **Protocol**: IP, ICMP, ARP  
- **Attack Type**: ICMP flood attacks overload networks by flooding them with ICMP packets.
- **Impact**: Reduces available bandwidth and overloads network devices.
- **Mitigation**: Limit ICMP traffic and configure firewalls to block malicious ICMP packets.

### Data Link Layer (Layer 2)

- **Protocol**: Ethernet, MAC Addressing  
- **Attack Type**: MAC flooding attacks saturate network switches by sending a flood of MAC addresses.
- **Impact**: Causes network switches to fail or drop their routing tables, disrupting network traffic.
- **Mitigation**: Limit the number of MAC addresses a switch can learn, authenticate MAC addresses, and use filtering mechanisms.

### Physical Layer (Layer 1)

- **Protocol**: Physical cabling, network hardware  
- **Attack Type**: Physical damage or tampering with network cables and hardware components.
- **Impact**: Hardware components become unresponsive, leading to network downtime.
- **Mitigation**: Implement physical security measures such as access control, monitoring, and regular audits to protect critical hardware.

---

## DDoS Traffic Types

### HTTP GET and POST Floods

- **GET Flood**: Attackers send a large number of HTTP GET requests to the target server, overwhelming it with traffic.
- **POST Flood**: A similar attack but using POST requests, which can be even more resource-intensive due to the processing required by POST forms.
- **Mitigation**: Use **reverse proxies** and **web application firewalls (WAF)** to detect and block malicious traffic.

### SYN Flood

- **SYN Flood**: The attacker sends multiple SYN packets to initiate TCP connections but never completes the handshake, leaving the server overwhelmed with half-open connections.
- **Mitigation**: Enable **SYN cookies**, limit SYN rates, and configure routers to block malicious SYN floods.

### UDP Flood

- **UDP Flood**: Attackers send large amounts of UDP packets to random ports on the target, causing the server to respond to non-existent requests.
- **Mitigation**: Use **rate-limiting** for UDP traffic and configure firewalls to drop excessive UDP packets.

### ICMP Flood

- **ICMP Flood**: Attackers flood the network with ICMP requests (e.g., ping) to exhaust bandwidth and network device resources.
- **Mitigation**: Implement **ICMP rate-limiting** and configure firewalls to block unnecessary ICMP traffic.

### MAC Flood

- **MAC Flood**: Attackers send numerous packets with random MAC addresses, filling up the switch's memory and preventing legitimate network communication.
- **Mitigation**: Limit the number of MAC addresses learned on each switch port and apply **AAA authentication** to validate devices.

---

## Mitigating DDoS Attacks

### Infrastructure Defense

Deploy firewalls with **deep packet inspection (DPI)**, **intrusion detection systems (IDS)**, and **rate-limiting routers** to prevent large-scale DDoS attacks at the infrastructure level. These tools inspect traffic flows and filter out malicious data before it reaches critical network components.

### Application Layer Mitigation

For Layer 7 attacks, use **application monitoring** solutions to detect anomalies in HTTP requests, SSL processing, or database access. By identifying irregular patterns, these solutions can block attacks at the application level without affecting legitimate users.

### Rate Limiting

Rate-limiting policies, especially on routers and firewalls, are essential for protecting against volumetric DDoS attacks. Rate limiting ensures that no single IP or session can overwhelm the network with excessive traffic.

---

## Glossary

- **Denial of Service (DoS)**: An attack that makes a system or network resource unavailable to its users.
- **Distributed Denial of Service (DDoS)**: A DoS attack that uses multiple compromised systems to flood the target with traffic.
- **SYN Cookie**: A technique used to prevent SYN flood attacks by storing partial TCP handshake data in the initial SYN packet.
- **Reverse Proxy**: A server that sits between client devices and servers, forwarding client requests to the appropriate server.
- **Rate Limiting**: A technique used to control the amount of incoming traffic by limiting the number of requests allowed during a given time frame.

---

## References

- [CISA - DDoS Quick Guide](https://www.cisa.gov/)
- [OWASP - Layer 7 DDoS](https://www.owasp.org/)
- [Juniper Networks - Protecting the Network from DDoS](https://www.juniper.net/)
