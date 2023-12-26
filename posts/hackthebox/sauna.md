# Box: Sauna
# Level: Easy
# OS: Windows
<hr>

Lets get started

# Recon

## Portscanning

command:```

From our scan we have quite a number of ports open. We'll start our enumeration from port 80.


# Enumeration (Port 80)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a35169c7-f166-4380-adb4-70e41b244bf9)

Scrolling down, you get this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d671a083-af96-43c9-86d4-0e30202a01b5)

We get "client 1", "client 2" without names of the employees.

Checking around the webpage, I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/af0f33fb-f7a7-44cc-805f-75d89736c0ca)

Scrolling down,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/19d1cf2f-0a80-4616-bcde-87516f1060e3)

We now have their names revealed.

From our nmap scan we can see the kerberos service running on port 88

Lets try to get users who have this service enabled



# Enumeration (Port 88)

Save the names in a file say ```users.txt```






































