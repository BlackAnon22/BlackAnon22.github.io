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

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/31d9728c-c538-452f-9a30-e5c15afa25f1)

A password is required but we don't have one. 

Well, I called john already and he said he will be sending one of his brothers, ```zip2ohn```.

Using ```zip2john``` we'll try to generate a hash that can be cracked with ```john```

command:```zip2john winrm_backup.zip > winrm.txt```
command:```john winrm.txt  --wordlist=/home/bl4ck4non/Documents/rockyou.txt```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Timelapse]
└─$ zip2john winrm_backup.zip > winrm.txt
ver 2.0 efh 5455 efh 7875 winrm_backup.zip/legacyy_dev_auth.pfx PKZIP Encr: TS_chk, cmplen=2405, decmplen=2555, crc=12EC5683 ts=72AA cs=72aa type=8
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Timelapse]
└─$ john winrm.txt  --wordlist=/home/bl4ck4non/Documents/rockyou.txt                                     
Using default input encoding: UTF-8
Loaded 1 password hash (PKZIP [32/64])
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
supremelegacy    (winrm_backup.zip/legacyy_dev_auth.pfx)     
1g 0:00:00:01 DONE (2023-09-25 22:48) 0.9259g/s 3216Kp/s 3216Kc/s 3216KC/s surkerior..superkebab
Use the "--show" option to display all of the cracked passwords reliably
Session completed. 
```
So we got the password to be ```supremelegacy```. Now lets unzip

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Timelapse]
└─$ unzip winrm_backup.zip
Archive:  winrm_backup.zip
[winrm_backup.zip] legacyy_dev_auth.pfx password: 
  inflating: legacyy_dev_auth.pfx    
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Timelapse]
└─$ ls -l legacyy_dev_auth.pfx 
-rwxr-xr-x 1 bl4ck4non bl4ck4non 2555 Oct 25  2021 legacyy_dev_auth.pfx
```
cool the password worked and we got a ```PKCS#12``` file.

For those who don't know about ```PKCS#12``` file, it is a cryptographic file format that typically contains both a digital certificate and its associated private key. These files are often used for securing sensitive information and establishing secure connections, such as in SSL/TLS certificates for web servers.

To access this file we can use the ```openssl``` command

command:```openssl pkcs12 -info -in legacyy_dev_auth.pfx```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/90cff726-3689-4bb6-afa9-d3519ba43540)

oops, a password is required. 

I called  john again but he wasn't picking his calls (he probably thinks I'm disturbing him lool). So, I called one of his brothers ```pfx2john```

Using ```pfx2john``` to get the hash and then using john to crack the hash

command:```pfx2john legacyy_dev_auth.pfx > legacyy.txt```
command:```john legacyy.txt  --wordlist=/home/bl4ck4non/Documents/rockyou.txt```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Timelapse]
└─$ pfx2john legacyy_dev_auth.pfx > legacyy.txt
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Timelapse]
└─$ john legacyy.txt  --wordlist=/home/bl4ck4non/Documents/rockyou.txt
Using default input encoding: UTF-8
Loaded 1 password hash (pfx, (.pfx, .p12) [PKCS#12 PBE (SHA1/SHA2) 256/256 AVX2 8x])
Cost 1 (iteration count) is 2000 for all loaded hashes
Cost 2 (mac-type [1:SHA1 224:SHA224 256:SHA256 384:SHA384 512:SHA512]) is 1 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
thuglegacy       (legacyy_dev_auth.pfx)     
1g 0:00:01:42 DONE (2023-09-25 22:58) 0.009797g/s 31662p/s 31662c/s 31662C/s thuglife06..thsco04
Use the "--show" option to display all of the cracked passwords reliably
```
We got the password to be ```thuglegacy```

Applying this password

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f76a03c4-de24-4a0f-a84a-863eb2ca0e6e)

We are asked to provide a passphrase. Lets use a simple passphrase, ```qwertyuiop``` should work. That's simple enough I guess

Using the passphrase and yeah you have to verify the passphrase

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2bd683e5-61e4-414f-8e21-5386568975c2)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f69a777e-541c-4bae-b88e-3f7584b2d04e)

We can see that the issuer here is ```Legacyy```, well that's probably a user on the box. Since we have the digital certificate and its associated private key we can try to get a user shell on this box




# Exploitation

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2ab0cf77-4403-4356-9b67-28febe5f7159)

If you recall, when we ran the nmap command we saw this port opened.

Port 5986 is commonly used for secure communications with Windows Remote Management (WinRM) over HTTPS. WinRM is a management protocol used for remote management and automation tasks in Windows environments.





















