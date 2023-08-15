# SQL injection vulnerability in WHERE clause allowing retrieval of hidden data
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

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1a110c4b-d810-42b6-b7f3-b5f9df4e4544)

Navigating to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a6c32fe1-538c-430b-8725-13a4afaf4e08)

Capturing the request on burpsuite,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6974648d-151b-4b1d-a68e-1aad9dbcf6b6)

First thing to do is to confirm the number of columns available in the database

So, we'll be using the query
```
' order by 1--
' order by 2--
' order by 3--
```
Ensure this is url encoded, so when you get the internal server error, it means the column number isn't available

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/46cca6a6-9af2-41e9-a473-8f2388847fce)

This means there's a column available in the database,

Trying other queries

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/413576a4-6bb9-4cab-918c-d629f51080fb)

This makes it 2 columns available in the database,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/28d25efa-ca02-4434-93ae-a908703068d9)

From the above screenshot you'll see that the query ```' order by 3--``` returned an Internal Server Error, which means there isn't a column 3 available in the database.

So, we have 2 columns available in the database.

To query the database version we can use the following query 
```
' UNION SELECT banner,null FROM v$version--
```
Explaining this
```
The banner column contains the information about the database version
The null is just there to fill in for the second column of the result
v$version is the name of a database table
```
Trying the query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9f5f9626-7647-445a-8c29-3d021874baf0)

Lets show the response in our browser

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a8001d54-7b63-488e-aa76-10bb21085337)

Nice, we have successfully solved the lab

-------------------------

# SQL injection attack, querying the database type and version on MySQL and Microsoft
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/178842fc-a6ef-4ae6-a5db-6dfe6ad690e9)

Navigating to the webpage, clicking on "Gifts"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2fdc0c82-d053-4b7d-b950-8320359cac38)

Capturing this request on burpsuite and sending it over to burp intruder

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f8492bbd-7d49-4822-acc0-9fb99834b8e1)

Now, lets check the number of columns available in the database using the query
```
' order by 1--
' order by 2--
' order by 3--
```
Ensure this is url encoded, so when you get the internal server error, it means the column number isn't available


































