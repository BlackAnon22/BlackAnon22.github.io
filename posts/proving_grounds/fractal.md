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
From our scan we can see 3 opened ports, port 21 which runs ftp, port 22 which runs ssh and port 80 which runs http. Our enumeration will be focused on 






























































