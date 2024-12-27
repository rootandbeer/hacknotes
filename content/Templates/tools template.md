---
tool: "Nmap"
category: "Recon"
tags: [tool/recon, networking]
date: 2024-12-15
---
# Nmap
**Purpose**: Network scanning and service discovery.

## Common Commands
```bash
nmap -A -T4 -v target_ip
nmap -sV --script vuln target_ip
```

## Notes

- Use `-Pn` for stealth scans.
- Combine with Metasploit for follow-up exploitation.