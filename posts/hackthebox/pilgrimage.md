# Box: Pilgrimage
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.10.11.219 -T4  -v -p-```

```
Nmap scan report for 10.10.11.219
Host is up (0.24s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.4p1 Debian 5+deb11u1 (protocol 2.0)
| ssh-hostkey: 
|   3072 20be60d295f628c1b7e9e81706f168f3 (RSA)
|   256 0eb6a6a8c99b4173746e70180d5fe0af (ECDSA)
|_  256 d14e293c708669b4d72cc80b486e9804 (ED25519)
80/tcp open  http    nginx 1.18.0
|_http-title: Did not follow redirect to http://pilgrimage.htb/
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: nginx/1.18.0
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=10/1%OT=22%CT=1%CU=32552%PV=Y%DS=2%DC=T%G=Y%TM=6519C8A
OS:A%P=x86_64-pc-linux-gnu)SEQ(SP=FE%GCD=1%ISR=109%TI=Z%CI=Z%II=I%TS=A)OPS(
OS:O1=M539ST11NW7%O2=M539ST11NW7%O3=M539NNT11NW7%O4=M539ST11NW7%O5=M539ST11
OS:NW7%O6=M539ST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN(
OS:R=Y%DF=Y%T=40%W=FAF0%O=M539NNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS
OS:%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=
OS:Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=
OS:R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T
OS:=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=
OS:S)

Uptime guess: 0.689 days (since Sun Oct  1 03:56:58 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=254 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 3306/tcp)
HOP RTT       ADDRESS
1   338.32 ms 10.10.14.1
2   338.37 ms 10.10.11.219

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Oct  1 20:29:46 2023 -- 1 IP address (1 host up) scanned in 1089.91 seconds
```
From our nmap scan we have 2 open ports. Port 22 which runs the ssh service and port 80 which runs the http service. Our enumeration today will be focused on port 80.



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fee92d11-c453-45f2-ae24-e1a55f04abd6)

Add that to your ```/etc/hosts``` file

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage]
└─$ sudo nano /etc/hosts
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage]
└─$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       bl4ck4non

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

10.10.11.219 pilgrimage.htb
```
Now refresh the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c602636d-a9a7-495c-a8c1-6a998765077b)

The page is now accessible. Lets register an account

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d63a9176-5266-4468-84bc-97b46281ef36)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/58ce2a2e-a0e5-4cf9-98d9-d2c8a35a387f)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2a7426b7-ef6a-45ae-88cc-69e3ce87a04b)

This is an upload page, where we can upload our jpegs and it gets it shrinked down for us. Now, this upload function doesn't allow other extensions, it's strictly ```jpeg``` and ```png``` files.

Lets fuzz for directories using ```ffuf```

command:```ffuf -u "http://pilgrimage.htb/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup```

```

```




















