# Box: Photobomb
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.228.95 -v -p- -T4```

```
```
From our nmap scan we have 3 open ports, port 21 which runs ftp, port 22 which runs ssh and port 80 which runs http. We'll begin our enumeration today from port 21.



# Enumeration (Port 21)

Lets connect to the ftp server with anonymous login

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2f5531f2-d127-4e1b-b73a-be3969838d44)

oops, anonymous login now allowed.

There's not much to do here, lets move our enumeration to port 80


# Enumeration (Port 80)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/56f533a2-04c3-4dab-ab6d-dac098d5ee7a)

We'll add that domain name to our ```/etc/hosts``` file, then try to load the webpage again

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/02be7144-38e9-43c2-ba0d-b591152d54fc)

This is a wordpress site

lets fireup our wpscan tool to help scan this weboage. We'll enumerate users, themes and plugins

command:```






























