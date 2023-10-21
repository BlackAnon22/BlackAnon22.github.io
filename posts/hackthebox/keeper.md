# Box: Keeper
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

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8ebb3073-989d-4be5-8c12-87c221540241)

okay, we got a login page

Lets try to login with default creds to see what happens

username:```admin```        password:```password```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bc08d222-ba29-410b-82b0-ee3faf1f61ce)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d77123d1-cafb-4a7f-bb37-4e738a5034ed)

oops, it didn't work

If you take a look at the login page well, you'll see this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/217b2ab6-fe5b-4d66-8298-1064665fbceb)

```rt``` basically just means ```request tracker```

Doing my research, I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2ece7152-cf04-421d-9e37-29579f8a192b)

Lets login using those creds

username:```root```         password:```password```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e6925f84-c320-44c0-afb6-ebeada290b14)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/104d62a2-7ba5-4e44-ac86-af4d5228fc3d)

nice nice, we are logged in

Going through the webpage I found something interesting

Click on Admin>Users>Select, you should see this when you do that

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/edccf158-2aa6-4683-9faf-b046d7006a78)

So, we have a user ``` 	lnorgaard```. Click on that user, it should give you more information about the user

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/022ca505-eaa2-44db-86f1-248a8986baff)

We got the password of the user. Lets use this to ssh into the server

username:```lnorgaard```      password:```Welcome2023!```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4a39d96d-0d7c-45e2-9be0-c1682f7365dc)

cool, we are in. Lets go ahead to escalate our privileges



# Privilege Escalation

Checking the user's directory, I found a zip file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/58315266-27dd-436c-aa25-e0ac33c3c171)

Send the file over to your machine

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7601a0e8-07c9-4917-9316-d900e0493635)

Lets unzip this file

```
──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/keeper]
└─$ unzip RT30000.zip 
Archive:  RT30000.zip
  inflating: KeePassDumpFull.dmp     
 extracting: passcodes.kdbx          
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/keeper]
└─$ ls -la           
total 332828
drwxr-xr-x  2 bl4ck4non bl4ck4non      4096 Oct 21 12:54 .
drwxr-xr-x 14 bl4ck4non bl4ck4non      4096 Oct 20 18:16 ..
-rwxr-x---  1 bl4ck4non bl4ck4non 253395188 May 24 11:51 KeePassDumpFull.dmp
-rw-r--r--  1 bl4ck4non bl4ck4non  87391651 Oct 21 12:50 RT30000.zip
-rw-r--r--  1 root      root            100 Oct 20 18:20 keeper
-rwxr-x---  1 bl4ck4non bl4ck4non      3630 May 24 11:51 passcodes.kdbx
```
A ```.kdbx``` file is typically a KeePass database file, used by the KeePass password manager. To access and manage the contents of a .kdbx file, you'll need to use a compatible KeePass client. To install, just run the ```sudo apt install keepassx``` command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ad69e2d6-adbd-4d76-bf88-859eb800ca09)

oops, this requires a password.

John couldn't crack the password actually. 

If you recall, when we extracted the zip file there was a dump file ```KeePassDumpFull.dmp```. When looking for a way to access it I found [this](https://github.com/CMEPW/keepass-dump-masterkey)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/23d6882a-126c-40ac-8dd3-b5219ded4c93)

You can download the python script from [here](https://github.com/CMEPW/keepass-dump-masterkey/blob/main/poc.py)

After downloading, lets run the script

command:```python3 poc.py -d KeePassDumpFull.dmp```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/546d6b16-dac7-481e-80d5-d2faebf7665f)

We can see something like ```dgr●d med fl●de``` from the output

putting this on google I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/37d66f25-8fff-46f0-891e-52089e5fecc9)

Using ```rødgrød med fløde``` as the password, I was able to view the keepass file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/21164a74-a88c-4a63-8239-0ab49fe7567f)

Checking the network tab,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a36665dd-b6ac-49c1-940c-0ec2612b408e)

Lets click on that

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/92bd2fd1-c1f0-4ebb-91dc-cada01114431)

nice nice, we can see the password of the root user and also the PuTTY-User-Key-File. But the password wasn't working when I tried to ssh into the server. Lets try the PuTTY-User-Key-File

Save the PuTTY-User-Key-File in a file say "bankai.ppk"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ef211f2f-711d-4297-9dc6-11ac910e138c)

We can use puttygen to create a .pem key file using the .ppk file.

command:```puttygen bankai.ppk -O public-openssh -o bankai.pem```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/keeper]
└─$ puttygen bankai.ppk -O public-openssh -o bankai.pem
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/keeper]
└─$ ls -la bankai.pem    
-rw-r--r-- 1 bl4ck4non bl4ck4non 398 Oct 21 18:36 bankai.pem
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/keeper]
└─$ chmod 600 bankai.pem    
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/keeper]
└─$ ls -la id_rsa
-rw------- 1 bl4ck4non bl4ck4non 398 Oct 21 18:36 bankai.pem
```
smooth, now we can ssh into the server as the root user using the ```bankai.pem``` file

command:```ssh -i bankai.pem  root@tickets.keeper.htb```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2206693c-ed79-4b5f-a211-7f7e4317e973)

nice nice, we got root shell, we have successfully pwned this box

That will be all for today
<br><br>
[Back To Home](../../index.md)






















