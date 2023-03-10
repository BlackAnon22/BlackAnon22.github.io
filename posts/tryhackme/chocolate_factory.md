<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap 10.10.250.54 -A -p- -T4 -v

```

```
There are 29 ports opened, but port 21, port 22 and port 80 are the major opened ports which we’d pay more attention to

Since the major ports opened are port 21, port 22 and port 80. We will start our enumeration from port 21.



<h2>Enumeration Port 21</h2>

Since Anonymous login is allowed for port 21, we can use default credentials to login into the ftp server.

```username: anonymous```     ```password: anonymous```

>command: ftp 10.10.250.54

```
                                                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/chocolate_factory]
└─$ ftp 10.10.250.54
Connected to 10.10.250.54.
220 (vsFTPd 3.0.3)
Name (10.10.250.54:bl4ck4non): anonymous

331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> 
```
cool, we are logged in












































