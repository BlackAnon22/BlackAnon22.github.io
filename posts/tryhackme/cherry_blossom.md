# Recon

## PortScanning

command:```sudo nmap -A 10.10.244.236 -T4  -v -p-```

```

```
From our scan, we have 3 opened ports. Port 22 which runs ssh, port 139&445 which runs netbios. We'll be starting our enumeration from the smb ports.



# Enumeration (Port 139 & Port 445)

Since this is running Samba, lets check for available shares on the smb server

command:```smbclient -L 10.10.244.236```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/99e10e4d-2ac2-41a6-90fc-829c010eb8cb)

We have a sharename ```Anonymous```, lets try to access this share

command:```smbclient //10.10.244.236/Anonymous```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/88db4e04-d65b-48d8-aa3f-80288f6c0571)

Note: When it prompts you for a password, just hit the enter key and you'll be logged in.

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

As you can see from the above screenshot, we have something that looks like a ```png header```. What this means is that the base64 encoding contains a ```png image```. So what we can do is decode the base64 encoding into an image. To do this we will be using a python script

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

```
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ python steg.py ../../image.png 
File _journal.zip succesfully extracted from ../../image.png
                                                                                                                                  
                                                                                                                                 ┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ ls
crypt.py  __init__.py  _journal.zip  lsb.py  __pycache__  steg.py  test.npy  tests.py
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ unzip _journal.zip 
Archive:  _journal.zip
file #1:  bad zipfile offset (local header sig):  0
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/…/TryHackMe/Cherry_Blossom/stegpy/stegpy]
└─$ file _journal.zip 
_journal.zip: JPEG image data
```
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

commands
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
abeg.txt  crypt.py  __init__.py  Journal.ctz  _journal.zip  lsb.py  __pycache__  steg.py  test.npy  tests.py
                                                                                                                                                                                                
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

command:```

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
After extracting we got the file ```Journal.ctd```. I'll be opening this file using the text editor ```gedit```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/38292f1b-2d7f-440e-8b76-89aa5e98145d)

Reading through this, we can see three names being mentioned ```Anitta```,```Harry``` and ```Lily```. 

Moving on you should see something that looks like this. 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/90dc77b6-c36a-4334-aa02-f2ab4aef2410)

This looks like a wordlist, but the content are base64 encoded. There was a discussion where the author talked about the wordlist cherry-blossom.

What we'll do is decoding the base64 encoded texts, save it in a ```.txt``` file, then we'll use the password to bruteforce 



















