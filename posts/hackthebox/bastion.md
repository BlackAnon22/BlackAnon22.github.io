# Box: Bastion
# Level: Easy
# OS: Windows
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.129.153.193 -T4  -v -p-```

```
Nmap scan report for 10.129.153.193
Host is up (0.16s latency).
Not shown: 65522 closed tcp ports (reset)
PORT      STATE SERVICE      VERSION
22/tcp    open  ssh          OpenSSH for_Windows_7.9 (protocol 2.0)
| ssh-hostkey: 
|   2048 3a56ae753c780ec8564dcb1c22bf458a (RSA)
|   256 cc2e56ab1997d5bb03fb82cd63da6801 (ECDSA)
|_  256 935f5daaca9f53e7f282e664a8a3a018 (ED25519)
135/tcp   open  msrpc        Microsoft Windows RPC
139/tcp   open  netbios-ssn  Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds Windows Server 2016 Standard 14393 microsoft-ds
5985/tcp  open  http         Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
47001/tcp open  http         Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
49664/tcp open  msrpc        Microsoft Windows RPC
49665/tcp open  msrpc        Microsoft Windows RPC
49666/tcp open  msrpc        Microsoft Windows RPC
49667/tcp open  msrpc        Microsoft Windows RPC
49668/tcp open  msrpc        Microsoft Windows RPC
49669/tcp open  msrpc        Microsoft Windows RPC
49670/tcp open  msrpc        Microsoft Windows RPC
```
Well, only 4 open ports here are worth focusing on. Port 22, Port 135, Port 139 and Port 445. Well, our enumeration will be focused more on port 445.



# Enumeration

We can start off my checking the number of shares available on the smb server

command:```smbclient -L 10.129.153.193```

This will prompt you for a password, you don't have to worry about that, just hit the ```Enter key```.

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/bastion]
└─$ smbclient -L 10.129.153.193
Password for [WORKGROUP\bl4ck4non]:

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        Backups         Disk      
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
Reconnecting with SMB1 for workgroup listing.
do_connect: Connection to 10.129.153.193 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
Unable to connect with SMB1 -- no workgroup available
```
4 shares are available on this server, all the shares are standard smb shares except for the sharename ```Backups```. Lets try connecting to this share, this is  so we can view the files available on the share

command:```smbclient //10.129.153.193/Backups```

This will prompt you for a password, you don't have to worry about that, just hit the ```Enter key```.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a0237be3-a04b-46c3-a518-bfb60755d5a9)

We have a ```.txt```,```.tmp``` file and also a ```windowsimagebackup``` directory available on this share. well, lets take a look at that directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f0ecdfce-4ebc-41f5-9051-1f7e05dc7498)

After checking through the directories we find 2 disk images, lets download them to our machine using the ```get``` command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f1b0d1a4-67d1-4cfd-b5b7-ca4648bb7f80)

I'm not sure this will be possible, we've already been told about this in the ```note.txt``` file😅

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d5b88adc-1496-4357-b7d0-4abbf468641f)

Well, this doesn't mean we can't mount it though🤔. 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d063999b-ec16-47c3-88a9-b25fb27227f6)

Now that we know the way to go, lets exploit😎




# Exploitation

We can start by creating a directory we want the file to be mounted to

command:```sudo mkdir /mnt/bastion_backup```

Then we can mount,

command:```sudo mount -t cifs //10.129.153.193/Backups /mnt/bastion_backup```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/bastion]
└─$ sudo mkdir /mnt/bastion_backup             
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/bastion]
└─$ sudo mount -t cifs //10.129.153.193/Backups /mnt/bastion_backup 
Password for root@//10.129.153.193/Backups: 
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/bastion]
└─$ cd /mnt/bastion_backup 
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[/mnt/bastion_backup]
└─$ ls -la                
total 9
drwxr-xr-x 2 root root 4096 Apr 16  2019 .
drwxr-xr-x 3 root root 4096 Sep 17 04:47 ..
-r-xr-xr-x 1 root root  116 Apr 16  2019 note.txt
-rwxr-xr-x 1 root root    0 Feb 22  2019 SDT65CB.tmp
drwxr-xr-x 2 root root    0 Feb 22  2019 WindowsImageBackup
```
The mounting was a success hehe, now we can locate the vhd files

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/febaafcb-c087-4da4-9659-f290b2018d15)

Well, lets mount the ```vhd``` disk files

























