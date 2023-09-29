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

The ```semicolon(;)``` is often used as a delimeter so seperate multiple commands within a single input field. So, we can try to use the ```semicolon(;)``` character to run multiple commands.

For example lets say we want to run the ```id``` command alongside the domain name we provided. So, we'll be having an input like this ```google.com;id```

Lets try to execute this to see what happens

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/730ee60f-38a8-4c9a-85a4-5cf2f525d477)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7a23174f-f258-4b4d-8bad-91b5efffcb21)

Scrolling down,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6cef73f1-ffc0-4d30-858d-a7a1e4217465)

It worked hehe, we were able to successfully execute the linux command




















