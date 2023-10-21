# Box: Topology
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.73.145 -v -p- -T4```

```
```
From the scan we have 2 open ports, port 22 which runs ssh and port 80 which runs http. Our enumeration today will be focused on port 80



# Enumeration

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5e340e8a-5cd0-4205-879c-a2be90b0a64e)

This looks like a normal webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/97542b33-5dba-434a-b9a8-991f29a0b2f5)

Clicking on that,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/32907fe6-6347-4b90-91c9-fa5355ceb9b0)

Lets add the subdomain ```latex.topology.htb``` to our ```/etc/hosts``` file.

Now, we should be able to access the subdomain

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2cfdd623-abdf-43ee-a9e0-155788fa7a4b)

We have a Latex Equation Generator here




























