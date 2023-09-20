This file contains the cheat sheet for those who wants to take the eJPTv2 exam. So you can just use this for your referencing.


# Discovering hosts available on a network

## Get the IP address of your machine
```sh
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

## To Bruteforce For SMB (Port 445)
```
$ hydra -L /usr/share/metasploit-framework/data/wordlists/unix_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt smb://192.168.56.50
```
## To Bruteforce for SMB(Port 445) for Known Usernames, e.g admin
```
$ hydra -l admin -P /usr/share/wordlists/rockyou.txt smb://192.168.56.50
```















