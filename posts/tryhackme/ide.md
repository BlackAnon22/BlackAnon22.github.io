<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 10.10.101.244 -p- -T4 -v

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-03 10:19 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 10:19
Completed NSE at 10:19, 0.00s elapsed
Initiating NSE at 10:19
Completed NSE at 10:19, 0.00s elapsed
Initiating NSE at 10:19
Completed NSE at 10:19, 0.00s elapsed
Initiating Ping Scan at 10:19
Scanning 10.10.101.244 [4 ports]
Completed Ping Scan at 10:19, 0.37s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 10:19
Completed Parallel DNS resolution of 1 host. at 10:19, 0.03s elapsed
Initiating SYN Stealth Scan at 10:19
Scanning 10.10.101.244 [65535 ports]
Discovered open port 21/tcp on 10.10.101.244
Discovered open port 22/tcp on 10.10.101.244
Discovered open port 80/tcp on 10.10.101.244
Increasing send delay for 10.10.101.244 from 0 to 5 due to 534 out of 1334 dropped probes since last increase.
Increasing send delay for 10.10.101.244 from 5 to 10 due to 13 out of 31 dropped probes since last increase.
SYN Stealth Scan Timing: About 5.37% done; ETC: 10:29 (0:09:06 remaining)
SYN Stealth Scan Timing: About 7.46% done; ETC: 10:33 (0:12:37 remaining)
SYN Stealth Scan Timing: About 9.07% done; ETC: 10:36 (0:15:12 remaining)
SYN Stealth Scan Timing: About 13.10% done; ETC: 10:35 (0:13:23 remaining)
SYN Stealth Scan Timing: About 17.02% done; ETC: 10:34 (0:12:16 remaining)
SYN Stealth Scan Timing: About 21.33% done; ETC: 10:34 (0:11:30 remaining)
SYN Stealth Scan Timing: About 25.68% done; ETC: 10:34 (0:10:45 remaining)
SYN Stealth Scan Timing: About 30.40% done; ETC: 10:34 (0:10:00 remaining)
SYN Stealth Scan Timing: About 35.56% done; ETC: 10:34 (0:09:16 remaining)
SYN Stealth Scan Timing: About 40.74% done; ETC: 10:34 (0:08:32 remaining)
SYN Stealth Scan Timing: About 45.59% done; ETC: 10:34 (0:07:47 remaining)
Discovered open port 62337/tcp on 10.10.101.244
SYN Stealth Scan Timing: About 50.61% done; ETC: 10:34 (0:07:03 remaining)
SYN Stealth Scan Timing: About 55.62% done; ETC: 10:33 (0:06:19 remaining)
SYN Stealth Scan Timing: About 61.02% done; ETC: 10:33 (0:05:32 remaining)
SYN Stealth Scan Timing: About 66.05% done; ETC: 10:33 (0:04:49 remaining)
SYN Stealth Scan Timing: About 71.25% done; ETC: 10:33 (0:04:05 remaining)
SYN Stealth Scan Timing: About 76.45% done; ETC: 10:34 (0:03:22 remaining)
SYN Stealth Scan Timing: About 81.37% done; ETC: 10:33 (0:02:39 remaining)
SYN Stealth Scan Timing: About 86.45% done; ETC: 10:33 (0:01:55 remaining)
SYN Stealth Scan Timing: About 91.61% done; ETC: 10:33 (0:01:11 remaining)
Completed SYN Stealth Scan at 10:34, 862.28s elapsed (65535 total ports)
Initiating Service scan at 10:34
Scanning 4 services on 10.10.101.244
Completed Service scan at 10:34, 12.07s elapsed (4 services on 1 host)
Initiating OS detection (try #1) against 10.10.101.244
Retrying OS detection (try #2) against 10.10.101.244
Retrying OS detection (try #3) against 10.10.101.244
Retrying OS detection (try #4) against 10.10.101.244
Retrying OS detection (try #5) against 10.10.101.244
Initiating Traceroute at 10:34
Completed Traceroute at 10:34, 0.17s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 10:34
Completed Parallel DNS resolution of 2 hosts. at 10:34, 0.03s elapsed
NSE: Script scanning 10.10.101.244.
Initiating NSE at 10:34
NSE: [ftp-bounce] PORT response: 500 Illegal PORT command.
Completed NSE at 10:34, 5.17s elapsed
Initiating NSE at 10:34
Completed NSE at 10:34, 1.53s elapsed
Initiating NSE at 10:34
Completed NSE at 10:34, 0.00s elapsed
Nmap scan report for 10.10.101.244
Host is up (0.16s latency).
Not shown: 65531 closed tcp ports (reset)
PORT      STATE SERVICE VERSION
21/tcp    open  ftp     vsftpd 3.0.3
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.18.1.243
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 1
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
22/tcp    open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 e2bed33ce87681ef477ed043d4281428 (RSA)
|   256 a882e961e4bb61af9f3a193b64bcde87 (ECDSA)
|_  256 244675a76339b63ce9f1fca413516320 (ED25519)
80/tcp    open  http    Apache httpd 2.4.29 ((Ubuntu))
| http-methods: 
|_  Supported Methods: OPTIONS HEAD GET POST
|_http-title: Apache2 Ubuntu Default Page: It works
|_http-server-header: Apache/2.4.29 (Ubuntu)
62337/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-title: Codiad 2.8.4
|_http-favicon: Unknown favicon MD5: B4A327D2242C42CF2EE89C623279665F
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.29 (Ubuntu)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=3/3%OT=21%CT=1%CU=32851%PV=Y%DS=2%DC=T%G=Y%TM=6401BF31
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=FF%GCD=1%ISR=10D%TI=Z%CI=Z%TS=A)SEQ(SP=FF%
OS:GCD=1%ISR=10D%TI=Z%CI=Z%II=I%TS=A)OPS(O1=M506ST11NW6%O2=M506ST11NW6%O3=M
OS:506NNT11NW6%O4=M506ST11NW6%O5=M506ST11NW6%O6=M506ST11)WIN(W1=F4B3%W2=F4B
OS:3%W3=F4B3%W4=F4B3%W5=F4B3%W6=F4B3)ECN(R=Y%DF=Y%T=40%W=F507%O=M506NNSNW6%
OS:CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y
OS:%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%R
OS:D=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%
OS:S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPC
OS:K=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 2.086 days (since Wed Mar  1 08:30:52 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=255 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 8080/tcp)
HOP RTT       ADDRESS
1   162.80 ms 10.18.0.1
2   160.82 ms 10.10.101.244

NSE: Script Post-scanning.
Initiating NSE at 10:34
Completed NSE at 10:34, 0.00s elapsed
Initiating NSE at 10:34
Completed NSE at 10:34, 0.00s elapsed
Initiating NSE at 10:34
Completed NSE at 10:34, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 897.78 seconds
           Raw packets sent: 72421 (3.191MB) | Rcvd: 67859 (2.718MB)
```
We have 4 ports opened. Port 21, port 22, port 80 and port 62337.



<h2>Enumeration Port 21</h2>

Since Anonymous login is allowed this means we can login with the default credentials.

```username:anonymous```      ```password:anonymous```

command used: ftp 10.10.101.244

![image](https://user-images.githubusercontent.com/67879936/222686856-14dd1c86-c70d-4640-88ba-719895346b82.png)

Now that we are logged in lets look for files that might help us gain access to the machine

![image](https://user-images.githubusercontent.com/67879936/222686980-5ee088b2-f24c-499c-8fbc-0df916859e77.png)

There was a file ```-```, so we will use the get command to download the file to our machine. After downloading the file, we will have to rename it, I renamed mine to ```ftp_file```, then I used the cat command to view the contents of the file.

>command: cat ftp_file

![image](https://user-images.githubusercontent.com/67879936/222687716-0cf9277b-af8e-4a2b-9939-d17c23a49973.png)

The contents of the file gives us 2 users, ```john``` and ```drac```. Also, we can see that the content of the file was from user ```drac``` to user “john”. This means when we find a login page which we will, the username should be john and the password would be a default password (we will have to try some default passwords). Since, that was the only file in the ftp directory lets move on with enumeration.



<h2>Enumeration Port 80</h2>

Going over to the webpage there was nothing there

![image](https://user-images.githubusercontent.com/67879936/222688532-bce837b4-3bb8-49b8-92e0-cc1ac3e0ebcf.png)

Lets fire up gobuster to search for hidden directories

>command: gobuster dir -u http://10.10.101.244 -w /usr/share/dirb/wordlists/common.txt -t 16 -x php,txt,html,zip

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/IDE]
└─$ gobuster dir -u http://10.10.101.244 -w /usr/share/dirb/wordlists/common.txt -t 16 -x php,txt,html,zip
===============================================================
Gobuster v3.4
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.101.244
[+] Method:                  GET
[+] Threads:                 16
[+] Wordlist:                /usr/share/dirb/wordlists/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.4
[+] Extensions:              php,txt,html,zip
[+] Timeout:                 10s
===============================================================
2023/03/03 10:52:40 Starting gobuster in directory enumeration mode
===============================================================
/index.html           (Status: 200) [Size: 10918]
/index.html           (Status: 200) [Size: 10918]
/server-status        (Status: 403) [Size: 278]
Progress: 23070 / 23075 (99.98%)
===============================================================
2023/03/03 10:57:12 Finished
===============================================================

```
From the scan above we can see that there is nothing for us in this port, so lets move on to the next port.




<h2>Enumeration Port 62337</h2>

Going over to the webpage we find a login page

![image](https://user-images.githubusercontent.com/67879936/222690787-b5ed490f-f63e-4a2b-97e4-06d815566148.png)

Lets fire up gobuster again to search for hidden directories

>command: gobuster dir -u http://10.10.101.244:62337 -w /usr/share/dirb/wordlists/common.txt -t 16 -x php,txt,html,zip


  
  
  
  
  
  
  
  
  
  














