---
title: Better Shell
description: 
draft: false
tags: 
date: 2024-10-18
---


```bash
python -c 'import pty; pty.spawn("/bin/bash")'
```

```bash
alias ls="ls --color" #adds color to shell
```

**Upgrade from a Netcat reverse shell to get a a python TTY to a fully interactive shell with tab complete, bash history, working left/right arrow keys, CTRL+C, etc:**
```bash
CTRL+Z   ### Background python TTY
stty raw -echo
fg    ### press ENTER, you won't see your commands echoed. 
reset
export SHELL=bash
export TERM=linux    ### Specify "linux" to run nano, vi, sudoedit, etc.
stty rows 46 columns 169    ### optional, resize window
```
