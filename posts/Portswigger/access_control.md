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












