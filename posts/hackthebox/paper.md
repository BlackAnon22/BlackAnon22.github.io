# Box: Paper
# Level: Easy
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.129.136.31 -T4  -v -p-```

From the above scan we have 3 open ports. Port 22 which runs ssh, port 80 which runs http, port 443 which runs ssl/http. Well, our ennumeration today will be focused on the http service.



# Enumeration

Lets start by adding the IP address to our ```/etc/hosts``` file

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/paper]
└─$ sudo nano /etc/hosts
[sudo] password for bl4ck4non: 
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/paper]
└─$ cat /etc/hosts 
127.0.0.1       localhost
127.0.1.1       bl4ck4non

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
10.129.136.31 paper.htb
```
Good. Now lets navigate to the webpage ```paper.htb```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/37753a5c-546a-4ad8-a793-ec52ac71cd93)

You should get this





















