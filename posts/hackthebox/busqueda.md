# Box: Busqueda
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.78.165 -v -p- -T4```

```
```
From our nmap scan we have 2 open ports, port 22 which runs ssh and port 80 which runs http. Our enumeration today will be focused on port 80



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5c2b168c-3cd6-4abe-a7d9-204d873c455b)

We'll add this domain name to our ```/etc/hosts``` file

Now lets navigate back to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b92cb0f7-c047-4dee-bf25-13d998954717)

