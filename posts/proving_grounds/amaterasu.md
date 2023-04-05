# Recon

## PortScanning

command:```sudo nmap -A 192.168.82.249  -T4  -v -Pn -p-```

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-04-05 23:58 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 23:58
Completed NSE at 23:58, 0.00s elapsed
Initiating NSE at 23:58
Completed NSE at 23:58, 0.00s elapsed
Initiating NSE at 23:58
Completed NSE at 23:58, 0.00s elapsed
Initiating Parallel DNS resolution of 1 host. at 23:58
Completed Parallel DNS resolution of 1 host. at 23:58, 0.04s elapsed
Initiating SYN Stealth Scan at 23:58
Scanning 192.168.82.249 [65535 ports]
Discovered open port 21/tcp on 192.168.82.249
SYN Stealth Scan Timing: About 6.72% done; ETC: 00:06 (0:07:10 remaining)
SYN Stealth Scan Timing: About 21.18% done; ETC: 00:03 (0:03:47 remaining)
Discovered open port 33414/tcp on 192.168.82.249
Discovered open port 40080/tcp on 192.168.82.249
SYN Stealth Scan Timing: About 34.92% done; ETC: 00:02 (0:02:50 remaining)
SYN Stealth Scan Timing: About 50.42% done; ETC: 00:02 (0:01:59 remaining)
SYN Stealth Scan Timing: About 64.35% done; ETC: 00:02 (0:01:24 remaining)
SYN Stealth Scan Timing: About 74.64% done; ETC: 00:02 (0:01:06 remaining)
Discovered open port 25022/tcp on 192.168.82.249
Completed SYN Stealth Scan at 00:02, 231.62s elapsed (65535 total ports)
Initiating Service scan at 00:02
Scanning 4 services on 192.168.82.249
Completed Service scan at 00:03, 95.08s elapsed (4 services on 1 host)
Initiating OS detection (try #1) against 192.168.82.249
Retrying OS detection (try #2) against 192.168.82.249
Initiating Traceroute at 00:03
Completed Traceroute at 00:03, 0.19s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 00:03
Completed Parallel DNS resolution of 2 hosts. at 00:03, 0.07s elapsed
NSE: Script scanning 192.168.82.249.
Initiating NSE at 00:03
NSE: [ftp-bounce] PORT response: 500 Illegal PORT command.
Completed NSE at 00:04, 35.26s elapsed
Initiating NSE at 00:04
Completed NSE at 00:04, 2.38s elapsed
Initiating NSE at 00:04
Completed NSE at 00:04, 0.00s elapsed
Nmap scan report for 192.168.82.249
Host is up (0.17s latency).
Not shown: 65524 filtered tcp ports (no-response)
PORT      STATE  SERVICE          VERSION
21/tcp    open   ftp              vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: TIMEOUT
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to 192.168.49.82
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 3
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
22/tcp    closed ssh
111/tcp   closed rpcbind
139/tcp   closed netbios-ssn
443/tcp   closed https
445/tcp   closed microsoft-ds
2049/tcp  closed nfs
10000/tcp closed snet-sensor-mgmt
25022/tcp open   ssh              OpenSSH 8.6 (protocol 2.0)
| ssh-hostkey: 
|   256 68c605e8dcf29a2a789beea1aef6381a (ECDSA)
|_  256 e989ccc21714f3bc6221064a5e7180ce (ED25519)
33414/tcp open   unknown
| fingerprint-strings: 
|   GetRequest, HTTPOptions: 
|     HTTP/1.1 404 NOT FOUND
|     Server: Werkzeug/2.2.3 Python/3.9.13
|     Date: Wed, 05 Apr 2023 23:02:17 GMT
|     Content-Type: text/html; charset=utf-8
|     Content-Length: 207
|     Connection: close
|     <!doctype html>
|     <html lang=en>
|     <title>404 Not Found</title>
|     <h1>Not Found</h1>
|     <p>The requested URL was not found on the server. If you entered the URL manually please check your spelling and try again.</p>
|   Help: 
|     <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
|     "http://www.w3.org/TR/html4/strict.dtd">
|     <html>
|     <head>
|     <meta http-equiv="Content-Type" content="text/html;charset=utf-8">
|     <title>Error response</title>
|     </head>
|     <body>
|     <h1>Error response</h1>
|     <p>Error code: 400</p>
|     <p>Message: Bad request syntax ('HELP').</p>
|     <p>Error code explanation: HTTPStatus.BAD_REQUEST - Bad request syntax or unsupported method.</p>
|     </body>
|     </html>
|   RTSPRequest: 
|     <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
|     "http://www.w3.org/TR/html4/strict.dtd">
|     <html>
|     <head>
|     <meta http-equiv="Content-Type" content="text/html;charset=utf-8">
|     <title>Error response</title>
|     </head>
|     <body>
|     <h1>Error response</h1>
|     <p>Error code: 400</p>
|     <p>Message: Bad request version ('RTSP/1.0').</p>
|     <p>Error code explanation: HTTPStatus.BAD_REQUEST - Bad request syntax or unsupported method.</p>
|     </body>
|_    </html>
40080/tcp open   http             Apache httpd 2.4.53 ((Fedora))
| http-methods: 
|   Supported Methods: GET POST OPTIONS HEAD TRACE
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/2.4.53 (Fedora)
|_http-title: My test page
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port33414-TCP:V=7.93%I=7%D=4/6%Time=642DFDFD%P=x86_64-pc-linux-gnu%r(Ge
SF:tRequest,184,"HTTP/1\.1\x20404\x20NOT\x20FOUND\r\nServer:\x20Werkzeug/2
SF:\.2\.3\x20Python/3\.9\.13\r\nDate:\x20Wed,\x2005\x20Apr\x202023\x2023:0
SF:2:17\x20GMT\r\nContent-Type:\x20text/html;\x20charset=utf-8\r\nContent-
SF:Length:\x20207\r\nConnection:\x20close\r\n\r\n<!doctype\x20html>\n<html
SF:\x20lang=en>\n<title>404\x20Not\x20Found</title>\n<h1>Not\x20Found</h1>
SF:\n<p>The\x20requested\x20URL\x20was\x20not\x20found\x20on\x20the\x20ser
SF:ver\.\x20If\x20you\x20entered\x20the\x20URL\x20manually\x20please\x20ch
SF:eck\x20your\x20spelling\x20and\x20try\x20again\.</p>\n")%r(HTTPOptions,
SF:184,"HTTP/1\.1\x20404\x20NOT\x20FOUND\r\nServer:\x20Werkzeug/2\.2\.3\x2
SF:0Python/3\.9\.13\r\nDate:\x20Wed,\x2005\x20Apr\x202023\x2023:02:17\x20G
SF:MT\r\nContent-Type:\x20text/html;\x20charset=utf-8\r\nContent-Length:\x
SF:20207\r\nConnection:\x20close\r\n\r\n<!doctype\x20html>\n<html\x20lang=
SF:en>\n<title>404\x20Not\x20Found</title>\n<h1>Not\x20Found</h1>\n<p>The\
SF:x20requested\x20URL\x20was\x20not\x20found\x20on\x20the\x20server\.\x20
SF:If\x20you\x20entered\x20the\x20URL\x20manually\x20please\x20check\x20yo
SF:ur\x20spelling\x20and\x20try\x20again\.</p>\n")%r(RTSPRequest,1F4,"<!DO
SF:CTYPE\x20HTML\x20PUBLIC\x20\"-//W3C//DTD\x20HTML\x204\.01//EN\"\n\x20\x
SF:20\x20\x20\x20\x20\x20\x20\"http://www\.w3\.org/TR/html4/strict\.dtd\">
SF:\n<html>\n\x20\x20\x20\x20<head>\n\x20\x20\x20\x20\x20\x20\x20\x20<meta
SF:\x20http-equiv=\"Content-Type\"\x20content=\"text/html;charset=utf-8\">
SF:\n\x20\x20\x20\x20\x20\x20\x20\x20<title>Error\x20response</title>\n\x2
SF:0\x20\x20\x20</head>\n\x20\x20\x20\x20<body>\n\x20\x20\x20\x20\x20\x20\
SF:x20\x20<h1>Error\x20response</h1>\n\x20\x20\x20\x20\x20\x20\x20\x20<p>E
SF:rror\x20code:\x20400</p>\n\x20\x20\x20\x20\x20\x20\x20\x20<p>Message:\x
SF:20Bad\x20request\x20version\x20\('RTSP/1\.0'\)\.</p>\n\x20\x20\x20\x20\
SF:x20\x20\x20\x20<p>Error\x20code\x20explanation:\x20HTTPStatus\.BAD_REQU
SF:EST\x20-\x20Bad\x20request\x20syntax\x20or\x20unsupported\x20method\.</
SF:p>\n\x20\x20\x20\x20</body>\n</html>\n")%r(Help,1EF,"<!DOCTYPE\x20HTML\
SF:x20PUBLIC\x20\"-//W3C//DTD\x20HTML\x204\.01//EN\"\n\x20\x20\x20\x20\x20
SF:\x20\x20\x20\"http://www\.w3\.org/TR/html4/strict\.dtd\">\n<html>\n\x20
SF:\x20\x20\x20<head>\n\x20\x20\x20\x20\x20\x20\x20\x20<meta\x20http-equiv
SF:=\"Content-Type\"\x20content=\"text/html;charset=utf-8\">\n\x20\x20\x20
SF:\x20\x20\x20\x20\x20<title>Error\x20response</title>\n\x20\x20\x20\x20<
SF:/head>\n\x20\x20\x20\x20<body>\n\x20\x20\x20\x20\x20\x20\x20\x20<h1>Err
SF:or\x20response</h1>\n\x20\x20\x20\x20\x20\x20\x20\x20<p>Error\x20code:\
SF:x20400</p>\n\x20\x20\x20\x20\x20\x20\x20\x20<p>Message:\x20Bad\x20reque
SF:st\x20syntax\x20\('HELP'\)\.</p>\n\x20\x20\x20\x20\x20\x20\x20\x20<p>Er
SF:ror\x20code\x20explanation:\x20HTTPStatus\.BAD_REQUEST\x20-\x20Bad\x20r
SF:equest\x20syntax\x20or\x20unsupported\x20method\.</p>\n\x20\x20\x20\x20
SF:</body>\n</html>\n");
Aggressive OS guesses: Linux 2.6.32 (88%), Linux 2.6.32 or 3.10 (88%), Linux 2.6.39 (88%), Linux 3.10 - 3.12 (88%), Linux 4.4 (88%), Synology DiskStation Manager 5.1 (88%), Linux 2.6.35 (87%), Linux 4.9 (87%), Linux 3.4 (87%), Linux 3.5 (87%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 36.235 days (since Tue Feb 28 18:26:03 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=256 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Unix

TRACEROUTE (using port 22/tcp)
HOP RTT       ADDRESS
1   177.40 ms 192.168.49.1
2   177.40 ms 192.168.82.249

NSE: Script Post-scanning.
Initiating NSE at 00:04
Completed NSE at 00:04, 0.00s elapsed
Initiating NSE at 00:04
Completed NSE at 00:04, 0.00s elapsed
Initiating NSE at 00:04
Completed NSE at 00:04, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 372.64 seconds
           Raw packets sent: 131297 (5.781MB) | Rcvd: 198 (8.860KB)
```
From the above scan we see that we have 4 ports opened. Port 21 which runs ftp, port 25022 which runs ssh, port 33414 (service is unknown) and port 40080 which runs http. We'll be starting our enumeration from port 21.

# Enumeration (Port 21)

Since Anonymous login is allowed, this means we can login using default credentials

```username:anonymous```                    ```password:anonymous```

command:```ftp 192.168.120.249```

![image](https://user-images.githubusercontent.com/67879936/230232998-7e795c8d-0b02-4f9a-8d8b-394600ae1837.png)

As you can see, from the above screenshot we logged in successfully but when we try to view files nothing is displayed.

Since we can't get directory listing lets move on to the next port



# Enumeration (Port 40080)

Navigating to the webpage should get you this

![image](https://user-images.githubusercontent.com/67879936/230233696-43760bb2-26d7-44d8-add0-a53658fbaa80.png)

























