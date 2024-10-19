---
title: Gobuster
description: 
draft: false
tags: 
date: 2024-10-18
---

**Recursively enumerate directories and files including extensions like HTML and PHP**
```bash
gobuster dir -u <IP> -e -r -x html,htm,asp,aspx,jsp,php,cgi,txt,xml -w /usr/share/wordlists/dirb/common.txt
```


