<h2>Recon</h2>
<h3>PortScan</h3>

>command used:sudo nmap -A -p- -T4 -v 

```
# Nmap 7.93 scan initiated Thu Feb  2 08:44:49 2023 as: nmap -A -v -T4 -oN wheels 192.168.102.202
Nmap scan report for 192.168.102.202
Host is up (0.25s latency).
Not shown: 998 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.4 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 c1994b952225ed0f8520d363b448bbcf (RSA)
|   256 0f448badad95b8226af036ac19d00ef3 (ECDSA)
|_  256 32e12a6ccc7ce63e23f4808d33ce9b3a (ED25519)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Wheels - Car Repair Services
| http-methods: 
|_  Supported Methods: GET POST OPTIONS HEAD
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=2/2%OT=22%CT=1%CU=31940%PV=Y%DS=2%DC=T%G=Y%TM=63DB6A18
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=105%GCD=1%ISR=109%TI=Z%II=I%TS=A)OPS(O1=M5
OS:4EST11NW7%O2=M54EST11NW7%O3=M54ENNT11NW7%O4=M54EST11NW7%O5=M54EST11NW7%O
OS:6=M54EST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN(R=Y%D
OS:F=Y%T=40%W=FAF0%O=M54ENNSNW7%CC=Y%Q=)ECN(R=N)T1(R=Y%DF=Y%T=40%S=O%A=S+%F
OS:=AS%RD=0%Q=)T1(R=N)T2(R=N)T3(R=N)T4(R=N)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=
OS:AR%O=%RD=0%Q=)T5(R=N)T6(R=N)T7(R=N)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%
OS:RID=G%RIPCK=G%RUCK=G%RUD=G)U1(R=N)IE(R=Y%DFI=N%T=40%CD=S)IE(R=N)

Network Distance: 2 hops
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 443/tcp)
HOP RTT       ADDRESS
1   268.27 ms 192.168.49.1
2   268.31 ms 192.168.102.202

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Thu Feb  2 08:45:28 2023 -- 1 IP address (1 host up) scanned in 39.09 seconds
```
We have 2 ports opened here, port 22 which runs ssh and port 80 which runs http. So, our enumeration will be focused more on port 80.


<h2>Enumeration</h2>

Going to the webpage should get you this

![image](https://user-images.githubusercontent.com/67879936/222130410-04fcecfc-fcf6-43dc-a46e-1b1b50a3b401.png)

This web page runs a Wheels CarService, lets try to register an account to see if we can login to the web application

![image](https://user-images.githubusercontent.com/67879936/222131549-907be999-ab3c-4b0a-95fc-25c56765e67c.png)

Now, lets try to login after creating our account

![image](https://user-images.githubusercontent.com/67879936/222132098-077cb8a7-d253-48eb-b64c-cdad86ec3b1c.png)

But clicking on the login button doesn't log us is but redirects us to the home page

![image](https://user-images.githubusercontent.com/67879936/222132237-52fd9ca8-e35c-471d-8298-40eb326bc6ec.png)

Looking at the footer of the webpage

![image](https://user-images.githubusercontent.com/67879936/222133059-69501d18-14e5-4254-9c96-306c83d696e0.png)

The email here is _info@wheels.service_ lets go ahead and copy this same format for our mail since the mail won't get any verification code or link

![image](https://user-images.githubusercontent.com/67879936/222133634-42b4ff0c-021a-4f1e-90de-dbbaa3a20071.png)

Now, lets try to login

![image](https://user-images.githubusercontent.com/67879936/222133973-0e55cdf8-571a-41f8-9d37-6b7d3355ff08.png)





















