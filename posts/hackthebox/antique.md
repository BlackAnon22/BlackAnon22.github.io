# Box: Antique
# Level: Easy
# OS: Linux
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 10.129.73.127 -v -p- -T4```

```
```
We can see that port 23 is open. I decided to run a udp scan and found this

command:```sudo nmap 10.129.73.127 -sU -v -T4```
