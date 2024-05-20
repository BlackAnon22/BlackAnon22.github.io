I participated in the LACTF competition with my friend Sensei and I was able to solve 5 challs. Yeah, welcome challs and discord challs inclusive, that's my specialty afterall😂. I wasn't available throughout the CTF though, this was because of exams hehe.

Lets take a look at the challs I solved

# Challenges Solved
## General
-      Do you read
-      Say Hello
-      Do you read 2

## Misc
-     infinite loop
-     mixed signals


## Web
-     terms and conditions



# General

## Do you read
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/84770bcb-cb3b-49ce-bc53-092666f8e6bb)

There's a landing page which is the url where the challs are hosted on, this [url](https://afr1cacyb3rfe5t.ctfd.io).

Checking the page source should fetch you the flag

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b02694fa-80cc-478b-8264-82cb455505d5)

FLAG:-```ACTF{dont_skip_cutscenes}```

-----------------------------

## Say Hello
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d364c740-4429-464c-86c2-69c8c621a90b)

The question asked here was "Are you following these twitter accounts??", since I already follow all of them before now my response is "yes"

FLAG:-```yes```

-----------------------------------

## Do you read 2
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/643e8a87-ade6-4ec6-afcc-e04f19971bfa)

Yeah, you can already see the flag there😅

FLAG:-```actf{i_did_not_skip_this_cutscene}```

--------------------

# Misc

## Nulock's nemesis 1
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/859b6242-68ae-4a3c-bae6-f3fe9c0f3414)

Lets connect to the challenge instance

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/53d956f9-1383-4a76-a76f-7eeca761bd14)

You can see from the above screenshot that we can't use the normal linux commands here. 

To solve this chall we'll make use of wildcards

```
Wildcards are characters used in shell commands to represent one or more other characters. They're commonly used in file management commands to specify patterns of filenames that you want to match. Here are some common wildcards:

* (asterisk): Matches any sequence of characters, including none.
? (question mark): Matches any single character.
[ ] (square brackets): Matches any one character within the specified range or set.
Here's how they work in practice:

*: Matches zero or more characters.
Example: *.txt matches any file ending in .txt.
?: Matches exactly one character.
Example: file?.txt matches file1.txt, fileA.txt, but not file12.txt.
[ ]: Matches any one character within the specified range or set.
Example: [123].txt matches 1.txt, 2.txt, or 3.txt.
```
Lets try to cause an error

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b14923cc-88b0-4e88-99c4-d594e2380340)

You can see that theere's a bash script in that directory but then we don't know the directory we are sitted at

To try to read a file in this directory we can try using the wildcards we can just use the wildcard ```. ????``` where ```??? represents the length of the file we want to read``` and ```. when used as a standalone character refers to the current working directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/42fcf6c7-97fc-46c6-b4ae-4005264b2a82)

We were able to read the ```lol.txt``` file

Lets make an assumption here, we'll assume that the flag is in the ```flag.txt``` file, so to read this we can use the wildcard ```. ????????```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/63e5b86f-efe9-4022-973c-658e4f5f08a1)

We got our flag

FLAG:-```ACTF{Th4t_w4s_5impl3_wasnt_it?}```

------------------------------

# Web

## Mystique 
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b1791b59-8e0a-4ea2-bd3b-ec4d83002583)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bed8d502-0468-470f-aebd-8bc6e6679770)

We have this login page, yeah we can't signup because the signup button isn't working and yeah default creds ain't working hehe



----------------------------------

## Troll
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/72590bd2-aaa2-4fe6-bca7-f1a414f660b9)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/34409e37-1c2e-49ae-ab65-c3ee87d72e6c)

You see it's blank, viewing the page source

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/53c028ef-b714-49ac-969e-a43069a389d7)

Also blank

Lets fuzz for directories using ffuf

command:```ffuf -u "https://afr1cacyb3rfe5t-troll.chals.io/FUZZ" -w /usr/share/wordlists/dirb/common.txt  -e .zip,.sql,.php,.phtml,.bak,.backup```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3caeb709-ff12-4ba0-9ad7-e86bc2397d34)

We have the ```/robots.txt``` directory, checking this directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/21fc78dc-5ab7-4ddd-a3ae-84e87daaa7f1)

We have another directory here, lets navigate to this directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/38c71c85-a0ab-4662-8d87-632f94e92243)

So navigating to that directory gives us a file to download

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/africa_cyberfest/web]
└─$ ls -la
total 444
drwxr-xr-x 2 bl4ck4non bl4ck4non   4096 May 19 07:18 .
drwxr-xr-x 7 bl4ck4non bl4ck4non   4096 May 19 03:43 ..
-rw-r--r-- 1 bl4ck4non bl4ck4non 444640 May 19 07:17 robots.txt
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/africa_cyberfest/web]
└─$ file robots.txt                                                                                                  
robots.txt: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=35a237ca786dd7f433a5e3761cef1b76eb451a25, for GNU/Linux 3.2.0, not stripped
```
oops, that's a binary.

