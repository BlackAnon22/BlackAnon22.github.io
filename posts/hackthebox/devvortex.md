# Box: Devvorted
# Level: Easy
# OS: Easy
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.49.198 -v -p- -T4```

From our scan we have 2 open ports, port 22 which runs the ssh service and port 80 which runs the http service. Our enumeration today will be focused on port 80.



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/acb6c6b3-777f-4a87-a5ac-49253e9c3e2f)

We'll add the domain name to our ```/etc/hosts/``` file

Now, lets navigate back to the domain name

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e9474da0-59fa-4208-8dcc-a4e7b1ac9667)
