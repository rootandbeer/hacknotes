---
title: Hydra
description: 
draft: false
tags: 
date: 2024-10-19
---

**Bruteforce SSH password**
```bash
hydra -l <USERNAME> -P wordlist.txt ssh://<TARGET>
```

**Bruteforce SSH Username & Password
```bash
hydra -L wordlist.txt -P wordlist.txt ssh://<TARGET>
```