---
title: Nmap
description: 
draft: false
tags: 
date: 2024-10-18
---

Nmap (Network Mapper) is an open-source tool used for network discovery and security auditing. It identifies active devices on a network, determines open ports, and detects the services and their versions running on those ports. Additionally, Nmap can infer the operating system of a device based on its responses to specific probes. With its scripting engine, users can automate scanning tasks and customize their scans for specific needs. Overall, Nmap is essential for network administrators and security professionals to assess network security and configurations.


## Commands
Performs an aggressive scan of all TCP ports on the target IP to detect the operating system, service versions, and potential vulnerabilities using default Nmap scripts.
```bash
nmap -A -sC -p- <IP>
```

---
### Supporting Content