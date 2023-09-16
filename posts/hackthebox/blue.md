# Box: Blue
# Level: Easy
# OS: Windows
<hr>

This is a very easy box, not easy, very easy 

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.129.110.225 -T4  -v -p-```

```
Nmap scan report for 10.129.110.225
Host is up (0.15s latency).
Not shown: 65513 closed tcp ports (reset)
PORT      STATE    SERVICE      VERSION
47/tcp    filtered ni-ftp
135/tcp   open     msrpc        Microsoft Windows RPC
139/tcp   open     netbios-ssn  Microsoft Windows netbios-ssn
445/tcp   open     microsoft-ds Windows 7 Professional 7601 Service Pack 1 microsoft-ds (workgroup: WORKGROUP)
2468/tcp  filtered qip-msgd
6099/tcp  filtered raxa-mgmt
9834/tcp  filtered unknown
19056/tcp filtered unknown
31232/tcp filtered unknown
33400/tcp filtered unknown
37044/tcp filtered unknown
45939/tcp filtered unknown
49152/tcp open     msrpc        Microsoft Windows RPC
49153/tcp open     msrpc        Microsoft Windows RPC
49154/tcp open     msrpc        Microsoft Windows RPC
49155/tcp open     msrpc        Microsoft Windows RPC
49156/tcp open     msrpc        Microsoft Windows RPC
49157/tcp open     msrpc        Microsoft Windows RPC
49393/tcp filtered unknown
49496/tcp filtered unknown
61199/tcp filtered unknown
61779/tcp filtered unknown
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=9/16%OT=135%CT=1%CU=35042%PV=Y%DS=2%DC=T%G=Y%TM=6505D5
OS:1D%P=x86_64-pc-linux-gnu)SEQ(SP=103%GCD=1%ISR=10D%TI=I%CI=I%II=I%SS=S%TS
OS:=7)OPS(O1=M539NW8ST11%O2=M539NW8ST11%O3=M539NW8NNT11%O4=M539NW8ST11%O5=M
OS:539NW8ST11%O6=M539ST11)WIN(W1=2000%W2=2000%W3=2000%W4=2000%W5=2000%W6=20
OS:00)ECN(R=Y%DF=Y%T=80%W=2000%O=M539NW8NNS%CC=N%Q=)T1(R=Y%DF=Y%T=80%S=O%A=
OS:S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=80%W=0%S=A%A=O%F=R%O=%RD=0%Q
OS:=)T5(R=Y%DF=Y%T=80%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=80%W=0%S=A
OS:%A=O%F=R%O=%RD=0%Q=)T7(R=N)U1(R=Y%DF=N%T=80%IPL=164%UN=0%RIPL=G%RID=G%RI
OS:PCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=80%CD=Z)

Uptime guess: 0.015 days (since Sat Sep 16 16:55:45 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=259 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: Host: HARIS-PC; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-time: 
|   date: 2023-09-16T16:17:27
|_  start_date: 2023-09-16T15:55:59
| smb2-security-mode: 
|   210: 
|_    Message signing enabled but not required
| smb-os-discovery: 
|   OS: Windows 7 Professional 7601 Service Pack 1 (Windows 7 Professional 6.1)
|   OS CPE: cpe:/o:microsoft:windows_7::sp1:professional
|   Computer name: haris-PC
|   NetBIOS computer name: HARIS-PC\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2023-09-16T17:17:24+01:00
|_clock-skew: mean: -19m57s, deviation: 34m37s, median: 1s

TRACEROUTE (using port 1025/tcp)
HOP RTT       ADDRESS
1   148.34 ms 10.10.14.1
2   148.63 ms 10.129.110.225

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
```
Well from the scan we hav3 3 main ports opened. Our enumeration today will be focused on the port runnint the netbios service.



# Enumeration

Lets start by checking the number of shares available on the smb server

command:```smbclient -L 10.129.110.225```

This is going to prompt you for a password, just hit the ```Enter key``` since we don't have any password

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Blue]
└─$ smbclient -L 10.129.110.225
Password for [WORKGROUP\bl4ck4non]:

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        Share           Disk      
        Users           Disk      
Reconnecting with SMB1 for workgroup listing.
do_connect: Connection to 10.129.110.225 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
Unable to connect with SMB1 -- no workgroup available
```
We have 5 smb shares available on the server

I couldn't find anything after connecting to the shares🥲.

We can check out nmap scripting engine to scan the smb port for potential vulnerabilities

command:```nmap -p 445 --script smb-vuln*.nse 10.129.110.225```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bad2e7ad-4287-4517-a8ce-7adcfcd7c9d5)

Checking out the CVE we find this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6923c708-17bc-472f-8a64-50392c648e03)

So it is a vulnerability that exists in ```SMBv1```. The vulnerability is  also known as ```EternalBlue```. Well, lets exploit😎




# Exploitation

We can use the metasploit module for this

command:```msfconsole```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/04cc7b9c-0896-4f6c-a88e-6bcfff2f73bf)

Good

command:```search eternalblue```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4411b9d9-3489-466d-bbec-83b29150ce14)

Next,

command:```use exploit/windows/smb/ms17_010_eternalblue```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0aa62370-9387-4a0c-a5fe-5a7aa7cff8a6)

We'll set the RHOSTS and LHOST. RHSOT is the target's IP, while LHOST is our tun0 IP

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/79ef8f25-2b66-4677-a5b3-77cf238d55ac)

Now we can use the ```exploit``` command to exploit

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ff992a9b-e7f7-45dc-abad-36a2fd9577cc)

We got a meterpreter session hehehe

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bb99258e-33d4-449c-b637-585c72f91b16)

We won't be need privilege escalation, this is because we spawned a shell as the highest privileged user which is ```NT Authority\System```

Lets locate the flag

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/80dabba0-f61c-4d55-85b5-747e07af86cf)

Well that's all


Alright, wait😂. Metasploit??? well, I have some folks who would come for me if they caught me using it😂. So, we'll be doing the manual exploitation also,this is because metasploit is more of automation and all.

Well I found this great exploit, you can download from [here](https://github.com/d4t4s3c/Win7Blue)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/52f2d875-b76e-4364-a85f-9d17ef713c68)

Now that we made the shell script executable, we can execute it with the command ```./Win7Blue.sh```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f2bd08d7-b255-4033-9117-4b1c06f3d069)

Our target is a windows 7 with a 64 bits architecture, so we'll be choosing ```3```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/be5e0fe7-aba6-4d78-b910-8f888490fe02)

RHOST should be the target's ip

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4b29c4e8-5f08-421f-89db-415d7a678faa)

LHOST should be your tun0 ip

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3d763ca9-761a-4b15-b75f-7c470d64481b)

LPORT should be the port you want to listen on, before setting this ensure you have a netcat listener set up already. For example, I plan on using port ```443```, so I have my netcat listener ready 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c0e9a776-e6b8-4949-9080-2511b6b39b47)

Now, we can provide the LPORT

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2d247926-c529-498e-b6f6-53eea1bcdaca)

Checking the listener we set up,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bed411f9-6370-4788-aabb-362d3fec8194)

We spwned a shell as user ```NT Authority\System```😎

So, you can choose to either use the metasploit exploitation process or the manual exploitation process🙂


That will be all for today
<br> <br>
[Back To Home](../../index.md)







