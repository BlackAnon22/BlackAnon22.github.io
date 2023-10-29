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

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6d3d7f92-e021-40c2-bf94-cf6cc085eb4a)

When we try to join HTB, we get this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/24800ff4-e180-415e-b7d4-23abd047b85b)

So we are to supply an invite code, would have said we should bruteforce this, but truth is we don't know the length of the code.

Checking the page source

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/62371c21-6006-4c7a-bd03-53bcf275ca36)

That is the javascript file loaded by the ```/invite``` page that has to do with invite codes

Lets check the content of that file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/330248ca-4aa5-46cf-9330-87d42fcb50b3)

From the above screenshot you can see the javascript function ```makeInviteCode```

What we'll do now is go back to the ```/invite``` dir, then try to execute this javascript function using the developer tool ```console```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/03e16d92-d7f0-4cc0-b1ff-c1256df90f75)

We got something that looks like a rot13 cipher, lets decode this using [cyberchef](https://gchq.github.io/CyberChef/)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6cb43ef1-bc03-417d-af8f-7d5bcc1c4685)

So, to generate the invite code we have to make a post request to ```/api/v1/invite/generate```

Lets capure this request using burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/439d498a-e416-412f-be41-6ea0dd05eb53)



















