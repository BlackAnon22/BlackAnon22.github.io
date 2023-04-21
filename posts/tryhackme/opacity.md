# Recon

## PortScanning
command:```sudo nmap -A 10.10.149.13 -T4 -v -p-```

```
# Nmap 7.93 scan initiated Mon Apr 10 06:37:31 2023 as: nmap -A -T4 -v -p- -oN opacity 10.10.149.13
Increasing send delay for 10.10.149.13 from 0 to 5 due to 777 out of 1942 dropped probes since last increase.
Increasing send delay for 10.10.149.13 from 5 to 10 due to 21 out of 51 dropped probes since last increase.
Nmap scan report for 10.10.149.13
Host is up (0.17s latency).
Not shown: 65531 closed tcp ports (reset)
PORT    STATE SERVICE     VERSION
22/tcp  open  ssh         OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 0fee2910d98e8c53e64de3670c6ebee3 (RSA)
|   256 9542cdfc712799392d0049ad1be4cf0e (ECDSA)
|_  256 edfe9c94ca9c086ff25ca6cf4d3c8e5b (ED25519)
80/tcp  open  http        Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
| http-title: Login
|_Requested resource was login.php
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
139/tcp open  netbios-ssn Samba smbd 4.6.2
445/tcp open  netbios-ssn Samba smbd 4.6.2
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=4/10%OT=22%CT=1%CU=39665%PV=Y%DS=2%DC=T%G=Y%TM=6433A3B
OS:0%P=x86_64-pc-linux-gnu)SEQ(SP=105%GCD=1%ISR=103%TI=Z%CI=Z%II=I%TS=A)OPS
OS:(O1=M506ST11NW7%O2=M506ST11NW7%O3=M506NNT11NW7%O4=M506ST11NW7%O5=M506ST1
OS:1NW7%O6=M506ST11)WIN(W1=F4B3%W2=F4B3%W3=F4B3%W4=F4B3%W5=F4B3%W6=F4B3)ECN
OS:(R=Y%DF=Y%T=40%W=F507%O=M506NNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=A
OS:S%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R
OS:=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F
OS:=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%
OS:T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD
OS:=S)

Uptime guess: 24.632 days (since Thu Mar 16 15:40:10 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=261 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
| smb2-time: 
|   date: 2023-04-10T05:50:36
|_  start_date: N/A
| nbstat: NetBIOS name: OPACITY, NetBIOS user: <unknown>, NetBIOS MAC: 000000000000 (Xerox)
| Names:
|   OPACITY<00>          Flags: <unique><active>
|   OPACITY<03>          Flags: <unique><active>
|   OPACITY<20>          Flags: <unique><active>
|   \x01\x02__MSBROWSE__\x02<01>  Flags: <group><active>
|   WORKGROUP<00>        Flags: <group><active>
|   WORKGROUP<1d>        Flags: <unique><active>
|_  WORKGROUP<1e>        Flags: <group><active>
| smb2-security-mode: 
|   311: 
|_    Message signing enabled but not required

TRACEROUTE (using port 8080/tcp)
HOP RTT       ADDRESS
1   267.09 ms 10.18.0.1
2   267.24 ms 10.10.149.13

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Mon Apr 10 06:50:40 2023 -- 1 IP address (1 host up) scanned in 789.78 seconds
```
From our scan we have 4 port opened. Port 22 which runs ssh, port 80 which runs http and port 139&445 which runs netbios-ssn. We'll be starting our enumeration from the port 80.




# Enumeration (port 80)
Going to the webpage, you'll get this

