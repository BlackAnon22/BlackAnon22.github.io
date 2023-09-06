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

#
<hr>














