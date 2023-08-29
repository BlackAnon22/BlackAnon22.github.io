# OS command injection, simple case
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5fe1257e-aa10-4808-9456-07dc312be969)

Navigate to the website, 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6801b2fd-9ba6-4dfd-9da5-9504da42bb14)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/65bc6550-551a-4063-bdcf-116f9d6b0220)

Capture this request on burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c6e53c61-e24c-4e25-a8e5-641059dcc47d)

So the vulnerability lies in the storeId function.

Checking payload all things I saw something on chaining commands, we can execute the ```whoami``` command by chaining it. So, we'll have something like this
```
storeId=1|whoami
```
Trying this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7eef72bb-d17b-4a48-880e-5c44fc12368e)

So we got the name of the current user.

Checking the response in our browser

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5c8d3284-eab1-48c8-8515-1ea3bd6c0280)

We have successfully completed the task

------------------------

# 
<hr>

## Task














