# Box: TwoMillion
# Level: Easy
# OS: Linux
<hr>

Lets get started 

# Recon

## PortScanning

command:```sudo nmap -A 10.129.229.66 -v -p- -T4```

```
```
From our nmap scan we have 2 open ports, port 22 which runs the ssh service and port 80 which runs the http service. Our enumeration today will be focused on port 80


# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/19bf0da8-e623-47ee-ad86-8bb898b168e1)

Lets add that domain name to our ```/etc/hosts``` file and then navigate back there

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7d69dfdd-5971-4527-934e-866e9b8fe1b7)

nice
