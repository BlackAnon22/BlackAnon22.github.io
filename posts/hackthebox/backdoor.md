<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A -T4 -p- -v 10.10.11.125

```
[~] Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-06 00:39 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 00:39
Completed NSE at 00:39, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 00:39
Completed NSE at 00:39, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 00:39
Completed NSE at 00:39, 0.00s elapsed
Initiating Ping Scan at 00:39
Scanning 10.10.11.125 [2 ports]
Completed Ping Scan at 00:39, 0.33s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 00:39
Completed Parallel DNS resolution of 1 host. at 00:39, 0.01s elapsed
DNS resolution of 1 IPs took 0.01s. Mode: Async [#: 1, OK: 0, NX: 1, DR: 0, SF: 0, TR: 1, CN: 0]
Initiating Connect Scan at 00:39
Scanning 10.10.11.125 [3 ports]
Discovered open port 80/tcp on 10.10.11.125
Discovered open port 22/tcp on 10.10.11.125
Discovered open port 1337/tcp on 10.10.11.125
Completed Connect Scan at 00:39, 0.51s elapsed (3 total ports)
Initiating Service scan at 00:39
Scanning 3 services on 10.10.11.125
Completed Service scan at 00:39, 11.61s elapsed (3 services on 1 host)
NSE: Script scanning 10.10.11.125.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 00:39
Completed NSE at 00:39, 21.71s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 00:39
Completed NSE at 00:39, 3.26s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 00:39
Completed NSE at 00:39, 0.00s elapsed
Nmap scan report for 10.10.11.125
Host is up, received syn-ack (0.39s latency).
Scanned at 2023-03-06 00:39:12 WAT for 38s

PORT     STATE SERVICE REASON  VERSION
22/tcp   open  ssh     syn-ack OpenSSH 8.2p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 b4de43384657db4c213b69f3db3c6288 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDqz2EAb2SBSzEIxcu+9dzgUZzDJGdCFWjwuxjhwtpq3sGiUQ1jgwf7h5BE+AlYhSX0oqoOLPKA/QHLxvJ9sYz0ijBL7aEJU8tYHchYMCMu0e8a71p3UGirTjn2tBVe3RSCo/XRQOM/ztrBzlqlKHcqMpttqJHphVA0/1dP7uoLCJlAOOWnW0K311DXkxfOiKRc2izbgfgimMDR4T1C17/oh9355TBgGGg2F7AooUpdtsahsiFItCRkvVB1G7DQiGqRTWsFaKBkHPVMQFaLEm5DK9H7PRwE+UYCah/Wp95NkwWj3u3H93p4V2y0Y6kdjF/L+BRmB44XZXm2Vu7BN0ouuT1SP3zu8YUe3FHshFIml7Ac/8zL1twLpnQ9Hv8KXnNKPoHgrU+sh35cd0JbCqyPFG5yziL8smr7Q4z9/XeATKzL4bcjG87sGtZMtB8alQS7yFA6wmqyWqLFQ4rpi2S0CoslyQnighQSwNaWuBYXvOLi6AsgckJLS44L8LxU4J8=
|   256 aac9fc210f3ef4ec6b3570262253ef66 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBIuoNkiwwo7nM8ZE767bKSHJh+RbMsbItjTbVvKK4xKMfZFHzroaLEe9a2/P1D9h2M6khvPI74azqcqnI8SUJAk=
|   256 d28be4ec0761aacaf8ec1cf88cc1f6e1 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIB7eoJSCw4DyNNaFftGoFcX4Ttpwf+RPo0ydNk7yfqca
80/tcp   open  http    syn-ack Apache httpd 2.4.41 ((Ubuntu))
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-generator: WordPress 5.8.1
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Backdoor &#8211; Real-Life
1337/tcp open  waste?  syn-ack
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 00:39
Completed NSE at 00:39, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 00:39
Completed NSE at 00:39, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 00:39
Completed NSE at 00:39, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 38.03 seconds
```
We have 3 ports opened here, but our enumeration will be focused more on port 80.




<h2>Enumeration</h2>

Going to the webpage should get you this

![image](https://user-images.githubusercontent.com/67879936/222992935-3f0c5502-39ba-48f3-acc0-c36aabacb68e.png)

This webpage is running on wordpress. 

![image](https://user-images.githubusercontent.com/67879936/222995154-0c969ebb-2856-4208-a75c-e3bb957efeb0.png)

Cicking on the home button takes us here

![image](https://user-images.githubusercontent.com/67879936/222995199-ef5bf57d-f70c-44ac-ab78-76c9c2aa3a97.png)

We got a "server not found" error. Lets go ahead and add this IP address to our ```/etc/hosts``` file

>command: sudo nano /etc/hosts

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/backdoor]
└─$ sudo nano /etc/hosts                               
[sudo] password for bl4ck4non: 
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/backdoor]
└─$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       bl4ck4non

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
10.200.84.200 thomaswreath.thm
10.10.11.125 backdoor.htb
```
Now, lets navigate to ```http://backdoor.htb``` 
Lets go ahead and fuzz for directories using ffuf 

>command: ffuf -u "http://10.10.11.125/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/backdoor]
└─$ ffuf -u "http://10.10.11.125/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.11.125/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________
index.php               [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 441ms]
index.php               [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 426ms]
server-status           [Status: 403, Size: 277, Words: 20, Lines: 10, Duration: 282ms]
wp-admin                [Status: 301, Size: 315, Words: 20, Lines: 10, Duration: 231ms]
wp-blog-header.php      [Status: 200, Size: 0, Words: 1, Lines: 1, Duration: 318ms]
wp-content              [Status: 301, Size: 317, Words: 20, Lines: 10, Duration: 201ms]
wp-config.php           [Status: 200, Size: 0, Words: 1, Lines: 1, Duration: 300ms]
wp-cron.php             [Status: 200, Size: 0, Words: 1, Lines: 1, Duration: 253ms]
wp-includes             [Status: 301, Size: 318, Words: 20, Lines: 10, Duration: 410ms]
wp-links-opml.php       [Status: 200, Size: 223, Words: 12, Lines: 12, Duration: 296ms]
wp-mail.php             [Status: 403, Size: 2616, Words: 191, Lines: 121, Duration: 294ms]
wp-load.php             [Status: 200, Size: 0, Words: 1, Lines: 1, Duration: 295ms]
wp-login.php            [Status: 200, Size: 5674, Words: 282, Lines: 99, Duration: 329ms]
wp-signup.php           [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 511ms]
wp-settings.php         [Status: 500, Size: 0, Words: 1, Lines: 1, Duration: 511ms]
wp-trackback.php        [Status: 200, Size: 135, Words: 11, Lines: 5, Duration: 397ms]
xmlrpc.php              [Status: 405, Size: 42, Words: 6, Lines: 1, Duration: 403ms]
xmlrpc.php              [Status: 405, Size: 42, Words: 6, Lines: 1, Duration: 506ms]
:: Progress: [32298/32298] :: Job [1/1] :: 108 req/sec :: Duration: [0:06:54] :: Errors: 240 ::
```
Since we know the webpage is running on wordpress, lets use the wpscan tool to enumerate the webpage for users, themes and plugins





