![image](https://user-images.githubusercontent.com/67879936/230836631-80b1c48c-8cad-44e4-990a-0e6b0dfaf8d4.png)

A login page. I tried using default creds to login but none worked. 

Lets try to fuzz for directories using ```ffuf```

command:```ffuf -u "http://10.10.149.13/FUZZ" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ ffuf -u "http://10.10.149.13/FUZZ" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -e .zip,.sql,.php,.phtml,.bak,.backup  

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.149.13/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

index.php               [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 170ms]
login.php               [Status: 200, Size: 848, Words: 115, Lines: 35, Duration: 204ms]
css                     [Status: 301, Size: 310, Words: 20, Lines: 10, Duration: 203ms]
logout.php              [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 156ms]
cloud                   [Status: 301, Size: 312, Words: 20, Lines: 10, Duration: 190ms]
server-status           [Status: 403, Size: 277, Words: 20, Lines: 10, Duration: 235ms]
```
cool, we found a directory ```/cloud```. Moving to that directory you should get something like this

![image](https://user-images.githubusercontent.com/67879936/230845383-e4fd8a56-a239-4fa6-a7d6-0181d219267d.png)

So, we can upload an image here by providing the link to where the image is provided. Lets try to upload an image

![image](https://user-images.githubusercontent.com/67879936/230845724-5ddb1201-ce61-4e05-8c9c-9130dd9527f8.png)
![image](https://user-images.githubusercontent.com/67879936/230845802-afd37968-0ae4-4d40-a295-ca6bde043c6b.png)

After clicking on the upload button

![image](https://user-images.githubusercontent.com/67879936/230845907-91f05b10-3a97-4fa6-bdad-4f84c1d72208.png)
![image](https://user-images.githubusercontent.com/67879936/230846016-6b47e133-7133-4155-a70e-8a77787e3c43.png)




# Exploitation

Now, what we'll do is to abuse this file upload function in helping us to upload a reverse shell. I'll be usng the php reverse shell from pentest monkey. You can get it [here](https://github.com/jivoi/pentest/blob/master/shell/rshell.php).

![image](https://user-images.githubusercontent.com/67879936/230846850-529ebd60-a2f9-47ae-aa78-e586b6dbe8e4.png)

Ensure you change the $ip and the $port. Now, lets save this

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/opacity]
└─$ file abeg.php 
abeg.php: PHP script, ASCII text
```
So, we have a php script. but the file upload function only allows images(png,jpg,jpeg). To upload our reverse shell, we'll have to bypass this.

![image](https://user-images.githubusercontent.com/67879936/230848782-d10497a2-70a0-4506-8ebf-9519d87722e8.png)
![image](https://user-images.githubusercontent.com/67879936/230848878-c7be5fd7-3a6d-4497-8e90-11473090d6f0.png)

Lets capture this request on burpsuite

![image](https://user-images.githubusercontent.com/67879936/230854019-c7ee1295-eb9f-4ca2-81fc-12ce847610c9.png)

<font color="Green">We'll be using the "#" character in the url, it changes the interpretation of the URL by the web browser. The "#" character is used to represent a fragment identifier, which indicates a specific section within the webpage that should be scrolled to</font>

![image](https://user-images.githubusercontent.com/67879936/230854059-60012059-773b-4654-9ac1-2ff58a915e38.png)

<font color="Green">The web browser will interpret the URL as a request to load the "abeg.php" webpage and then scroll to the section identified by the fragment identifier "#". Because the fragment identifier does not match any section ID in the webpage, the browser will not actually scroll to any section, but it will still load the webpage.</font>

Now, lets forward this request. Also, don't forget to set up your netcat listener.

Keep forwarding the request

![image](https://user-images.githubusercontent.com/67879936/230853755-a5e8f13f-5bd2-4730-8a2b-cf441e7a3bd4.png)

Checking your netcat listener, you should have gotten a shell

![image](https://user-images.githubusercontent.com/67879936/230853984-9541b685-9992-49f3-abca-26a9a8ded24b.png)

Let's stabilize this shell

```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=xterm
```
![image](https://user-images.githubusercontent.com/67879936/230854628-e9baf49e-6eb5-4e4f-934c-a519857f4e76.png)

Now, lets go ahead and escalate our privileges.




# Privilege Escalation

Running linpeas I found this

![image](https://user-images.githubusercontent.com/67879936/233614862-bdf58eb9-3317-4821-9e56-0221d5933c2b.png)

There seems to be something in the ```/opt``` directory. Lets check it out

![image](https://user-images.githubusercontent.com/67879936/233615237-b97c9798-6f1c-4b62-bc5b-d485fe7a7bd2.png)

<font color="Green">A KDBX file is a password-protected database file format used by KeePass, a popular open-source password manager application. It stores sensitive information such as passwords, usernames, and other confidential data in an encrypted format, ensuring that the data remains secure and protected from unauthorized access.</font>

Cool😎, lets send this file to our machine

![image](https://user-images.githubusercontent.com/67879936/233616274-ca3889b4-5a67-4cf3-bf72-1943b58c41ff.png)

Lets try to open this file. I'll be using a tool called ```keepassxc```. To install this you can use ```sudo apt install keepassxc```

![image](https://user-images.githubusercontent.com/67879936/233616889-98562bb3-0479-44b4-a8d6-7fcdc6a4079a.png)

It asks for a password when we try to open the file, but we sure didn't find any password during our enumeration. Since this is a kdbx file, we can use **_John the Ripper_** to crack the password.

command:```keepass2john dataset.kdbx > dataset.txt```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/opacity]
└─$ keepass2john dataset.kdbx > dataset.txt 
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/opacity]
└─$ ls -l dataset.txt 
-rw-r--r-- 1 bl4ck4non bl4ck4non 322 Apr 21 11:45 dataset.txt
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/opacity]
└─$ cat dataset.txt 
dataset:$keepass$*2*100000*0*2114f635de17709ecc4a2be2c3403135ffd7c0dd09084c4abe1d983ad94d93a5*2bceccca0facfb762eb79ca66588135c72a8835e43d871977ff7d3e9db0ffa17*cae9a25c785fc7f16772bb00bac5cc82*b68e2c3be9e46e8b7fc05eb944fad8b4ec5254a40084a73127b4126408b2ff46*b0afde2bd0db881200fc1c2494baf7c28b7486f081a82e935411ab72a27736b4
```
Using John,

command:```john dataset.txt  --wordlist=/home/bl4ck4non/Documents/rockyou.txt```

![image](https://user-images.githubusercontent.com/67879936/233617809-96d43b5b-b5e2-437a-93f6-41dcb7a60eb5.png)

We were about to get the password hehe. Now, lets use this password to open the file

![image](https://user-images.githubusercontent.com/67879936/233617980-14524dff-6049-4e99-a219-48cd84c2a565.png)
![image](https://user-images.githubusercontent.com/67879936/233618653-165ee5e8-12ed-4148-bdbe-1f87c4b5815e.png)

The password worked, we can see that this file contains the credentials for user ```sysadmin```

Lets login to the ssh server using the creds we found

```username:sysadmin```                 ```password:Cl0udP4ss40p4city#8700```

command:```ssh sysadmin@10.10.251.188```

![image](https://user-images.githubusercontent.com/67879936/233619357-330c7c7c-0570-4fd9-8c6c-275180e79870.png)

cool, we are logged in.

Lets go ahead and further escalate our privileges

![image](https://user-images.githubusercontent.com/67879936/233620159-ec2a3e07-158c-41b9-b59a-66c07cbff215.png)

We see the ```script.php``` script running as root. Lets check what the script entails

![image](https://user-images.githubusercontent.com/67879936/233620905-7243aec9-6831-4bf4-996d-868e738c6883.png)

<font color="Green">The script requires the "backup.inc.php" library file, which is likely a script containing backup-related functions that are used in this script.The line "require_once('lib/backup.inc.php');" at the beginning of the script includes the "backup.inc.php" file in the current script, making its functions available for use. This is known as "including" or "importing" a script into another script.</font>

What we'll be doing is that we'll change the content of the ```backup.inc.php``` script located in the ```home/sysadmin/scripts/lib``` directory

![image](https://user-images.githubusercontent.com/67879936/233621542-2ce5ba62-b731-4bea-a770-1e43331f5c57.png)

Let's move this to another file say ```opacity.php``` since we have write access to the file

![image](https://user-images.githubusercontent.com/67879936/233621778-1d44b0cc-83c6-4858-81af-9952fdbc949c.png)

Cool, now lets go ahead and create our own ```backup.inc.php```, yeah the script will have to be malicious if we want to further escalate our privileges. We'll be using the php reverse shell from pentest monkey that we made use of earlier.

![image](https://user-images.githubusercontent.com/67879936/233622436-2ba26172-b00a-4068-8ccd-65d7b92c1f9c.png)

Ensure you change the $ip and $port. Lets go ahead and save this script

![image](https://user-images.githubusercontent.com/67879936/233622558-925873dd-6e5f-4c45-ae61-1dfda3d5c33d.png)

Ensure you set your netcat listener after saving the file

![image](https://user-images.githubusercontent.com/67879936/233622877-d335e9c4-6527-49c7-8625-6b407bcc205f.png)

Wait for some mins and check back on your netcat listener

![image](https://user-images.githubusercontent.com/67879936/233623165-808aaf69-b30d-4897-9a7d-fac11598c0ff.png)

cool, we got a shell as the ```root``` user😎. Lets stabilize this shell as we did earlier

![image](https://user-images.githubusercontent.com/67879936/233623502-f059580d-54bf-485b-8fb4-bc5a9c0e3444.png)

That'll be all for today.

<br> <br>
[Back To Home](../../index.md)































