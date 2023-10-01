# Box: Pilgrimage
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.10.11.219 -T4  -v -p-```

```
```
From our nmap scan we have 2 open ports. Port 22 which runs the ssh service and port 80 which runs the http service. Our enumeration today will be focused on port 80.



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fee92d11-c453-45f2-ae24-e1a55f04abd6)

Add that to your ```/etc/hosts``` file

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage]
└─$ sudo nano /etc/hosts
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/pilgrimage]
└─$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       bl4ck4non

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

10.10.11.219 pilgrimage.htb
```
Now refresh the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c602636d-a9a7-495c-a8c1-6a998765077b)

nice




















