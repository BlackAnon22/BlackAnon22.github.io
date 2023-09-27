# Box: Cupidme
# Level: Intermediate
# OS: Linux
<hr>

Lets get started

# Recon

## Portscanning

command:```sudo nmap -A 10.0.30.187 -T4  -v -p-```

```
```
From our scan we have only 1 open port, so our enumeration will be focused on that port




# Enumeration 

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/57455236-6563-4073-9aa1-42af759dead3)

Lets fuzz for directories

command:```ffuf -u "http://10.0.30.187/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/EchoCtf/cupidme]
└─$ ffuf -u "http://10.0.30.187/FUZZ" -w /usr/share/wordlists/dirb/common.txt -e .zip,.sql,.php,.phtml,.bak,.backup

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.0.30.187/FUZZ
 :: Wordlist         : FUZZ: /usr/share/wordlists/dirb/common.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

images                  [Status: 301, Size: 185, Words: 6, Lines: 8, Duration: 167ms]
index.php               [Status: 200, Size: 1805, Words: 92, Lines: 2, Duration: 171ms]
index.php               [Status: 200, Size: 1805, Words: 92, Lines: 2, Duration: 547ms]
LICENSE                 [Status: 200, Size: 1075, Words: 152, Lines: 19, Duration: 166ms]
upload.php              [Status: 302, Size: 0, Words: 1, Lines: 1, Duration: 161ms]
:: Progress: [32305/32305] :: Job [1/1] :: 137 req/sec :: Duration: [0:02:46] :: Errors: 0 ::
```
So, 













