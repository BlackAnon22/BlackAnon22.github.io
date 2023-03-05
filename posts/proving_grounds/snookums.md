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
From our scan we have 8 opened ports. Port 21 which runs ftp, port 22 which runs ssh, port 80 which runs http, port 111 which runs rpcbind




































