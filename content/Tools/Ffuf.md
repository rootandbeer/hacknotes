---
title: Fuff
description: 
draft: false
tags: 
date: 2024-10-18
---

**Fuzz file path's to look for `/etc/passwd`**

```bash
ffuf -w <wordlist> -fs 0 -u http://<target>/script.php?FUZZ=/etc/passwd
```


---

