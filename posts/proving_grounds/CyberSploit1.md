## CyberSploit1 Proving Grounds
## Level: Easy
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 192.168.245.92 -T4  -v -p-```

```
# Nmap 7.93 scan initiated Sun Jun 25 07:25:11 2023 as: nmap -A -T4 -v -p- -oN cybersploit1 192.168.245.92
Increasing send delay for 192.168.245.92 from 0 to 5 due to 749 out of 1872 dropped probes since last increase.
Increasing send delay for 192.168.245.92 from 5 to 10 due to 11 out of 24 dropped probes since last increase.
Warning: 192.168.245.92 giving up on port because retransmission cap hit (6).
Nmap scan report for 192.168.245.92
Host is up (0.21s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 5.9p1 Debian 5ubuntu1.10 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   1024 011bc8fe18712860846a9f303511663d (DSA)
|   2048 d95314a37f9951403f49efef7f8b35de (RSA)
|_  256 ef435bd0c0ebee3e76615c6dce15fe7e (ECDSA)
80/tcp open  http    Apache httpd 2.2.22 ((Ubuntu))
|_http-title: Hello Pentester!
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.2.22 (Ubuntu)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=6/25%OT=22%CT=1%CU=42183%PV=Y%DS=4%DC=T%G=Y%TM=6497E24
OS:8%P=x86_64-pc-linux-gnu)SEQ(SP=101%GCD=1%ISR=10C%TI=Z%II=I%TS=8)OPS(O1=M
OS:54EST11NW7%O2=M54EST11NW7%O3=M54ENNT11NW7%O4=M54EST11NW7%O5=M54EST11NW7%
OS:O6=M54EST11)WIN(W1=7120%W2=7120%W3=7120%W4=7120%W5=7120%W6=7120)ECN(R=Y%
OS:DF=Y%T=40%W=7210%O=M54ENNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=
OS:0%Q=)T2(R=N)T3(R=N)T4(R=N)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)
OS:T6(R=N)T7(R=N)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=78
OS:ED%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 0.013 days (since Sun Jun 25 07:25:29 2023)
Network Distance: 4 hops
TCP Sequence Prediction: Difficulty=257 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 256/tcp)
HOP RTT       ADDRESS
1   261.41 ms 192.168.45.1
2   261.40 ms 192.168.45.254
3   261.39 ms 192.168.251.1
4   261.40 ms 192.168.245.92

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Jun 25 07:44:24 2023 -- 1 IP address (1 host up) scanned in 1153.06 seconds
```
From our scan we have 2 open ports, port 22 which runs ssh and port 80 which runs http. Enumeration today will be focused on port 80.



# Enumeration

Navigating to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d67ab198-c0fd-40d9-bd49-075c9b46036d)

Well, we were told to try something more😂. 

Checking the source page;

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/15ca60b9-b7a8-433a-bda3-41b87be75a45)

Cool,we found a username ```itsskv```

There's no login page to test this username against, but since we have port 22 (which runs ssh) open, our best guess will be to test the username for the ssh server. But we haven't found a password yet. Well, lets keep looking

Firing up ffuf

command:```ffuf -u "http://192.168.245.92/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/cybersploit]
└─$ ffuf -u "http://192.168.245.92/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://192.168.245.92/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

cgi-bin/                [Status: 403, Size: 290, Words: 21, Lines: 11, Duration: 227ms]
hacker                  [Status: 200, Size: 3757743, Words: 22955, Lines: 21776, Duration: 224ms]
index                   [Status: 200, Size: 2333, Words: 318, Lines: 51, Duration: 217ms]
index.html              [Status: 200, Size: 2333, Words: 318, Lines: 51, Duration: 221ms]
robots.txt              [Status: 200, Size: 53, Words: 1, Lines: 2, Duration: 163ms]
robots                  [Status: 200, Size: 53, Words: 1, Lines: 2, Duration: 167ms]
:: Progress: [32298/32298] :: Job [1/1] :: 170 req/sec :: Duration: [0:03:00] :: Errors: 0 ::
```
We found some interesting directories, navigating through the directories one by one

<h4>/cgi-bin/</h4>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/db3185a6-861b-495d-b193-c06d83d75a70)

oops, we don't have permission to view the webpage.

<h4>/hacker</h4>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/169e8dc9-792f-4500-a9fb-0f920aa80d0f)

This is more like the backgrounf gif, there's nothing else there.

<h4>/robots.txt</h4>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/02deb6ed-eba0-49e3-b7b3-d1896f0f9de2)

Interesting, we found a base64 encoded text.

<h4>/robots</h4>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/42b3dab0-8ce9-4334-8fdd-cdc5953f0fe8)

This contains the same base64 encoded text we found in the ```/robots.txt``` directory.

Decoding the encoded text

command:```echo "Y3liZXJzcGxvaXR7eW91dHViZS5jb20vYy9jeWJlcnNwbG9pdH0=" | base64 -d```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/cybersploit]
└─$ echo "Y3liZXJzcGxvaXR7eW91dHViZS5jb20vYy9jeWJlcnNwbG9pdH0=" | base64 -d
cybersploit{youtube.com/c/cybersploit}
```
Well. that looks like a flag. 

Let me give you a little shocker😂, that decoded text that looks like a flag is the password to the ssh server😆.

username:```itsskv```      password:```cybersploit{youtube.com/c/cybersploit}```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/30852181-450f-4a9b-a0bb-d430400c5091)

cool, we are logged in. Lets go ahead and escalate our privileges




# Privilege Escalation

Using the command

command:```cat /etc/issue```

We find out that there is an outdated kernel version

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/67046468-83b1-427b-87f0-0371606561dd)

The Linux Kernel is vulnerable to ```overlayfs```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9db41fce-07da-4995-8c7a-c6f7b058d3ff)

You can get the exploit [here](https://www.exploit-db.com/exploits/37292)

Sending the exploit over to the target machine

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2822f966-c492-4b34-8822-73f5dba6e496)

Now, lets compile

command:```gcc abeg.c -o abeg```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/09a9ee98-3bbc-4d1c-89b0-0eb4c33ed5c8)

Now, lets execute the file

command:```./abeg```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1c80352c-0acb-46e6-abfd-1f76f04a379a)

cool, we got a shell as root😎



That will be all for today
<br> <br>
[Back To Home](../../index.md)










