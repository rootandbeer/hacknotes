---
ctf_platform: HackTheBox
difficulty: Medium
tags:
  - "#walkthrough/hackthebox"
date: 2024-12-15
---
# Ephemeral 2 Walkthrough
**Platform**: HackTheBox  
**Difficulty**: Medium  

## Steps
1. **Recon**: 
   ```bash
   nmap -A -T4 target_ip
	```

2. **Exploit Samba**:
    - Use Metasploit module: `exploit/linux/samba/is_known_pipename`.
3. **Privilege Escalation**:
    - Exploit `invalid-input.sh` in `/opt/scripts/`.