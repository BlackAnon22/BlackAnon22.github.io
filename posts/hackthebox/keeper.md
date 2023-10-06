# Box: Keeper
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.10.11.227 -T4  -v -p-```

```
```
From our above scan we have 2 open ports, port 22 which runs the ssh service and port 80 which runs the http service. Our enumeration today will be focused on port 80.



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/515e7e93-59dc-49a3-849e-94b0addc3cf4)

Lets add that subdomain ```tickets.keeper.htb``` to our ```/etc/hosts``` file

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/keeper]
└─$ sudo nano /etc/hosts                                                                                    
[sudo] password for bl4ck4non: 
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/HTB/keeper]
└─$ cat /etc/hosts            
127.0.0.1       localhost
127.0.1.1       bl4ck4non

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

10.10.11.227 tickets.keeper.htb
```
cool, now lets navigate to that subdomain

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/45b62909-bbbf-4145-a11b-8282a5d18a79)

okay, we got a login page












