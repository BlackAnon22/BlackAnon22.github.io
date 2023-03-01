<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 192.168.82.71 -p- -T4 -v

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-01 16:13 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 16:13
Completed NSE at 16:13, 0.00s elapsed
Initiating NSE at 16:13
Completed NSE at 16:13, 0.00s elapsed
Initiating NSE at 16:13
Completed NSE at 16:13, 0.00s elapsed
Initiating Ping Scan at 16:13
Scanning 192.168.82.71 [4 ports]
Completed Ping Scan at 16:13, 0.29s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 16:13
Completed Parallel DNS resolution of 1 host. at 16:13, 0.03s elapsed
Initiating SYN Stealth Scan at 16:13
Scanning 192.168.82.71 [65535 ports]
Discovered open port 445/tcp on 192.168.82.71
Discovered open port 25/tcp on 192.168.82.71
Discovered open port 80/tcp on 192.168.82.71
Discovered open port 22/tcp on 192.168.82.71
SYN Stealth Scan Timing: About 6.04% done; ETC: 16:22 (0:08:02 remaining)
SYN Stealth Scan Timing: About 19.79% done; ETC: 16:18 (0:04:07 remaining)
SYN Stealth Scan Timing: About 34.38% done; ETC: 16:17 (0:02:54 remaining)
SYN Stealth Scan Timing: About 46.32% done; ETC: 16:17 (0:02:20 remaining)
SYN Stealth Scan Timing: About 57.98% done; ETC: 16:17 (0:01:49 remaining)
SYN Stealth Scan Timing: About 71.94% done; ETC: 16:17 (0:01:11 remaining)
Completed SYN Stealth Scan at 16:17, 242.39s elapsed (65535 total ports)
Initiating Service scan at 16:17
Scanning 4 services on 192.168.82.71
Completed Service scan at 16:17, 6.56s elapsed (4 services on 1 host)
Initiating OS detection (try #1) against 192.168.82.71
Retrying OS detection (try #2) against 192.168.82.71
Initiating Traceroute at 16:17
Completed Traceroute at 16:17, 0.27s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 16:17
Completed Parallel DNS resolution of 2 hosts. at 16:17, 0.06s elapsed
NSE: Script scanning 192.168.82.71.
Initiating NSE at 16:17
Completed NSE at 16:18, 40.22s elapsed
Initiating NSE at 16:18
Completed NSE at 16:18, 1.68s elapsed
Initiating NSE at 16:18
Completed NSE at 16:18, 0.00s elapsed
Nmap scan report for 192.168.82.71
Host is up (0.22s latency).
Not shown: 65530 filtered tcp ports (no-response)
PORT    STATE  SERVICE     VERSION
22/tcp  open   ssh         OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 dbdd2cea2f85c589bcfce9a338f0d750 (RSA)
|   256 e3b765c2a78e4529bb62ec301aebed6d (ECDSA)
|_  256 d55b795bce48d85746db594fcd455def (ED25519)
25/tcp  open   smtp        OpenSMTPD
| smtp-commands: bratarina Hello nmap.scanme.org [192.168.49.82], pleased to meet you, 8BITMIME, ENHANCEDSTATUSCODES, SIZE 36700160, DSN, HELP
|_ 2.0.0 This is OpenSMTPD 2.0.0 To report bugs in the implementation, please contact bugs@openbsd.org 2.0.0 with full details 2.0.0 End of HELP info
53/tcp  closed domain
80/tcp  open   http        nginx 1.14.0 (Ubuntu)
|_http-title:         Page not found - FlaskBB        
|_http-server-header: nginx/1.14.0 (Ubuntu)
445/tcp open   netbios-ssn Samba smbd 4.7.6-Ubuntu (workgroup: COFFEECORP)
Aggressive OS guesses: Linux 2.6.32 (88%), Linux 2.6.39 (88%), Linux 3.10 - 3.12 (88%), Linux 3.4 (88%), Linux 3.5 (88%), Linux 4.4 (88%), Synology DiskStation Manager 5.1 (88%), Linux 2.6.35 (87%), Linux 3.10 (87%), Linux 2.6.32 or 3.10 (87%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 26.225 days (since Fri Feb  3 10:53:46 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=263 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: Host: bratarina; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_clock-skew: mean: 1h40m01s, deviation: 2h53m14s, median: 0s
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb-os-discovery: 
|   OS: Windows 6.1 (Samba 4.7.6-Ubuntu)
|   Computer name: bratarina
|   NetBIOS computer name: BRATARINA\x00
|   Domain name: \x00
|   FQDN: bratarina
|_  System time: 2023-03-01T10:17:45-05:00
| smb2-time: 
|   date: 2023-03-01T15:17:43
|_  start_date: N/A
| smb2-security-mode: 
|   311: 
|_    Message signing enabled but not required

TRACEROUTE (using port 53/tcp)
HOP RTT       ADDRESS
1   261.97 ms 192.168.49.1
2   262.34 ms 192.168.82.71

NSE: Script Post-scanning.
Initiating NSE at 16:18
Completed NSE at 16:18, 0.00s elapsed
Initiating NSE at 16:18
Completed NSE at 16:18, 0.00s elapsed
Initiating NSE at 16:18
Completed NSE at 16:18, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 297.78 seconds
           Raw packets sent: 131317 (5.782MB) | Rcvd: 206 (9.112KB)

```
From the above scan we have 3 ports opened, port 22 which runs ssh, port 25 which runs smtp and port 80 which runs http. Our enumeration today will be focused more on port 25 and port 80


<h2>Enumeration Port 25</h2>


























