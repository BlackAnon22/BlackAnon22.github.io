# Box: Bashed
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.129.38.185 -v -p- -T4```

```
Nmap scan report for 10.129.38.185
Host is up (0.14s latency).
Not shown: 65435 closed tcp ports (reset), 99 filtered tcp ports (no-response)
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-title: Arrexel's Development Site
|_http-favicon: Unknown favicon MD5: 6AA5034A553DFA77C3B2C7B4C26CF870
| http-methods: 
|_  Supported Methods: OPTIONS GET HEAD POST
|_http-server-header: Apache/2.4.18 (Ubuntu)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94%E=4%D=12/27%OT=80%CT=1%CU=39715%PV=Y%DS=2%DC=T%G=Y%TM=658B8D
OS:24%P=x86_64-pc-linux-gnu)SEQ(SP=100%GCD=1%ISR=109%TI=Z%CI=I%TS=8)SEQ(SP=
OS:FF%GCD=1%ISR=109%TI=Z%CI=I%TS=8)OPS(O1=M53CST11NW7%O2=M53CST11NW7%O3=M53
OS:CNNT11NW7%O4=M53CST11NW7%O5=M53CST11NW7%O6=M53CST11)WIN(W1=7120%W2=7120%
OS:W3=7120%W4=7120%W5=7120%W6=7120)ECN(R=Y%DF=Y%T=40%W=7210%O=M53CNNSNW7%CC
OS:=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T
OS:=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=
OS:0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=N)U1(R=Y%DF=N%T=40
OS:%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 0.011 days (since Wed Dec 27 03:18:25 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=256 (Good luck!)
IP ID Sequence Generation: All zeros

TRACEROUTE (using port 995/tcp)
HOP RTT       ADDRESS
1   142.55 ms 10.10.14.1
2   140.40 ms 10.129.38.185

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Wed Dec 27 03:34:13 2023 -- 1 IP address (1 host up) scanned in 1127.11 seconds
```
From our scan we have one open port, port 80 which runs on http. So, our enumeration today will be focused on port 80.



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d090655b-9177-467d-90fb-4da5a3dd7916)

Lets fuzz for directories using ffuf

command:```ffuf -u "http://10.129.38.185/FUZZ" -w /usr/share/wordlists/dirb/common.txt  -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/bashed]
└─$ ffuf -u "http://10.129.38.185/FUZZ" -w /usr/share/wordlists/dirb/common.txt  -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v2.0.0-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://10.129.38.185/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

[Status: 200, Size: 7743, Words: 2956, Lines: 162, Duration: 141ms]
    * FUZZ:

[Status: 200, Size: 0, Words: 1, Lines: 1, Duration: 153ms]
    * FUZZ: config.php

[Status: 301, Size: 312, Words: 20, Lines: 10, Duration: 159ms]
    * FUZZ: css

[Status: 301, Size: 312, Words: 20, Lines: 10, Duration: 139ms]
    * FUZZ: dev

[Status: 301, Size: 314, Words: 20, Lines: 10, Duration: 161ms]
    * FUZZ: fonts

[Status: 301, Size: 315, Words: 20, Lines: 10, Duration: 150ms]
    * FUZZ: images

[Status: 200, Size: 7743, Words: 2956, Lines: 162, Duration: 156ms]
    * FUZZ: index.html

[Status: 301, Size: 311, Words: 20, Lines: 10, Duration: 146ms]
    * FUZZ: js

[Status: 301, Size: 312, Words: 20, Lines: 10, Duration: 162ms]
    * FUZZ: php

[Status: 403, Size: 301, Words: 22, Lines: 12, Duration: 139ms]
    * FUZZ: server-status

[Status: 301, Size: 316, Words: 20, Lines: 10, Duration: 145ms]
    * FUZZ: uploads

:: Progress: [32298/32298] :: Job [1/1] :: 272 req/sec :: Duration: [0:02:08] :: Errors: 0 ::
```

We have lots of directories here, the directory that interests me is the ```/dev``` directory









































