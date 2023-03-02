<h2>Search_Engine WEB</h2>

Lets start with searching for random things

![image](https://user-images.githubusercontent.com/67879936/222456164-b405ed98-ca49-41b6-b082-eeac7cabee11.png)

You should get something like this. After checking for a while I remembered solving a room on TryHackMe that has a similar search box but was vulnerable to SQL Injection. So, I tried to test this for SQL Injection.

Let’s start by using a simple SQLI payload that checks the number of columns available, this is to test if the search box is vulnerable to SQL Injection.

```payload used: ‘ ORDER BY 1 — -```

![image](https://user-images.githubusercontent.com/67879936/222456318-663cb77d-a4e5-4cfd-ac61-68e5f11efbac.png)

Nice, from the above screenshot we can tell the search box is vulnerable to SQL Injection. I exploited this by capturing the request using burpsuite and using sqlmap to dump tables and columns

So, capturing the search request on burpsuite we should get this

![image](https://user-images.githubusercontent.com/67879936/222456445-e4d04376-7b1d-42ba-b0d1-acea5108a5ef.png)

After capturing the request lets go ahead to store the contents on our machine. Copy the contents and paste it in any editor of your choice then save it

![image](https://user-images.githubusercontent.com/67879936/222456519-2dda2d86-3521-4f9e-a3f6-6b2ff05113e3.png)

After doing this, we can go ahead to use sqlmap.

Lets start with checking the tables available on the server.

>command:sqlmap -r req.txt --dbs --tables

-r →To read the file
— dbs → To enumerate database
— tables → To enumerate tables

![image](https://user-images.githubusercontent.com/67879936/222456758-5779702e-8c00-46c4-847b-cac8b6fde546.png)

![image](https://user-images.githubusercontent.com/67879936/222456861-defa892e-026b-4adf-abdb-73f68f94ca04.png)

![image](https://user-images.githubusercontent.com/67879936/222456913-d5311321-8f2b-4cde-86ee-df0ec7dff429.png)

![image](https://user-images.githubusercontent.com/67879936/222456979-fad83cd8-cf01-4f79-bc58-754a918d343b.png)

![image](https://user-images.githubusercontent.com/67879936/222457022-8c7993ed-4de2-4683-8865-affd0eaa6b41.png)

Okay, from the above screenshots we found out that the name of the database is “search”, we also found 2 tables “search_engine” and “users”

Now, lets go ahead and dump the contents of the columns in the “users” table

>command:sqlmap -r req.txt -D search -T users --columns --dump

-r → To read the file
-D → Database Name
-T → Table’s Name
--columns → To enumerate columns
--dump → dump all the contents in the columns

![image](https://user-images.githubusercontent.com/67879936/222457299-ae330eaa-b5a5-446d-92d9-8f5aead86ae9.png)

![image](https://user-images.githubusercontent.com/67879936/222457328-aede9494-bca0-4ad9-a0a1-d4798e1941d5.png)

Boom, we got the flag in the column name “password”

Flag:```FLAG{!nj3ct!0n_5l4y3r_XD}```












