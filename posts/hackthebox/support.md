# Box: Support
# Level: Easy
# OS: Windows
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A -T4 -p- -v 10.129.227.255```

```
Nmap scan report for 10.129.227.255
Host is up (0.26s latency).
Not shown: 65516 filtered tcp ports (no-response)
PORT      STATE SERVICE       VERSION
53/tcp    open  domain        Simple DNS Plus
88/tcp    open  kerberos-sec  Microsoft Windows Kerberos (server time: 2023-10-27 07:08:30Z)
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
389/tcp   open  ldap          Microsoft Windows Active Directory LDAP (Domain: support.htb0., Site: Default-First-Site-Name)
445/tcp   open  microsoft-ds?
464/tcp   open  kpasswd5?
593/tcp   open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp   open  tcpwrapped
3268/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: support.htb0., Site: Default-First-Site-Name)
3269/tcp  open  tcpwrapped
5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
9389/tcp  open  mc-nmf        .NET Message Framing
49664/tcp open  msrpc         Microsoft Windows RPC
49667/tcp open  msrpc         Microsoft Windows RPC
49676/tcp open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
49681/tcp open  msrpc         Microsoft Windows RPC
49705/tcp open  msrpc         Microsoft Windows RPC
51898/tcp open  msrpc         Microsoft Windows RPC
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running (JUST GUESSING): Microsoft Windows 2022 (88%)
Aggressive OS guesses: Microsoft Windows Server 2022 (88%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 0.010 days (since Fri Oct 27 07:55:31 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=263 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: Host: DC; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-time: 
|   date: 2023-10-27T07:09:30
|_  start_date: N/A
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled and required

TRACEROUTE (using port 139/tcp)
HOP RTT       ADDRESS
1   283.65 ms 10.10.14.1
2   284.42 ms 10.129.227.255

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Fri Oct 27 08:10:15 2023 -- 1 IP address (1 host up) scanned in 549.69 seconds
```
From our nmap scan we have quite a number of open ports. Lets start our enumeration from the port that connects to the smb server



# Enumeration (Port 445)

Lets first view the available shares on the smb server

command:```smbclient -L 10.129.227.255```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/support]
└─$ smbclient -L 10.129.227.255                
Password for [WORKGROUP\bl4ck4non]:

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        NETLOGON        Disk      Logon server share 
        support-tools   Disk      support staff tools
        SYSVOL          Disk      Logon server share 
Reconnecting with SMB1 for workgroup listing.
do_connect: Connection to 10.129.227.255 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
Unable to connect with SMB1 -- no workgroup available
```
We have 6 shares available on this server, all are default shares except ```support-tools```.

Lets connect to this share

command:```smbclient //10.129.227.255/support-tools```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/support]
└─$ smbclient //10.129.227.255/support-tools
Password for [WORKGROUP\bl4ck4non]:
Try "help" to get a list of possible commands.
smb: \> ls
  .                                   D        0  Wed Jul 20 18:01:06 2022
  ..                                  D        0  Sat May 28 12:18:25 2022
  7-ZipPortable_21.07.paf.exe         A  2880728  Sat May 28 12:19:19 2022
  npp.8.4.1.portable.x64.zip          A  5439245  Sat May 28 12:19:55 2022
  putty.exe                           A  1273576  Sat May 28 12:20:06 2022
  SysinternalsSuite.zip               A 48102161  Sat May 28 12:19:31 2022
  UserInfo.exe.zip                    A   277499  Wed Jul 20 18:01:07 2022
  windirstat1_1_2_setup.exe           A    79171  Sat May 28 12:20:17 2022
  WiresharkPortable64_3.6.5.paf.exe      A 44398000  Sat May 28 12:19:43 2022

                4026367 blocks of size 4096. 966881 blocks available
smb: \> 
```
nice nice, we have 7 files available on this share, the file that looks interesting is the file ```UserInfo.exe.zip```, we can download this to our machine using the ```get``` command

```
smb: \> get UserInfo.exe.zip 
getting file \UserInfo.exe.zip of size 277499 as UserInfo.exe.zip (137.2 KiloBytes/sec) (average 137.2 KiloBytes/sec)
smb: \> exit
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/support]
└─$ ls -l UserInfo.exe.zip      
-rw-r--r-- 1 bl4ck4non bl4ck4non 277499 Oct 27 08:20 UserInfo.exe.zip
```
smooth, lets unzip this file

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/support]
└─$ unzip UserInfo.exe.zip 
Archive:  UserInfo.exe.zip
  inflating: UserInfo.exe            
  inflating: CommandLineParser.dll   
  inflating: Microsoft.Bcl.AsyncInterfaces.dll  
  inflating: Microsoft.Extensions.DependencyInjection.Abstractions.dll  
  inflating: Microsoft.Extensions.DependencyInjection.dll  
  inflating: Microsoft.Extensions.Logging.Abstractions.dll  
  inflating: System.Buffers.dll      
  inflating: System.Memory.dll       
  inflating: System.Numerics.Vectors.dll  
  inflating: System.Runtime.CompilerServices.Unsafe.dll  
  inflating: System.Threading.Tasks.Extensions.dll  
  inflating: UserInfo.exe.config 
```