Using the command ```strings robots.txt | grep "actf{"``` or the command ```strings robots.txt | grep "ACTF{"``` won't get you the flag actually😂. This is because the flag format actually changed (case-sesitive wise). So, running only the ```strings``` command on the binary gives you the flag

command:```strings robots.txt```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1bc8b02e-f555-4c54-aac0-7b72975bde20)

We got the flag

FLAG:-```aCtF{robotTxt_and_strings_as_requested}```

-----------------------------

# Forensics

## Whispers in the Wires
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b76031c1-6181-4c65-91de-5de3f39fe2f0)

Download the pcap file


--------------------------------------

## Invasion!
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/633b475d-9c04-4295-b3dd-ecc85e07e31d)

This is actually a huge file just so you know😅, download this file to your machine and unzip, you should see this

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/africa_cyberfest/forensics]
└─$ cd disk_image      
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/africa_cyberfest/forensics/disk_image]
└─$ ls -la
total 18074244
drwxr-xr-x 2 bl4ck4non bl4ck4non        4096 May 19 04:08  .
drwxr-xr-x 3 bl4ck4non bl4ck4non        4096 May 19 07:11  ..
-rw------- 1 bl4ck4non bl4ck4non  9346220032 Apr 25 04:09 'doh ctf.vmdk'
```
We have a "vmdk" image, well what I did was convert this to a raw image using qemu

To install qemu you can use the command ```sudo apt-get install qemu-utils```

To convert to raw image you can use the command ```qemu-img convert -f vmdk -O raw doh\ ctf.vmdk doh.raw```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d44c3002-3a68-4561-aa5d-0cd6dc84ce9b)

Now that we are done converting we can mount this using autopsy

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/50ec0517-8878-437d-a500-5afb7aa93450)

We'll be analyzing the ```C:\``` drive, that's where juicy stuff's at

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d12bf5d3-433d-48aa-b13d-6a890f6564e9)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d64d19c9-c63e-463a-8fb0-689c861603ed)

We'll do a file analysis

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ec9a1226-3bf0-4f24-a5e8-e8b78a90aee0)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5d6e8711-1940-4ca9-afd1-4655152d449b)

This user actually has something juicy in his Desktop directory hehe

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a06667f3-4138-46c0-8de0-e222705f1d70)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4a29c4dc-48c5-436b-be7e-2ce1e33dfaa2)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/08f4cd20-9c3c-47b8-9035-3ecb53d450b7)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8b8284f2-a45d-4f78-ab6a-50c76fc16dd6)

We have this docx file, but then when you view the hex display you'll see that it has a different header

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/560175c3-4a7c-468f-9f9b-cdfa39082f89)

What's a PK header??

```
A PK header is a 4-byte sequence (50 4B 03 04) that identifies a file as a ZIP archive, serving as a file signature.
```
This means it's not really a docx file, rather it's a zip file.

Now this is what we'll do, we'll export this file to our machine then we change the extension from ```.docx``` to ```.zip```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3864d736-9aae-42e7-8a4a-e26898c9ac5e)

Nice, now lets try to unzip

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1d32ad7e-7292-4290-ba4e-a07ebf1ed81d)

You can see that a password is required, zip2joh won't work because the password isn't in rockyou😂

Lets go back to autopsy and check the ``` /Africa Cyberfest/``` directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d04e41de-324f-4248-be91-aadaa5d6eb3f)

We can see that ```.DAT``` file

```
NTUSER.DAT is a Windows file storing user-specific settings and configuration data, including preferences, application settings, and account information, personalizing the Windows experience for each user.
```
Lets export this file too

If you run ```strings``` and ```grep``` you'll see this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5b3420a9-2e5e-4698-b031-522306d2c1a2)

This means our password's there actually

To extract data from this windows registry file we can use a tool ```reglookup```, you can use the ```sudo apt-get install reglookup``` to install the tool

command:```reglookup  NTUSER.DAT > abeg.txt```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/africa_cyberfest/forensics]
└─$ reglookup  NTUSER.DAT > abeg.txt
```
Now we can grep out the password from this txt file

command:```strings abeg.txt| grep "shadow_commander_password"```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/africa_cyberfest/forensics]
└─$ strings abeg.txt| grep "shadow_commander_password"
/Environment/shadow_commander_password,SZ,'5dUiSm*4*m$A$',
```
So the password is ```5dUiSm*4*m$A$```, lets use this to unzip the file we had earlier









































