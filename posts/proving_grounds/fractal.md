<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A -T4 -p- -v

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-05 01:25 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 01:25
Completed NSE at 01:25, 0.00s elapsed
Initiating NSE at 01:25
Completed NSE at 01:25, 0.00s elapsed
Initiating NSE at 01:25
Completed NSE at 01:25, 0.00s elapsed
Initiating Ping Scan at 01:25
Scanning 192.168.53.233 [4 ports]
Completed Ping Scan at 01:25, 0.20s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 01:25
Completed Parallel DNS resolution of 1 host. at 01:25, 0.04s elapsed
Initiating SYN Stealth Scan at 01:25
Scanning 192.168.53.233 [65535 ports]
Discovered open port 22/tcp on 192.168.53.233
Discovered open port 80/tcp on 192.168.53.233
Discovered open port 21/tcp on 192.168.53.233
SYN Stealth Scan Timing: About 4.39% done; ETC: 01:37 (0:11:15 remaining)
SYN Stealth Scan Timing: About 10.77% done; ETC: 01:35 (0:08:25 remaining)
Increasing send delay for 192.168.53.233 from 0 to 5 due to max_successful_tryno increase to 5
SYN Stealth Scan Timing: About 18.26% done; ETC: 01:35 (0:07:54 remaining)
SYN Stealth Scan Timing: About 26.49% done; ETC: 01:35 (0:07:24 remaining)
SYN Stealth Scan Timing: About 33.78% done; ETC: 01:36 (0:06:54 remaining)
SYN Stealth Scan Timing: About 39.23% done; ETC: 01:36 (0:06:23 remaining)
SYN Stealth Scan Timing: About 45.23% done; ETC: 01:36 (0:05:50 remaining)
SYN Stealth Scan Timing: About 50.39% done; ETC: 01:36 (0:05:17 remaining)
SYN Stealth Scan Timing: About 56.29% done; ETC: 01:36 (0:04:43 remaining)
SYN Stealth Scan Timing: About 61.96% done; ETC: 01:36 (0:04:09 remaining)
SYN Stealth Scan Timing: About 67.62% done; ETC: 01:36 (0:03:35 remaining)
SYN Stealth Scan Timing: About 73.18% done; ETC: 01:36 (0:03:00 remaining)
SYN Stealth Scan Timing: About 78.36% done; ETC: 01:36 (0:02:24 remaining)
SYN Stealth Scan Timing: About 83.57% done; ETC: 01:36 (0:01:50 remaining)
SYN Stealth Scan Timing: About 88.93% done; ETC: 01:36 (0:01:15 remaining)
SYN Stealth Scan Timing: About 94.05% done; ETC: 01:37 (0:00:41 remaining)
Completed SYN Stealth Scan at 01:37, 704.77s elapsed (65535 total ports)
Initiating Service scan at 01:37
Scanning 3 services on 192.168.53.233
Completed Service scan at 01:37, 11.76s elapsed (3 services on 1 host)
Initiating OS detection (try #1) against 192.168.53.233
Retrying OS detection (try #2) against 192.168.53.233
Initiating Traceroute at 01:37
Completed Traceroute at 01:37, 0.24s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 01:37
Completed Parallel DNS resolution of 2 hosts. at 01:37, 0.07s elapsed
NSE: Script scanning 192.168.53.233.
Initiating NSE at 01:37
Completed NSE at 01:37, 5.19s elapsed
Initiating NSE at 01:37
Completed NSE at 01:37, 1.26s elapsed
Initiating NSE at 01:37
Completed NSE at 01:37, 0.00s elapsed
Nmap scan report for 192.168.53.233
Host is up (0.19s latency).
Not shown: 64513 closed tcp ports (reset), 1019 filtered tcp ports (no-response)
PORT   STATE SERVICE VERSION
21/tcp open  ftp     ProFTPD
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 c1994b952225ed0f8520d363b448bbcf (RSA)
|   256 0f448badad95b8226af036ac19d00ef3 (ECDSA)
|_  256 32e12a6ccc7ce63e23f4808d33ce9b3a (ED25519)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
| http-robots.txt: 2 disallowed entries 
|_/app_dev.php /app_dev.php/*
|_http-title: Welcome!
|_http-favicon: Unknown favicon MD5: 231567A8CC45C2CF966C4E8D99A5B7FD
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.41 (Ubuntu)
Aggressive OS guesses: Linux 2.6.32 (88%), Linux 3.4 (88%), Linux 3.5 (88%), Linux 4.2 (88%), Linux 4.4 (88%), Synology DiskStation Manager 5.1 (88%), WatchGuard Fireware 11.8 (88%), Linux 2.6.35 (87%), Linux 3.10 (87%), Linux 2.6.32 or 3.10 (87%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 28.827 days (since Sat Feb  4 05:46:53 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=261 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 3306/tcp)
HOP RTT       ADDRESS
1   226.52 ms 192.168.49.1
2   226.51 ms 192.168.53.233

NSE: Script Post-scanning.
Initiating NSE at 01:37
Completed NSE at 01:37, 0.00s elapsed
Initiating NSE at 01:37
Completed NSE at 01:37, 0.00s elapsed
Initiating NSE at 01:37
Completed NSE at 01:37, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 729.77 seconds
           Raw packets sent: 78217 (3.445MB) | Rcvd: 70971 (2.840MB)

```
From our scan we can see 3 opened ports, port 21 which runs ftp, port 22 which runs ssh and port 80 which runs http. Our enumeration will be focused on port 21 and port 80.




<h2>Enumeration Port 21</h2>

The version of this ftp service is proftpd, we didn't get the version so we can't look for available exploits. Also, anonymous login isn't allowed so we really can't do much. Lets move on to the next port.




<h2>Enumeration Port 80</h2>

Going to the webpage you should get this

![image](https://user-images.githubusercontent.com/67879936/222935655-0624f8ed-c040-45b1-9e04-6cb0e7b7c887.png)

Lets  search for hidden directories using ffuf

>command: ffuf -u "http://192.168.53.233/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Fractal]
└─$ ffuf -u "http://192.168.53.233/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://192.168.53.233/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________
app.php                 [Status: 301, Size: 310, Words: 20, Lines: 10, Duration: 327ms]
config.php              [Status: 403, Size: 46, Words: 7, Lines: 1, Duration: 207ms]
css                     [Status: 301, Size: 314, Words: 20, Lines: 10, Duration: 133ms]
favicon.ico             [Status: 200, Size: 6518, Words: 36, Lines: 18, Duration: 199ms]
img                     [Status: 301, Size: 314, Words: 20, Lines: 10, Duration: 245ms]
javascript              [Status: 301, Size: 321, Words: 20, Lines: 10, Duration: 216ms]
js                      [Status: 301, Size: 313, Words: 20, Lines: 10, Duration: 143ms]
phpmyadmin              [Status: 301, Size: 321, Words: 20, Lines: 10, Duration: 145ms]
robots.txt              [Status: 200, Size: 86, Words: 7, Lines: 4, Duration: 168ms]
server-status           [Status: 403, Size: 279, Words: 20, Lines: 10, Duration: 148ms]
:: Progress: [32298/32298] :: Job [1/1] :: 283 req/sec :: Duration: [0:02:35] :: Errors: 0 ::
```
cool, we got some directories to check. Going to _/robots.txt_ we find another directory there

![image](https://user-images.githubusercontent.com/67879936/222936078-d0d3db42-f6ac-4be1-a737-ca211f2d13c3.png)

Lets navigate to the _/app_dev.php_ directory

![image](https://user-images.githubusercontent.com/67879936/222936139-43526fae-60f9-4b08-b9b6-7beee719ea0d.png)































































