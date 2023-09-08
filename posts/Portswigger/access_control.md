# Unprotected admin functionality
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/11d3f19c-fd00-4462-86d9-d308d06e1737)

Navigate to the webpage,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cc66e7a8-8f11-47de-b474-93714963898a)

So, there's an unprotected admin panel, so to solve this lab we have to delete the user ```carlos```.

Alright, whenever I am checking out a webpage one of the directories I check before trying anything else is ```robots.txt```. The directory at times may contain some juicy details hehe

Navigating to the ```/robots.txt``` directory you should see this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4f89ac4d-18a9-4396-8bdc-1cc96a03d2d5)

We found the directory where the administrator panel is located. Navigating to that directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c28d20bd-bbcb-4b9f-b6a5-eb19e72a3650)

Lets go ahead and delete ```carlos``` account

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a2f55456-be4a-4969-abb4-bcf32d22831e)

We have successfully solved this lab😎

--------------------------------------

# Unprotected admin functionality with unpredictable URL
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9eeed816-f915-4cfa-98fb-49c96512726d)

Navigate to the webpage,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/08eb2db9-2388-421d-90bc-dd279e1de0e0)

Just like we did in the previous example. Lets check the ```robots.txt``` directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/72cbbded-8fb4-4144-a267-cdb8949ad79c)

Not found hehe 

In the task description, we were told that the location is  disclosed somewhere in the application.

Checking the source page, 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8736612a-0ab1-42f0-9b0e-fc7abfe7014d)

We found our admin panel hehe

Navigating to that directory,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9c55dd09-a372-4f81-b70a-7ccfe424452d)

Cool, now lets delete user ```carlos``` account

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c7fb51b7-e59c-4bd9-a51c-e6e23c41ba46)

We have successfully solved this lab

------------------------------------------

# User role controlled by request parameter
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/797fd993-666e-4268-a3e5-24b3d2b531e1)

Navigate to the webpage,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d3db81d7-3919-4550-81a3-3885aff57a16)

In the task description we were told that the admin panel is at ```/admin```. Navigating to that directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e7ccce2b-4ea0-4489-b219-54ad08dc6471)

This is saying we have to be logged in as the administrator user. But we currently don't have the credentials for the admin user.

But we were given the creds for user ```wiener```. Navigate to the ```/login``` and login with this creds

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/75f59c62-9dfa-4039-9307-39cfff70b4bc)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/780c124a-482a-4540-b002-76db262e29b5)

Now, navigate to the ```/admin``` directory and capture this request on burpsuite

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3f864d99-da51-4ee9-832a-057b57b08cdd)

We'll be changing the cookie ```Admin=false``` to ```Admin=true```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7d88b2e5-576d-4e62-aa46-9b7c55c059e7)

Forwarding the request should give us the admin panel

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b2f3ae7f-901a-4c2e-b95a-132b1d679e40)

Now, lets delete user ```carlos``` account

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0a04c7b7-106f-4e11-9e3f-8c4809263b2f)

We have successfully completed this lab.

------------------------------------

# User role can be modified in user profile
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9dbe937a-1461-44a7-9197-a1fb0bcb61dc)

Navigate to the webpage,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b5d51d79-e649-422d-adff-20f1ea34c72e)

We were given the creds for user ```wiener```. Lets try to login with this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/62563906-5437-4b5c-8457-a07e18ab833e)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a62784f9-8475-42ab-9eb6-4809c7695ac9)

Cool, we are logged in. 

Our focus will be on the "update email" function. We'll try to provide an email then we'll capture this request on burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ff6f2ef3-28aa-44c0-83b0-2cc4f8357c1b)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dd40d600-72e1-4614-bceb-587dcd8b6c0d)

Take a look at the ```roleid```. From the task description, we were told that the admin user has a ```roleid``` of ```2```.

Now, we'll be changing the ```roleid``` of user ```wiener``` to ```2```. You can edit your request to this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8939ae1e-bac6-45d7-abcb-f01b7d2566cd)

Following the redirection,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f59ebaf9-45d7-473f-a930-2a3f176b23b9)

Checking the response in browser, you should have this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b57301bd-222e-4a7b-a50c-4f96590fb211)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e350acda-b8a4-4dfc-944b-bf3d9b2dc122)

Lets go ahead and delete user ```carlos``` account

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/89edca54-0e96-4683-80e8-a16a93682517)

We have succesfully solved this lab

------------------------------------

# User ID controlled by request parameter 
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/02e62476-14ac-4fd6-8976-4a2a8f0a2752)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/786d56cf-115f-4f76-8abb-baba5537e3d4)

We were given creds for user ```wiener```, lets login

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6918f8c2-6a17-47ac-bc15-cb718da041e5)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b3a8d5a2-2d61-4aee-91e3-de7ed04e91a5)

