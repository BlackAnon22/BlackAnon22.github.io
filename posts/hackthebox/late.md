# Box: Late
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A -v -p- -T4 10.129.227.134```

```
Nmap scan report for 10.129.227.134
Host is up (0.21s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.6 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 02:5e:29:0e:a3:af:4e:72:9d:a4:fe:0d:cb:5d:83:07 (RSA)
|   256 41:e1:fe:03:a5:c7:97:c4:d5:16:77:f3:41:0c:e9:fb (ECDSA)
|_  256 28:39:46:98:17:1e:46:1a:1e:a1:ab:3b:9a:57:70:48 (ED25519)
80/tcp open  http    nginx 1.14.0 (Ubuntu)
| http-methods: 
|_  Supported Methods: GET HEAD
|_http-title: Late - Best online image tools
|_http-server-header: nginx/1.14.0 (Ubuntu)
|_http-favicon: Unknown favicon MD5: 1575FDF0E164C3DB0739CF05D9315BDF
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94%E=4%D=10/22%OT=22%CT=1%CU=43247%PV=Y%DS=2%DC=T%G=Y%TM=653594
OS:9B%P=x86_64-pc-linux-gnu)SEQ(SP=107%GCD=1%ISR=10C%TI=Z%CI=Z%II=I%TS=A)OP
OS:S(O1=M53CST11NW7%O2=M53CST11NW7%O3=M53CNNT11NW7%O4=M53CST11NW7%O5=M53CST
OS:11NW7%O6=M53CST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)EC
OS:N(R=Y%DF=Y%T=40%W=FAF0%O=M53CNNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=
OS:AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(
OS:R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%
OS:F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N
OS:%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%C
OS:D=S)

Uptime guess: 12.472 days (since Tue Oct 10 11:11:49 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=263 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 3306/tcp)
HOP RTT       ADDRESS
1   208.71 ms 10.10.14.1
2   208.96 ms 10.129.227.134

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Oct 22 22:31:07 2023 -- 1 IP address (1 host up) scanned in 600.20 seconds
```
From our nmap scan we have 2 open ports, port 22 which runs the ssh service and port 80 which runs the http service. Our enumeration today will be focused on port 80.



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ccbd19c5-7145-4fea-a2b6-39197f3d2ae5)

Scrolling down, you'll see this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9f8cf993-0b60-43d1-a3f7-523c2834797e)

Clicking on that should take you to this webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9b785c34-eed7-46c8-a8d5-cc091832ba8b)

Lets add the subdomain ```images.late.htb``` to our ```/etc/hosts``` file. After that we'll navigate again to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cae3ae2c-60a7-44e6-86a4-5710b67761d0)

This is an application that converts our images to text using the flask, since this has to do with flask it will be a great idea to test this for ssti (server-side template injection).



# Exploitation

We'll start out by uploading a normal png image to see how the application works

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6e7d214d-ed4b-4056-9647-05fb0e9d8ecb)

scanning the image, you will be prompted to download a txt file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9cafef82-70e7-4e99-a667-8f4a5968fe3f)

Lets view the content of this file

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/late]
└─$ cat results.txt            
<p></p>     
```
nice nice.

Now, lets test this for ssti, we'll start by using a simple payload ```{{7*7}}```, In this case, ```7*7``` is a simple arithmetic expression that calculates the product of 7 and 7, which is ```49```. So, when the template is processed, ```{{7*7}}``` would be replaced by ```49```.

To convert this to an image, we'll be using this online [tool](https://smallseotools.com/text-to-image/)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cd358251-cb63-42aa-929b-217a78ae9f05)

Now, lets upload this image

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/76885df7-bd9b-4bdd-8acd-18c3cb5bbd5b)

Lets check the content of the text file scanning

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/late]
└─$ cat results.txt
<p>BlackAnon49
</p>     
```
cool stuff, as you can see our arithmetic got executed. 

Lets look for a payload that can help us execute system commands

























