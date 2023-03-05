<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 192.168.53.114 -p- -T4 -v

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-05 04:28 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 04:28
Completed NSE at 04:28, 0.00s elapsed
Initiating NSE at 04:28
Completed NSE at 04:28, 0.00s elapsed
Initiating NSE at 04:28
Completed NSE at 04:28, 0.00s elapsed
Initiating Ping Scan at 04:28
Scanning 192.168.53.114 [4 ports]
Completed Ping Scan at 04:28, 0.22s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 04:28
Completed Parallel DNS resolution of 1 host. at 04:28, 0.04s elapsed
Initiating SYN Stealth Scan at 04:28
Scanning 192.168.53.114 [65535 ports]
Discovered open port 8080/tcp on 192.168.53.114
Discovered open port 21/tcp on 192.168.53.114
Discovered open port 3306/tcp on 192.168.53.114
Discovered open port 28080/tcp on 192.168.53.114
SYN Stealth Scan Timing: About 12.55% done; ETC: 04:32 (0:03:36 remaining)
SYN Stealth Scan Timing: About 24.05% done; ETC: 04:33 (0:03:13 remaining)
SYN Stealth Scan Timing: About 38.84% done; ETC: 04:33 (0:02:47 remaining)
Increasing send delay for 192.168.53.114 from 0 to 5 due to max_successful_tryno increase to 5
SYN Stealth Scan Timing: About 56.72% done; ETC: 04:34 (0:02:32 remaining)
SYN Stealth Scan Timing: About 65.07% done; ETC: 04:35 (0:02:13 remaining)
SYN Stealth Scan Timing: About 71.09% done; ETC: 04:35 (0:01:54 remaining)
SYN Stealth Scan Timing: About 77.16% done; ETC: 04:35 (0:01:34 remaining)
SYN Stealth Scan Timing: About 82.51% done; ETC: 04:35 (0:01:13 remaining)
Discovered open port 60022/tcp on 192.168.53.114
SYN Stealth Scan Timing: About 88.05% done; ETC: 04:35 (0:00:51 remaining)
Completed SYN Stealth Scan at 04:36, 454.71s elapsed (65535 total ports)
Initiating Service scan at 04:36
Scanning 5 services on 192.168.53.114
Completed Service scan at 04:36, 18.36s elapsed (5 services on 1 host)
Initiating OS detection (try #1) against 192.168.53.114
Retrying OS detection (try #2) against 192.168.53.114
Retrying OS detection (try #3) against 192.168.53.114
Retrying OS detection (try #4) against 192.168.53.114
Retrying OS detection (try #5) against 192.168.53.114
Initiating Traceroute at 04:36
Completed Traceroute at 04:36, 0.17s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 04:36
Completed Parallel DNS resolution of 2 hosts. at 04:36, 0.01s elapsed
NSE: Script scanning 192.168.53.114.
Initiating NSE at 04:36
NSE: [ftp-bounce] PORT response: 500 Illegal PORT command.
Completed NSE at 04:37, 8.01s elapsed
Initiating NSE at 04:37
Completed NSE at 04:37, 2.35s elapsed
Initiating NSE at 04:37
Completed NSE at 04:37, 0.00s elapsed
Nmap scan report for 192.168.53.114
Host is up (0.14s latency).
Not shown: 65530 closed tcp ports (reset)
PORT      STATE SERVICE    VERSION
21/tcp    open  ftp        vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_drwxr-xr-x   14 14       11           4096 Nov 06  2020 forum
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to 192.168.49.53
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 1
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
3306/tcp  open  mysql?
| fingerprint-strings: 
|   DNSStatusRequestTCP, DNSVersionBindReqTCP, GetRequest, HTTPOptions, Help, LANDesk-RC, LDAPSearchReq, NULL, RTSPRequest, SIPOptions, TLSSessionReq, TerminalServer, WMSRequest, giop, ms-sql-s: 
|_    Host '192.168.49.53' is not allowed to connect to this MariaDB server
8080/tcp  open  http-proxy
|_http-title: ForumOnRails
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
| fingerprint-strings: 
|   GetRequest, HTTPOptions: 
|     HTTP/1.0 403 Forbidden
|     Content-Type: text/html; charset=UTF-8
|     Content-Length: 3102
|     <!DOCTYPE html>
|     <html lang="en">
|     <head>
|     <meta charset="utf-8" />
|     <title>Action Controller: Exception caught</title>
|     <style>
|     body {
|     background-color: #FAFAFA;
|     color: #333;
|     margin: 0px;
|     body, p, ol, ul, td {
|     font-family: helvetica, verdana, arial, sans-serif;
|     font-size: 13px;
|     line-height: 18px;
|     font-size: 11px;
|     white-space: pre-wrap;
|     pre.box {
|     border: 1px solid #EEE;
|     padding: 10px;
|     margin: 0px;
|     width: 958px;
|     header {
|     color: #F0F0F0;
|     background: #C52F24;
|     padding: 0.5em 1.5em;
|     margin: 0.2em 0;
|     line-height: 1.1em;
|     font-size: 2em;
|     color: #C52F24;
|     line-height: 25px;
|     .details {
|_    bord
|_http-favicon: Unknown favicon MD5: D41D8CD98F00B204E9800998ECF8427E
28080/tcp open  http       Apache httpd 2.4.46 ((Unix))
|_http-server-header: Apache/2.4.46 (Unix)
|_http-title: html5-goku-en-javascript
| http-methods: 
|   Supported Methods: OPTIONS HEAD GET POST TRACE
|_  Potentially risky methods: TRACE
60022/tcp open  ssh        OpenSSH 8.4 (protocol 2.0)
| ssh-hostkey: 
|   3072 76615ce18cca14e87a63baa3469f09b3 (RSA)
|   256 e3edfca810d78eb17cdea259df190629 (ECDSA)
|_  256 e5dddda7e3ac5fb92b4bd027e33cc243 (ED25519)
2 services unrecognized despite returning data. If you know the service/version, please submit the following fingerprints at https://nmap.org/cgi-bin/submit.cgi?new-service :
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port3306-TCP:V=7.93%I=7%D=3/5%Time=64040E38%P=x86_64-pc-linux-gnu%r(NUL
SF:L,4C,"H\0\0\x01\xffj\x04Host\x20'192\.168\.49\.53'\x20is\x20not\x20allo
SF:wed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(GetRequest,
SF:4C,"H\0\0\x01\xffj\x04Host\x20'192\.168\.49\.53'\x20is\x20not\x20allowe
SF:d\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(HTTPOptions,4
SF:C,"H\0\0\x01\xffj\x04Host\x20'192\.168\.49\.53'\x20is\x20not\x20allowed
SF:\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(RTSPRequest,4C
SF:,"H\0\0\x01\xffj\x04Host\x20'192\.168\.49\.53'\x20is\x20not\x20allowed\
SF:x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(DNSVersionBindR
SF:eqTCP,4C,"H\0\0\x01\xffj\x04Host\x20'192\.168\.49\.53'\x20is\x20not\x20
SF:allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(DNSStat
SF:usRequestTCP,4C,"H\0\0\x01\xffj\x04Host\x20'192\.168\.49\.53'\x20is\x20
SF:not\x20allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(
SF:Help,4C,"H\0\0\x01\xffj\x04Host\x20'192\.168\.49\.53'\x20is\x20not\x20a
SF:llowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(TLSSessi
SF:onReq,4C,"H\0\0\x01\xffj\x04Host\x20'192\.168\.49\.53'\x20is\x20not\x20
SF:allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(LDAPSea
SF:rchReq,4C,"H\0\0\x01\xffj\x04Host\x20'192\.168\.49\.53'\x20is\x20not\x2
SF:0allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(SIPOpt
SF:ions,4C,"H\0\0\x01\xffj\x04Host\x20'192\.168\.49\.53'\x20is\x20not\x20a
SF:llowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(LANDesk-
SF:RC,4C,"H\0\0\x01\xffj\x04Host\x20'192\.168\.49\.53'\x20is\x20not\x20all
SF:owed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(TerminalSe
SF:rver,4C,"H\0\0\x01\xffj\x04Host\x20'192\.168\.49\.53'\x20is\x20not\x20a
SF:llowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(WMSReque
SF:st,4C,"H\0\0\x01\xffj\x04Host\x20'192\.168\.49\.53'\x20is\x20not\x20all
SF:owed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(ms-sql-s,4
SF:C,"H\0\0\x01\xffj\x04Host\x20'192\.168\.49\.53'\x20is\x20not\x20allowed
SF:\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(giop,4C,"H\0\0
SF:\x01\xffj\x04Host\x20'192\.168\.49\.53'\x20is\x20not\x20allowed\x20to\x
SF:20connect\x20to\x20this\x20MariaDB\x20server");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port8080-TCP:V=7.93%I=7%D=3/5%Time=64040E3E%P=x86_64-pc-linux-gnu%r(Get
SF:Request,C76,"HTTP/1\.0\x20403\x20Forbidden\r\nContent-Type:\x20text/htm
SF:l;\x20charset=UTF-8\r\nContent-Length:\x203102\r\n\r\n<!DOCTYPE\x20html
SF:>\n<html\x20lang=\"en\">\n<head>\n\x20\x20<meta\x20charset=\"utf-8\"\x2
SF:0/>\n\x20\x20<title>Action\x20Controller:\x20Exception\x20caught</title
SF:>\n\x20\x20<style>\n\x20\x20\x20\x20body\x20{\n\x20\x20\x20\x20\x20\x20
SF:background-color:\x20#FAFAFA;\n\x20\x20\x20\x20\x20\x20color:\x20#333;\
SF:n\x20\x20\x20\x20\x20\x20margin:\x200px;\n\x20\x20\x20\x20}\n\n\x20\x20
SF:\x20\x20body,\x20p,\x20ol,\x20ul,\x20td\x20{\n\x20\x20\x20\x20\x20\x20f
SF:ont-family:\x20helvetica,\x20verdana,\x20arial,\x20sans-serif;\n\x20\x2
SF:0\x20\x20\x20\x20font-size:\x20\x20\x2013px;\n\x20\x20\x20\x20\x20\x20l
SF:ine-height:\x2018px;\n\x20\x20\x20\x20}\n\n\x20\x20\x20\x20pre\x20{\n\x
SF:20\x20\x20\x20\x20\x20font-size:\x2011px;\n\x20\x20\x20\x20\x20\x20whit
SF:e-space:\x20pre-wrap;\n\x20\x20\x20\x20}\n\n\x20\x20\x20\x20pre\.box\x2
SF:0{\n\x20\x20\x20\x20\x20\x20border:\x201px\x20solid\x20#EEE;\n\x20\x20\
SF:x20\x20\x20\x20padding:\x2010px;\n\x20\x20\x20\x20\x20\x20margin:\x200p
SF:x;\n\x20\x20\x20\x20\x20\x20width:\x20958px;\n\x20\x20\x20\x20}\n\n\x20
SF:\x20\x20\x20header\x20{\n\x20\x20\x20\x20\x20\x20color:\x20#F0F0F0;\n\x
SF:20\x20\x20\x20\x20\x20background:\x20#C52F24;\n\x20\x20\x20\x20\x20\x20
SF:padding:\x200\.5em\x201\.5em;\n\x20\x20\x20\x20}\n\n\x20\x20\x20\x20h1\
SF:x20{\n\x20\x20\x20\x20\x20\x20margin:\x200\.2em\x200;\n\x20\x20\x20\x20
SF:\x20\x20line-height:\x201\.1em;\n\x20\x20\x20\x20\x20\x20font-size:\x20
SF:2em;\n\x20\x20\x20\x20}\n\n\x20\x20\x20\x20h2\x20{\n\x20\x20\x20\x20\x2
SF:0\x20color:\x20#C52F24;\n\x20\x20\x20\x20\x20\x20line-height:\x2025px;\
SF:n\x20\x20\x20\x20}\n\n\x20\x20\x20\x20\.details\x20{\n\x20\x20\x20\x20\
SF:x20\x20bord")%r(HTTPOptions,C76,"HTTP/1\.0\x20403\x20Forbidden\r\nConte
SF:nt-Type:\x20text/html;\x20charset=UTF-8\r\nContent-Length:\x203102\r\n\
SF:r\n<!DOCTYPE\x20html>\n<html\x20lang=\"en\">\n<head>\n\x20\x20<meta\x20
SF:charset=\"utf-8\"\x20/>\n\x20\x20<title>Action\x20Controller:\x20Except
SF:ion\x20caught</title>\n\x20\x20<style>\n\x20\x20\x20\x20body\x20{\n\x20
SF:\x20\x20\x20\x20\x20background-color:\x20#FAFAFA;\n\x20\x20\x20\x20\x20
SF:\x20color:\x20#333;\n\x20\x20\x20\x20\x20\x20margin:\x200px;\n\x20\x20\
SF:x20\x20}\n\n\x20\x20\x20\x20body,\x20p,\x20ol,\x20ul,\x20td\x20{\n\x20\
SF:x20\x20\x20\x20\x20font-family:\x20helvetica,\x20verdana,\x20arial,\x20
SF:sans-serif;\n\x20\x20\x20\x20\x20\x20font-size:\x20\x20\x2013px;\n\x20\
SF:x20\x20\x20\x20\x20line-height:\x2018px;\n\x20\x20\x20\x20}\n\n\x20\x20
SF:\x20\x20pre\x20{\n\x20\x20\x20\x20\x20\x20font-size:\x2011px;\n\x20\x20
SF:\x20\x20\x20\x20white-space:\x20pre-wrap;\n\x20\x20\x20\x20}\n\n\x20\x2
SF:0\x20\x20pre\.box\x20{\n\x20\x20\x20\x20\x20\x20border:\x201px\x20solid
SF:\x20#EEE;\n\x20\x20\x20\x20\x20\x20padding:\x2010px;\n\x20\x20\x20\x20\
SF:x20\x20margin:\x200px;\n\x20\x20\x20\x20\x20\x20width:\x20958px;\n\x20\
SF:x20\x20\x20}\n\n\x20\x20\x20\x20header\x20{\n\x20\x20\x20\x20\x20\x20co
SF:lor:\x20#F0F0F0;\n\x20\x20\x20\x20\x20\x20background:\x20#C52F24;\n\x20
SF:\x20\x20\x20\x20\x20padding:\x200\.5em\x201\.5em;\n\x20\x20\x20\x20}\n\
SF:n\x20\x20\x20\x20h1\x20{\n\x20\x20\x20\x20\x20\x20margin:\x200\.2em\x20
SF:0;\n\x20\x20\x20\x20\x20\x20line-height:\x201\.1em;\n\x20\x20\x20\x20\x
SF:20\x20font-size:\x202em;\n\x20\x20\x20\x20}\n\n\x20\x20\x20\x20h2\x20{\
SF:n\x20\x20\x20\x20\x20\x20color:\x20#C52F24;\n\x20\x20\x20\x20\x20\x20li
SF:ne-height:\x2025px;\n\x20\x20\x20\x20}\n\n\x20\x20\x20\x20\.details\x20
SF:{\n\x20\x20\x20\x20\x20\x20bord");
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=3/5%OT=21%CT=1%CU=43417%PV=Y%DS=2%DC=T%G=Y%TM=64040E62
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=103%GCD=1%ISR=10B%TI=Z%II=I%TS=A)SEQ(SP=10
OS:3%GCD=1%ISR=10B%TI=Z%TS=A)OPS(O1=M54EST11NW7%O2=M54EST11NW7%O3=M54ENNT11
OS:NW7%O4=M54EST11NW7%O5=M54EST11NW7%O6=M54EST11)WIN(W1=FE88%W2=FE88%W3=FE8
OS:8%W4=FE88%W5=FE88%W6=FE88)ECN(R=N)ECN(R=Y%DF=Y%T=40%W=FAF0%O=M54ENNSNW7%
OS:CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=N)T5(R
OS:=N)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=O%F=AR%O=%RD=0%Q=)T6(R=N)T7(R=N)U1(R=Y%DF=
OS:N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%
OS:CD=S)

Uptime guess: 23.165 days (since Fri Feb 10 00:39:33 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=259 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Unix

TRACEROUTE (using port 110/tcp)
HOP RTT       ADDRESS
1   161.85 ms 192.168.49.1
2   161.86 ms 192.168.53.114

NSE: Script Post-scanning.
Initiating NSE at 04:37
Completed NSE at 04:37, 0.00s elapsed
Initiating NSE at 04:37
Completed NSE at 04:37, 0.00s elapsed
Initiating NSE at 04:37
Completed NSE at 04:37, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 499.51 seconds
           Raw packets sent: 72663 (3.202MB) | Rcvd: 71407 (2.860MB)
```
We have 5 ports opened. Port 21 which runs ftp, port 8080&28080 which runs http, port 3306 which runs mysql and port 60022 which runs ssh. Our enumeration will be focused on port 21, port 80 and port 28080.



<h2>Enumeration Port 21</h2>

since anonymous login is allowed, this means we can login with default creds

```username:anonymous```                  ```password:anonymous```

>command: ftp 192.168.53.114

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/nappa]
└─$ ftp 192.168.53.114
Connected to 192.168.53.114.
220 (vsFTPd 3.0.3)
Name (192.168.53.114:bl4ck4non): anonymous
331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls -la
229 Entering Extended Passive Mode (|||10903|)
150 Here comes the directory listing.
dr-xr-xr-x    3 0        11           4096 Nov 06  2020 .
dr-xr-xr-x    3 0        11           4096 Nov 06  2020 ..
drwxr-xr-x   14 14       11           4096 Nov 06  2020 forum
```
I didn't find anything that's going to help us gain access on this server. Moving on with our enumeration



<h2>Enumeration Port 8080</h2>

Going to the webpage, you get this

![image](https://user-images.githubusercontent.com/67879936/222941305-656cbd77-fc21-4c0b-afcf-3ec725c4e471.png)

Lets go ahead and fuzz for directories using ffuf

>command: 






















