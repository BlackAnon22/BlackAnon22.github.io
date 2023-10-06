![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e9d55b3b-9ea7-4d15-af83-2346cee4426f)# Box: Keeper
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.10.11.227 -T4  -v -p-```

```
Nmap scan report for 10.10.11.227
Host is up (0.22s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   256 3539d439404b1f6186dd7c37bb4b989e (ECDSA)
|_  256 1ae972be8bb105d5effedd80d8efc066 (ED25519)
80/tcp open  http    nginx 1.18.0 (Ubuntu)
|_http-title: Site doesn't have a title (text/html).
| http-methods: 
|_  Supported Methods: GET HEAD
|_http-server-header: nginx/1.18.0 (Ubuntu)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=10/6%OT=22%CT=1%CU=38405%PV=Y%DS=2%DC=T%G=Y%TM=651F768
OS:9%P=x86_64-pc-linux-gnu)SEQ(SP=FB%GCD=1%ISR=102%TI=Z%CI=Z%II=I%TS=A)OPS(
OS:O1=M539ST11NW7%O2=M539ST11NW7%O3=M539NNT11NW7%O4=M539ST11NW7%O5=M539ST11
OS:NW7%O6=M539ST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN(
OS:R=Y%DF=Y%T=40%W=FAF0%O=M539NNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS
OS:%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=
OS:Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=
OS:R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T
OS:=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=
OS:S)

Uptime guess: 0.697 days (since Thu Oct  5 11:09:39 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=251 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 8888/tcp)
HOP RTT       ADDRESS
1   298.26 ms 10.10.14.1
2   298.28 ms 10.10.11.227

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Fri Oct  6 03:52:57 2023 -- 1 IP address (1 host up) scanned in 784.92 seconds
```
From our above scan we have 2 open ports, port 22 which runs the ssh service and port 80 which runs the http service. Our enumeration today will be focused on port 80.



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/515e7e93-59dc-49a3-849e-94b0addc3cf4)

Lets add that subdomain ```tickets.keeper.htb``` to our ```/etc/hosts``` file

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/keeper]
└─$ sudo nano /etc/hosts                                                                                    
[sudo] password for bl4ck4non: 
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/keeper]
└─$ cat /etc/hosts            
127.0.0.1       localhost
127.0.1.1       bl4ck4non

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

10.10.11.227 tickets.keeper.htb
```
cool, now lets navigate to that subdomain

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/45b62909-bbbf-4145-a11b-8282a5d18a79)

okay, we got a login page

Lets try to login with default creds to see what happens

username:```admin```        password:```password```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3643f82e-9bea-469b-b52d-c39caf6a533d)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ee58cf2a-f0a9-489c-9613-8692f1d36577)

oops, it didn't work

If you take a look at the login page well, you'll see this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/90c1889e-eb65-4fb0-afd4-089a0642afbb)

Doing my research, I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2ece7152-cf04-421d-9e37-29579f8a192b)

Lets login using those creds

username:```root```         password:```password```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d2606754-d0ef-4bc5-a261-410991edff59)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a0c2c43c-163f-483f-8104-34abf718b0b9)

Now, you can see we aren't logged in, we aren't also getting the login error that shows that either or username or password is incorrect.

At this point I had to use burpsuite to analyze the request

Lets capture the login request on burpsuite










