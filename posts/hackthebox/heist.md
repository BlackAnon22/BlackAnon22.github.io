# Box Name: Heist
# Level: Easy
# OS: Windows
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.129.96.157 -p- -v -T4```

```
Nmap scan report for 10.129.96.157
Host is up (0.40s latency).
Not shown: 65530 filtered tcp ports (no-response)
PORT      STATE SERVICE       VERSION
80/tcp    open  http          Microsoft IIS httpd 10.0
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
| http-title: Support Login Page
|_Requested resource was login.php
135/tcp   open  msrpc         Microsoft Windows RPC
445/tcp   open  microsoft-ds?
5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-title: Not Found
49669/tcp open  unknown
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
OS fingerprint not ideal because: Missing a closed TCP port so results incomplete
No OS matches for host
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=264 (Good luck!)
IP ID Sequence Generation: Randomized
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2023-10-10T19:48:09
|_  start_date: N/A
|_clock-skew: -1s

TRACEROUTE (using port 445/tcp)
HOP RTT       ADDRESS
1   339.57 ms 10.10.16.1
2   340.07 ms 10.129.96.157

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Tue Oct 10 20:48:49 2023 -- 1 IP address (1 host up) scanned in 436.02 seconds
```
From our nmap scan we have quite a number of ports opened. We'll start our enumeration today from port 80



# Enumeration (Port 80)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2bc80794-25ca-4678-a4fb-5ca4fb869bb6)

We get this login page



























