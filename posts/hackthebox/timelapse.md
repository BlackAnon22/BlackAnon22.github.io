# Box: Timelapse
# Level: Easy
# OS: Windows
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.129.227.105 -T4  -v -p-```

```
Nmap scan report for 10.129.227.105
Host is up (0.24s latency).
Not shown: 65519 filtered tcp ports (no-response)
PORT      STATE SERVICE       VERSION
53/tcp    open  domain        Simple DNS Plus
88/tcp    open  kerberos-sec  Microsoft Windows Kerberos (server time: 2023-09-26 05:11:48Z)
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
389/tcp   open  ldap          Microsoft Windows Active Directory LDAP (Domain: timelapse.htb0., Site: Default-First-Site-Name)
445/tcp   open  microsoft-ds?
464/tcp   open  kpasswd5?
593/tcp   open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp   open  ldapssl?
5986/tcp  open  ssl/http      Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
| ssl-cert: Subject: commonName=dc01.timelapse.htb
| Issuer: commonName=dc01.timelapse.htb
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-10-25T14:05:29
| Not valid after:  2022-10-25T14:25:29
| MD5:   e233a19945040859013fb9c5e4f691c3
|_SHA-1: 5861acf776b8703fd01ee25dfc7c9952a4477652
| tls-alpn: 
|_  http/1.1
|_ssl-date: 2023-09-26T05:13:28+00:00; +7h59m58s from scanner time.
|_http-title: Not Found
9389/tcp  open  mc-nmf        .NET Message Framing
49667/tcp open  msrpc         Microsoft Windows RPC
49673/tcp open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
49674/tcp open  msrpc         Microsoft Windows RPC
49696/tcp open  msrpc         Microsoft Windows RPC
64129/tcp open  msrpc         Microsoft Windows RPC
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
OS fingerprint not ideal because: Missing a closed TCP port so results incomplete
No OS matches for host
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=264 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: Host: DC01; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: mean: 7h59m57s, deviation: 0s, median: 7h59m57s
| smb2-time: 
|   date: 2023-09-26T05:12:52
|_  start_date: N/A
| smb2-security-mode: 
|   311: 
|_    Message signing enabled and required

TRACEROUTE (using port 53/tcp)
HOP RTT       ADDRESS
1   279.92 ms 10.10.14.1
2   280.01 ms 10.129.227.105

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Mon Sep 25 22:13:37 2023 -- 1 IP address (1 host up) scanned in 406.16 seconds
```
From our nmap scan we have quite a number of open ports. Our enumeration today will actually be focused on the port running the smb service, that is, port 445, also the port running the http service, that is, port 5986.




# Enumeration (Port 445)

Lets start out by checking the shares available on the smb server

command:```smbclient -L 10.129.227.105```

Since we have no password just hit the ```Enter``` key

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Timelapse]
└─$ smbclient -L 10.129.227.105      
Password for [WORKGROUP\bl4ck4non]:

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        NETLOGON        Disk      Logon server share 
        Shares          Disk      
        SYSVOL          Disk      Logon server share 
Reconnecting with SMB1 for workgroup listing.
do_connect: Connection to 10.129.227.105 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
Unable to connect with SMB1 -- no workgroup available
```
We have 6 shares available on this server. The most interesting one out of these shares is the sharename ```Shares```

Lets connect to this sharename to see what we have there

command:```smbclient //10.129.227.105/Shares```

Since we have no password just hit the ```Enter``` key

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Timelapse]
└─$ smbclient //10.129.227.105/Shares
Password for [WORKGROUP\bl4ck4non]:
Try "help" to get a list of possible commands.
smb: \> ls
  .                                   D        0  Mon Oct 25 16:39:15 2021
  ..                                  D        0  Mon Oct 25 16:39:15 2021
  Dev                                 D        0  Mon Oct 25 20:40:06 2021
  HelpDesk                            D        0  Mon Oct 25 16:48:42 2021

                6367231 blocks of size 4096. 1286468 blocks available
smb: \> 
```
Cool, we can now view the files avaiable on the sharename ```Shares``` on the smb server.

Navigating to the ```Dev``` directory, there's a zip file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c2700dea-b95a-4e51-9e85-e4a85d49bb14)

Lets download this file to our machine by using the ```get``` command.

command:```get winrm_backup.zip```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/80b5ad2e-52d3-4328-8b34-2a5e76bfeee4)

Good. Now we can try to unzip the file























