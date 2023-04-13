<h2>Recon</h2>

<h3>PortScanning</h3>

command:```sudo nmap -A 10.10.134.162 -p- -T4 -v```

```
[~] Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-11 08:24 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 08:24
Completed NSE at 08:24, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 08:24
Completed NSE at 08:24, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 08:24
Completed NSE at 08:24, 0.00s elapsed
Initiating Ping Scan at 08:24
Scanning 10.10.134.162 [2 ports]
Completed Ping Scan at 08:24, 0.28s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 08:24
Completed Parallel DNS resolution of 1 host. at 08:24, 0.21s elapsed
DNS resolution of 1 IPs took 0.21s. Mode: Async [#: 1, OK: 0, NX: 1, DR: 0, SF: 0, TR: 1, CN: 0]
Initiating Connect Scan at 08:24
Scanning 10.10.134.162 [2 ports]
Discovered open port 22/tcp on 10.10.134.162
Discovered open port 8001/tcp on 10.10.134.162
Completed Connect Scan at 08:24, 0.41s elapsed (2 total ports)
Initiating Service scan at 08:24
Scanning 2 services on 10.10.134.162
Completed Service scan at 08:24, 6.67s elapsed (2 services on 1 host)
NSE: Script scanning 10.10.134.162.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 08:24
Completed NSE at 08:24, 8.63s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 08:24
Completed NSE at 08:24, 0.81s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 08:24
Completed NSE at 08:24, 0.00s elapsed
Nmap scan report for 10.10.134.162
Host is up, received conn-refused (0.31s latency).
Scanned at 2023-03-11 08:24:19 WAT for 17s

PORT     STATE SERVICE REASON  VERSION
22/tcp   open  ssh     syn-ack OpenSSH 7.2p2 Ubuntu 4ubuntu2.10 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 8abf6b1e93717c990459d38d8104af46 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCicax/djwvuiP5H2ET5UJCYL3Kp7ukHPJ0YWsSBUc6o8O/wwzOkz82yJRrZAff40NmLEpbvf0Sxw2JhrtoxDmdj+FSHpV/xDUG/nRE0FU10wDB75fYP4VFKR8QbzwDu6fxkgkZ3SAWZ9R1MgjN3B49hywgwqMRNtw+z2r2rXeF56y1FFKotBtK1wA223dJ8BLE+lRkAZd4nOr5HFMwrO+kWgYzfYJgSQ+5LEH4E/X7vWGqjdBIHSoYOUvzGJJmCum2/MOQPoDw5B85Naw/aMQqsv7WM1mnTA34Z2eTO23HCKku5+Snf5amqVwHv8AfOFub0SS7AVfbIyP9fwv1psbP
|   256 40fd0cfc0ba8f52db12e3481e5c7a591 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBENyLKEyFWN1XPyR2L1nyEK5QiqJAZTV2ntHTCZqMtXKkjsDM5H7KPJ5EcYg5Rp1zPzaDZxBmPP0pDF1Rhko7sw=
|   256 7b3997f06c8aba385f487bccda72a844 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIJmb0JdTeq8kjq+30Ztv/xe3wY49Jhc60LHfPd5yGiRx
8001/tcp open  http    syn-ack Apache httpd 2.4.18 ((Ubuntu))
| http-methods: 
|_  Supported Methods: POST OPTIONS GET HEAD
|_http-title: En-Pass
|_http-server-header: Apache/2.4.18 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 08:24
Completed NSE at 08:24, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 08:24
Completed NSE at 08:24, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 08:24
Completed NSE at 08:24, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 18.79 seconds
```
From our scan we have 2 open ports. Port 22 which runs ssh and port 8001 which runs http. Our enumeration today will be focused  on port 8001.



<h2>Enumeration</h2>

Going to the webpage should get you this

![image](https://user-images.githubusercontent.com/67879936/224471509-f98e2e33-4ec3-4f06-ac99-9177ba7f0656.png)

Lets go ahead and fire up ffuf to help us search for directories

command:```ffuf -u "http://10.10.134.162:8001/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Enpass]
└─$ ffuf -u "http://10.10.134.162:8001/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.134.162:8001/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

                        [Status: 200, Size: 2563, Words: 365, Lines: 68, Duration: 306ms]
403.php                 [Status: 403, Size: 1123, Words: 287, Lines: 87, Duration: 382ms]
index.html              [Status: 200, Size: 2563, Words: 365, Lines: 68, Duration: 175ms]
reg.php                 [Status: 200, Size: 2417, Words: 665, Lines: 171, Duration: 162ms]
server-status           [Status: 403, Size: 280, Words: 20, Lines: 10, Duration: 536ms]
web                     [Status: 301, Size: 319, Words: 20, Lines: 10, Duration: 272ms]
zip                     [Status: 301, Size: 319, Words: 20, Lines: 10, Duration: 160ms]
:: Progress: [32298/32298] :: Job [1/1] :: 230 req/sec :: Duration: [0:03:25] :: Errors: 0 ::

```






