Alright, so in the task description we are asked to retrieve the api key for user ```carlos```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ff86a54f-1c00-4f18-a1fe-21aa7e160c28)

Taking a look at the url you have something like this ```/my-account?id=wiener```. One thing we can do to retrieve the api key for user ```carlos``` is changing the ```id``` parameter.

So, we'll have something like this ```/my-account?id=carlos```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f751612d-05c7-4b0b-aab5-b654d18ba13c)

Submiting the api key

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5c67a8b8-8187-41c0-a08f-efb59219a837)

We have successfully completed this lab.

--------------------------------

# User ID controlled by request parameter, with unpredictable user IDs 
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e211f21e-902c-4846-8a9d-b16cc7c347b7)

Navigate to the webpage,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a0f1f93a-1b48-433f-ba38-9600d9d13d35)

Lets login as user ```wiener``` since we were given the creds

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a935f568-2639-4f55-886d-0eecf2acad6d)

Take a look at the url, you'll see something like this ```/my-account?id=0e05390c-3df5-4a4d-ae21-b65b38a7c19b```. We can see the GUID(Globally Unique Identifier) of user ```wiener```.

Our task is to find the GUID for user ```carlos``` and then apply it

Reading the posts you should be able to see the user that posted it. For example

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ce9bcb87-256d-458c-883f-8044fe6bdfcd)

Clicking on ```administrator``` provides us with the GUID for the user and the blog posts posted by the user

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/76d21928-ab1c-4e74-bf62-641b6754ee7e)

The url should have something like this ```blogs?userId=5bd25b61-de54-4f06-9667-5c01e9966aee```

All we have to do now is to look for a blog post that was posted by user ```carlos```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a93bc644-0823-474d-a91c-d9b07905f181)

Found one, clicking on ```carlos``` should get us the GUID of the user and the blog posts posted by the user

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/99798870-7b70-4aa6-bc72-7eb43cd8d6e3)

The GUID should be located in the url ```/blogs?userId=6dfd4608-7537-4092-bfcf-ea3c4886716a```.

Applying that GUID for the url ```/my-account?id=0e05390c-3df5-4a4d-ae21-b65b38a7c19b```. So the new url should have the GUID of user ```carlos```, something like this ```/my-account?id=6dfd4608-7537-4092-bfcf-ea3c4886716a```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/140fe7a8-a87f-4cf4-8f72-ee01d3412252)

We found the API key, submitting the key

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/307dc7e8-b236-4abd-9665-e3c880518a35)

We have successfully solved this lab

---------------------------------------

# User ID controlled by request parameter with data leakage in redirect 
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/af5d1b56-2c31-4d50-a344-e9625d0bbda3)

Navigate to the webpage,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/76439fb7-3cdb-4d95-a001-c79a0530a61a)

Logging in as user  ```wiener```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3498f8e4-e8f7-4147-a020-14b17a2c3dcd)

So, our task is to get the api key for user  ```carlos```

To solve this lab what we'll do is capture the request using burpsuite when we try to login.

Logging out and logging in again (this time we'll capture the request using burpsuite)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/df8df38e-128d-4551-8664-f813a6f3e494)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c00389a7-3aa0-4ae8-983f-eb11a6f488d0)

Forwarding the request

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/93ad272e-d911-4193-971d-816fdb886ad2)

Sending this over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d2e01c3a-5d1b-424f-aada-f91c9305ec16)

Now, lets change the ```id``` from ```wiener``` to ```carlos```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9ee61310-dc8a-4e9c-8ac5-38de26147059)

We got a redirect, before following the redirection lets scroll down the response a little

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a9005aaf-cdeb-4956-b285-99056ca64a71)

The API key was in the redirect. Submitting the key

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/87c724dd-9ba8-4715-84a3-6820fd723ff6)

We have successfully solved this lab

------------------------

# User ID controlled by request parameter with password disclosure
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cfda9ab8-d606-4e17-9376-d4a2a1f8f3b3)

Navigate to the webpage,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/33c87a3a-0085-4ede-9404-e98bd0505b41)

Since we have the creds for user ```wiener``` lets login

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b0cd136a-51d2-4b41-8b07-8642e46af27e)

From the above screenshot, you can see that we have the ```update password``` button. Without changing the password, lets capture the request on burpsuite

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fb686e1d-e47e-4578-aeb6-535f4a7f8f47)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/da56c6f8-5103-4b1c-b93d-9e687bc06e38)

You can see that the password is in plaintext form. 

To get the password for the administrator user,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4eebfac5-4fbf-45cd-97fe-07d0a8abf1f6)

click on that, capture the request on burpsuite and then send it to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4b639568-02f7-4acb-9991-80d29f9cd62d)

We'll be changing the ```id``` parameter from ```wiener``` to ```administrator``` to see what happens

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/95c2bee7-7919-4e69-8e32-95e41a53e6eb)

