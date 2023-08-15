![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/be88b13e-7091-4004-b905-eb5221d79932)# SQL injection vulnerability in WHERE clause allowing retrieval of hidden data
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cb75436f-46d8-4223-a333-d02e2a762328)

Going over to the webpage and clicking on ```Gifts```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6da250fc-c7da-40e0-a2a9-b480799c9b9e)

You should get this,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8d3ff589-b4af-4ebe-b289-e33e0d3092aa)

Now, lets capture this request on burpsuite

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f3c61aa9-6328-457c-9ef6-759a6445d02d)

Sending the request over to burp repeater,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/40ce0d22-99e5-4dbf-9505-f49d929d73ab)

To display one or more unreleased products, we can use the payload ```' or 1=1--```, make sure this is url encoded to something like this ```'+or+1%3d1--```.

Adding this payload to the url,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ef4d74eb-dd1b-42e4-ab2b-2d9c795441ca)

cool, the status code is "ok". Viewing the response in our browser

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1e5003b4-7002-4fb4-9f2a-7e0d2206dfea)

Nice, we have successfully solved the lab😎.

------------------------------

# SQL injection vulnerability allowing login bypass
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fe917a2c-c5ee-4957-a733-9791d8041234)

Navigating to the webpage and clicking on "My Account"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/84e38257-e3d5-4722-b16e-9a736d67ac1e)

You should get this,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f4f46852-8207-4ab0-a157-8523b8b9dda5)

So we are asked to login as the ```administrator``` user, to do this we can use this

username:```administrator'--```          password:```aaaaaaa```

Note: We can either provide a blank password or we use any random stuff for the password since the password will get commented out anyways

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/85078867-6d9a-49b4-ae35-f179f3c1ec43)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bcde4b54-e194-499a-ae31-95dfeb16e484)

Cool, we have successfully solved the lab

---------------------

# SQL injection attack, querying the database type and version on Oracle
<hr>

## Task































