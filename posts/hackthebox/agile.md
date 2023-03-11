<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 10.10.11.203 -p- -v -T4

```
[~] Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-11 10:51 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 10:51
Completed NSE at 10:51, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 10:51
Completed NSE at 10:51, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 10:51
Completed NSE at 10:51, 0.00s elapsed
Initiating Ping Scan at 10:51
Scanning 10.10.11.203 [2 ports]
Completed Ping Scan at 10:51, 0.23s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 10:51
Completed Parallel DNS resolution of 1 host. at 10:51, 0.05s elapsed
DNS resolution of 1 IPs took 0.05s. Mode: Async [#: 1, OK: 0, NX: 1, DR: 0, SF: 0, TR: 1, CN: 0]
Initiating Connect Scan at 10:51
Scanning 10.10.11.203 [2 ports]
Discovered open port 80/tcp on 10.10.11.203
Discovered open port 22/tcp on 10.10.11.203
Completed Connect Scan at 10:51, 0.34s elapsed (2 total ports)
Initiating Service scan at 10:51
Scanning 2 services on 10.10.11.203
Completed Service scan at 10:51, 6.53s elapsed (2 services on 1 host)
NSE: Script scanning 10.10.11.203.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 10:51
Completed NSE at 10:51, 7.17s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 10:51
Completed NSE at 10:51, 1.13s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 10:51
Completed NSE at 10:51, 0.00s elapsed
Nmap scan report for 10.10.11.203
Host is up, received conn-refused (0.25s latency).
Scanned at 2023-03-11 10:51:17 WAT for 15s

PORT   STATE SERVICE REASON  VERSION
22/tcp open  ssh     syn-ack OpenSSH 8.9p1 Ubuntu 3ubuntu0.1 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   256 f4bcee21d71f1aa26572212d5ba6f700 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBCeVL2Hl8/LXWurlu46JyqOyvUHtAwTrz1EYdY5dXVi9BfpPwsPTf+zzflV+CGdflQRNFKPDS8RJuiXQa40xs9o=
|   256 65c1480d88cbb975a02ca5e6377e5106 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIEcaZPDjlx21ppN0y2dNT1Jb8aPZwfvugIeN6wdUH1cK
80/tcp open  http    syn-ack nginx 1.18.0 (Ubuntu)
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: nginx/1.18.0 (Ubuntu)
|_http-title: Did not follow redirect to http://superpass.htb
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 10:51
Completed NSE at 10:51, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 10:51
Completed NSE at 10:51, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 10:51
Completed NSE at 10:51, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 16.90 seconds
```
From our scan we have 2 open ports, port 22 which runs ssh and port 80 which runs http. So, our enumeration will be focused more on port 80.



<h2>Enumeration</h2>

Going to the webpage, you should have this

![image](https://user-images.githubusercontent.com/67879936/224513895-f38efaaa-0569-49b5-9d15-cc1024442f59.png)

Lets go ahead and add ```superpass.htb``` to our ```/etc/hosts``` file

>command: sudo nano /etc/hosts

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Agile]
└─$ sudo nano /etc/hosts
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Agile]
└─$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       bl4ck4non

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
10.10.11.203 superpass.htb
```
Now, lets revisit the webpage

![image](https://user-images.githubusercontent.com/67879936/224514089-65181b49-5fb6-47b8-80fe-993c7622a5aa.png)

cool, lets go ahead and create and account, then from there we login to the webserver

![image](https://user-images.githubusercontent.com/67879936/224514186-946c7e18-84c0-4ac7-b1e9-d9de02553ae5.png)

![image](https://user-images.githubusercontent.com/67879936/224514208-cc69fb53-78ba-4766-87f3-5cb2fea33bb5.png)

cool, we are logged in. Lets go ahead and fuzz for directories

>command: ffuf -u "http://superpass.htb/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Agile]
└─$ ffuf -u "http://superpass.htb/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://superpass.htb/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

                        [Status: 200, Size: 6128, Words: 2174, Lines: 131, Duration: 580ms]
download                [Status: 302, Size: 249, Words: 18, Lines: 6, Duration: 294ms]
static                  [Status: 301, Size: 178, Words: 6, Lines: 8, Duration: 282ms]
vault                   [Status: 302, Size: 243, Words: 18, Lines: 6, Duration: 582ms]
:: Progress: [32298/32298] :: Job [1/1] :: 51 req/sec :: Duration: [0:03:54] :: Errors: 0 ::
```




























