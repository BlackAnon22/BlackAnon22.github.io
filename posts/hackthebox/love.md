# Box: Love
# Level: Easy
# OS: Windows
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.89.221 -p- -T4 -v```

```
Nmap scan report for 10.129.89.221
Host is up (0.34s latency).
Not shown: 65516 closed tcp ports (reset)
PORT      STATE SERVICE     VERSION
80/tcp    open  http        Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1j PHP/7.3.27)
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1j PHP/7.3.27
|_http-title: Voting System using PHP
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
135/tcp   open  msrpc       Microsoft Windows RPC
139/tcp   open  netbios-ssn Microsoft Windows netbios-ssn
443/tcp   open  ssl/http    Apache httpd 2.4.46 (OpenSSL/1.1.1j PHP/7.3.27)
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1j PHP/7.3.27
| ssl-cert: Subject: commonName=staging.love.htb/organizationName=ValentineCorp/stateOrProvinceName=m/countryName=in
| Issuer: commonName=staging.love.htb/organizationName=ValentineCorp/stateOrProvinceName=m/countryName=in
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-01-18T14:00:16
| Not valid after:  2022-01-18T14:00:16
| MD5:   bff0:1add:5048:afc8:b3cf:7140:6e68:5ff6
|_SHA-1: 83ed:29c4:70f6:4036:a6f4:2d4d:4cf6:18a2:e9e4:96c2
|_ssl-date: TLS randomness does not represent time
|_http-title: 403 Forbidden
| tls-alpn: 
|_  http/1.1
445/tcp   open              Windows 10 Pro 19042 microsoft-ds (workgroup: WORKGROUP)
3306/tcp  open  mysql?
| fingerprint-strings: 
|   JavaRMI, Kerberos, LDAPBindReq, NCP, NotesRPC, TLSSessionReq, X11Probe, giop, ms-sql-s: 
|_    Host '10.10.16.30' is not allowed to connect to this MariaDB server
5000/tcp  open  http        Apache httpd 2.4.46 (OpenSSL/1.1.1j PHP/7.3.27)
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1j PHP/7.3.27
|_http-title: 403 Forbidden
5040/tcp  open  unknown
5985/tcp  open  http        Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-title: Not Found
|_http-server-header: Microsoft-HTTPAPI/2.0
5986/tcp  open  ssl/http    Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-title: Not Found
|_ssl-date: 2023-10-14T16:50:01+00:00; +21m32s from scanner time.
|_http-server-header: Microsoft-HTTPAPI/2.0
| tls-alpn: 
|_  http/1.1
| ssl-cert: Subject: commonName=LOVE
| Subject Alternative Name: DNS:LOVE, DNS:Love
| Issuer: commonName=LOVE
| Public Key type: rsa
| Public Key bits: 4096
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-04-11T14:39:19
| Not valid after:  2024-04-10T14:39:19
| MD5:   d35a:2ba6:8ef4:7568:f99d:d6f4:aaa2:03b5
|_SHA-1: 84ef:d922:a70a:6d9d:82b8:5bb3:d04f:066b:12f8:6e73
7680/tcp  open  pando-pub?
47001/tcp open  http        Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-title: Not Found
|_http-server-header: Microsoft-HTTPAPI/2.0
49664/tcp open  msrpc       Microsoft Windows RPC
49665/tcp open  msrpc       Microsoft Windows RPC
49666/tcp open  msrpc       Microsoft Windows RPC
49667/tcp open  msrpc       Microsoft Windows RPC
49668/tcp open  msrpc       Microsoft Windows RPC
49669/tcp open  msrpc       Microsoft Windows RPC
49670/tcp open  msrpc       Microsoft Windows RPC
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port3306-TCP:V=7.94%I=7%D=10/14%Time=652AC0EB%P=x86_64-pc-linux-gnu%r(T
SF:LSSessionReq,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.16\.30'\x20is\x20no
SF:t\x20allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(Ke
SF:rberos,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.16\.30'\x20is\x20not\x20a
SF:llowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(X11Probe
SF:,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.16\.30'\x20is\x20not\x20allowed
SF:\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(LDAPBindReq,4A
SF:,"F\0\0\x01\xffj\x04Host\x20'10\.10\.16\.30'\x20is\x20not\x20allowed\x2
SF:0to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(NCP,4A,"F\0\0\x01
SF:\xffj\x04Host\x20'10\.10\.16\.30'\x20is\x20not\x20allowed\x20to\x20conn
SF:ect\x20to\x20this\x20MariaDB\x20server")%r(NotesRPC,4A,"F\0\0\x01\xffj\
SF:x04Host\x20'10\.10\.16\.30'\x20is\x20not\x20allowed\x20to\x20connect\x2
SF:0to\x20this\x20MariaDB\x20server")%r(JavaRMI,4A,"F\0\0\x01\xffj\x04Host
SF:\x20'10\.10\.16\.30'\x20is\x20not\x20allowed\x20to\x20connect\x20to\x20
SF:this\x20MariaDB\x20server")%r(ms-sql-s,4A,"F\0\0\x01\xffj\x04Host\x20'1
SF:0\.10\.16\.30'\x20is\x20not\x20allowed\x20to\x20connect\x20to\x20this\x
SF:20MariaDB\x20server")%r(giop,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.16\
SF:.30'\x20is\x20not\x20allowed\x20to\x20connect\x20to\x20this\x20MariaDB\
SF:x20server");
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94%E=4%D=10/14%OT=80%CT=1%CU=39870%PV=Y%DS=2%DC=T%G=Y%TM=652AC1
OS:B0%P=x86_64-pc-linux-gnu)SEQ(SP=ED%GCD=1%ISR=106%TI=I%CI=I%II=I%SS=O%TS=
OS:U)SEQ(SP=ED%GCD=1%ISR=106%TI=I%CI=I%II=I%SS=S%TS=U)SEQ(SP=ED%GCD=1%ISR=1
OS:06%TI=RD%CI=I%II=I%TS=U)SEQ(SP=ED%GCD=3%ISR=106%TI=RD%CI=I%II=I%TS=U)OPS
OS:(O1=M53ANW8NNS%O2=M53ANW8NNS%O3=M53ANW8%O4=M53ANW8NNS%O5=M53ANW8NNS%O6=M
OS:53ANNS)WIN(W1=FFFF%W2=FFFF%W3=FFFF%W4=FFFF%W5=FFFF%W6=FF70)ECN(R=Y%DF=Y%
OS:T=80%W=FFFF%O=M53ANW8NNS%CC=N%Q=)T1(R=Y%DF=Y%T=80%S=O%A=S+%F=AS%RD=0%Q=)
OS:T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=80%W=0%S=A%A=O%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=
OS:80%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=80%W=0%S=A%A=O%F=R%O=%RD=0
OS:%Q=)T7(R=N)U1(R=Y%DF=N%T=80%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD
OS:=G)IE(R=Y%DFI=N%T=80%CD=Z)

Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=237 (Good luck!)
IP ID Sequence Generation: Randomized
Service Info: Hosts: www.example.com, LOVE, www.love.htb; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: mean: 2h06m32s, deviation: 3h30m00s, median: 21m31s
| smb-os-discovery: 
|   OS: Windows 10 Pro 19042 (Windows 10 Pro 6.3)
|   OS CPE: cpe:/o:microsoft:windows_10::-
|   Computer name: Love
|   NetBIOS computer name: LOVE\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2023-10-14T09:49:41-07:00
| smb2-time: 
|   date: 2023-10-14T16:49:47
|_  start_date: N/A
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
| smb-security-mode: 
|   account_used: <blank>
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)

TRACEROUTE (using port 995/tcp)
HOP RTT       ADDRESS
1   340.48 ms 10.10.16.1
2   158.33 ms 10.129.89.221

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sat Oct 14 17:28:32 2023 -- 1 IP address (1 host up) scanned in 2158.46 seconds
```
From our nmap scan we have quite a number of ports opened. We'll start our enumeration today from port 80.


# Enumeration (Port 80)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4a29fdd8-1318-45cd-973c-d79b460961d6)

We get this voting system login page. 

Checking for available exploits, I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6040db55-520d-428e-a0aa-46164c2971ab)

So, we can bypass this page using sqli. You can find the exploit [here](https://www.exploit-db.com/exploits/49843)

Now, lets try to login then we capture the request on burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/015bcee2-d44d-4bc5-a59f-e09340fb35da)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3b6b87e5-6662-46e1-80e0-4fdef4abb6f0)

Lets exploit this hehe



# Exploitation

Using the payload I got from exploit-db, I got my request to look like this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/37e884fc-6503-4c71-aef3-ec27b43f74ab)

Lets follow redirection

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2c572436-01d5-4ac7-ad3c-21a3a7592b59)

Lets follow this redirection also

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3c8b4142-6989-4548-8214-a4063be105b6)

Trying to view the response with "Render" should get you this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2cff733f-4cf9-403f-b373-ba882738acc2)

As you can see, we are successfully logged in.

Lets refresh the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/28483ce8-d9de-4357-bc7d-9e4a377e1cca)

nice nice







































