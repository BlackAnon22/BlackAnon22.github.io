# Box: Precious
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A -v -p- -T4 10.129.228.98```

```
```
From our scan we have 2 open ports, port 22 which runs the ssh service and port 80 which runs the http service. We will focus our enumeration today on port 80.



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6968606e-28ec-4f6f-974b-a24c4fa3f55c)

Add this domain name to your ```/etc/hosts``` file

Now lets navigate to the webpage again

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f1570fb6-22f6-4f42-942e-2fdc57ffeb73)

This web application helps us converts webpage to pdf
