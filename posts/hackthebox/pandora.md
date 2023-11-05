# Box: Pandora
# Level: Easy
# OS: Linux
<hr>

Lets get started 

# Recon

## PortScanning

command:```sudo nmap -A 10.129.82.84 -v -p- -T4```

```
```
From our nmap scan we have 2 open ports, port 22 which runs ssh and port 80 which runs the ssh service. Our enumeration today will be focused on port 80



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c905f057-10eb-493a-a56a-3b8a642bae9f)

So, this is an extension of the domain ```panda.htb```, lets add this domain name to our ```/etc/hosts``` file

Now, navigate to the domain ```panda.htb```