Scrolling down the response you should see this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/865248e3-bf96-4619-bcd1-d93a82a3afc3)

We have the password for the administrator user hehe.

Lets login

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c967fab5-ae94-43a2-8c1a-fbed302baf8f)

We are logged in

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8f2dc454-288a-4f49-96a6-329b2f99ebd4)

Deleting user ```carlos``` account

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4a330f8d-40ac-4980-9138-ea82f4172f11)

We have successfully completed this lab😎

------------------------------

# Insecure direct object references
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fd758785-3aca-4e48-9452-fe2669701c69)

From the task description user chat logs are stored directly on the server's file system and can be retrieved using static urls.

Navigate to the webpage,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/84034729-f130-46a3-b53f-8876569a20cc)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9f1cd0fe-25bf-4169-9c5d-853be0d0138d)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0f774aa7-1226-439b-8c97-f2cd9c394f36)

Lets try to send a message,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2663adaf-c8ec-44fc-8e78-1f44891004d7)

That was the message I sent. Click on "View transcript" and see what happens

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/portswigger]
└─$ cat 2.txt    
CONNECTED: -- Now chatting with Hal Pline --<br/>You: vawulence is good for the body<br/>Hal Pline: I heard the other half talking earlier. Someone needs to shape up
```
Ohh, so it just downloads the conversations we had with it and then goes ahead to name it. In this case the name of the converstation is ```2.txt```

Let's send another conversation and see what happens when we try to view transcript

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/70790323-8aee-49cf-8874-a85bed1fcf3f)

Trying to view the transcipt

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/portswigger]
└─$ cat 3.txt 
You: vawulence is good for the body<br/>Hal Pline: I heard the other half talking earlier. Someone needs to shape up<br/>CONNECTED: -- Now chatting with Hal Pline --<br/>You: vawulence is good for the body<br/>Hal Pline: Why would you want to know something like that? 
```
This was saved as ```3.txt```. This means without even sending a message we can try to download the transcipts from ```0.txt```. After checking for a while the one that stood out was ```1.txt```. 

So, what you'll do when viewing the transcript is change the number to ```1```

At this point, lets invite burpsuite to this party😎

What we'll do now is try to view the transcript, but this time we'll capture the request using burpsuite

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d20ee05e-50cd-421d-b782-88d8422c61be)

Forward the request,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/476139f9-3d63-40ea-9fa2-e789ed5c7deb)

Send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bb9ccc7b-a0e8-486b-87f4-b90769824e71)

Changing the ```4.txt``` to ```1.txt``` should show us the message where the password is stored

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b26505c0-c9c7-47dc-bdb9-d09542f7781e)

We found the password hehe

Lets login

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/76bd61d5-0f7b-48ea-aedb-fdf5da8e8c83)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bffd8502-47b5-462d-b993-9dc93d2ea4a1)

We have successfully completed this lab

-------------------------------------

# URL-based access control can be circumvented
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a86b3561-bdb0-4352-9ddf-546340def8d2)

Navigate to the webpage,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/57f0ea10-f109-400d-81a1-6711dc4802d1)

Clicking on "Admin panel", you should get this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ecdb0771-b0a2-4a1d-a99d-315c4b716c19)

We got the "Access denied" error. This means we aren't privileged to access the admin panel.

Let's click on "Admin panel" again, but this time we'll capture the request on burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/65b0e9b3-d61c-4ab3-834f-8cfb6d292922)

One way we can solve this is by using the HTTP request header ```X-Original-URL```, this is a request header that is sometimes used to provide information about the original URL or resource that a request was intended for.

We'll be using this header with a ```POST``` request. Since the ```/admin``` directory is the one we can't view, our request will look like this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/64118675-89f2-4b49-8800-7252e648a1dd)

Sending the request

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/33cc366b-b1d7-4ec3-ad03-e14f8349d761)

cool, we got a status of ```OK```. Checking the response in our browser

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/467d4a47-b905-418c-a29c-7c138e970e78)

Cool, we can view the admin panel, but when we try to delete user ```carlos``` account we get the ```access denied``` error.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7d509134-6c8b-44de-81d1-3751c70670a5)

Take a look at the url you'll see something like this ```/admin/delete?username=carlos```.

So, what we'll do now is that we'll add ```/admin/delete``` to the request header ```X-Original-URL```, also add the paramater ```?username=carlos``` to the header.

The request will look like this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8d86f533-727c-45fb-958e-c8e73cd4e9d4)

Now, lets follow the redirection

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/84ce689a-fb4b-4927-a7e3-5b5259b781da)

Got this, checking the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a5a929c2-1656-46cd-82d1-e1a6c8f60c53)

We have successfully solved this lab 

--------------------------------------

#
<hr>























