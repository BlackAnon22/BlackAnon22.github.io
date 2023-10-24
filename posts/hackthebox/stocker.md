# Box: Stocker
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.228.197 -v -p- -T4```

```
```
From our scan we have 2 open ports, port 22 and port 80. Our enumeration today will be focused on port 80




# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6a2b79b8-6952-4f43-8c0e-ac68df66a410)

Add the domain name ```stocker.htb``` to your ``/etc/hosts``` file.

We should be able to view the webpage now

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a70cdd08-d99d-4d0e-969e-03b8462c5942)

