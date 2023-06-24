## Sumo Proving Grounds
## Level: Easy
<hr>

Lets get started

# Recon

## PortScanning

command:```sudo nmap -A 192.168.212.87 -T4  -v -p-```

From our scan we can see we have 2 open ports. Port 22 which runs ssh and port 80 which runs http. Our enumeration today will be focused on port 80.




# Enumeration

Navigating to the webpage you should see this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2b321877-d939-4b76-a54b-580bff6381a5)

checking the web source page

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0d860ae0-5b3f-448a-abb3-a6ad3cedebde)

oops nothing

Well, all hope isn't lost yet, lets go ahead and fire up our directory enumeration tools. I'll be using ffuf

command:```ffuf -u "http://192.168.212.87/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/sumo]
└─$ ffuf -u "http://192.168.212.87/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://192.168.212.87/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

cgi-bin/                [Status: 403, Size: 290, Words: 21, Lines: 11, Duration: 214ms]
index                   [Status: 200, Size: 177, Words: 22, Lines: 5, Duration: 218ms]
index.html              [Status: 200, Size: 177, Words: 22, Lines: 5, Duration: 217ms]
:: Progress: [32298/32298] :: Job [1/1] :: 180 req/sec :: Duration: [0:03:29] :: Errors: 0 ::
```
cool, we found a directory ```cgi-bin/```. 

Navigating to that directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cdcb95fb-54cd-45a2-98f2-3d5ee220a66d)

opps, "403 error"😧. 

Lets try to fuzz this directory to see if we can get anything

command:```ffuf -u "http://192.168.212.87/cgi-bin/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/PG/sumo]
└─$ ffuf -u "http://192.168.212.87/cgi-bin/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://192.168.212.87/cgi-bin/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

test                    [Status: 200, Size: 14, Words: 3, Lines: 2, Duration: 223ms]
:: Progress: [32298/32298] :: Job [1/1] :: 157 req/sec :: Duration: [0:03:16] :: Errors: 0 ::
```
We found a sub-directory hehe😎.

Navigating to the sub-directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7cb25db6-01b1-4bb1-ba55-a443a2a724b7)

Okay, "CGI Default". 

What's CGI??

<font color="green">CGI stands for Common Gateway Interface. It is a standard protocol that enables communication between web servers and external programs or scripts. CGI allows web servers to execute these programs and generate dynamic content in response to user requests, facilitating the interactive nature of websites and web applications.</font>

Lets try to look for vulnerabilities for this standard protocol

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/784c7a05-cd16-4223-b5c4-21c6fe3b999e)

Okay, we find out the name of the vulnerability is shellshock, you can read more about it [here](https://securityintelligence.com/articles/shellshock-vulnerability-in-depth/)

Reading [this](https://www.exploit-db.com/docs/english/48112-the-shellshock-attack-%5Bpaper%5D.pdf?utm_source=dlvr.it&utm_medium=twitter) you'll see that editing the  user agent will get us a reverse shell.

Cool stuff right??😎





# Exploitation

We'll be using burpsuite to capture our web requests


  


