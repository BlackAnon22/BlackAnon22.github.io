# Lab: Username enumeration via different responses
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c43d0417-5927-4770-b8b7-894fdc85d040)

So this lab is vulnerable to username enumeration and password brute-force attacks. We'll need the wordlist provided when it is time to bruteforce

Navigate to the website,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8adb0cb3-8243-4d2a-bd80-2a44d3c2b023)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/474199c8-3f0f-41c6-a9fb-752aa0117ce1)

Lets login with something random, then we capture the request using burpsuite and send it over to burp intruder

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8eb0739e-4e37-4174-8481-b9a8542a226e)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e5ef07b6-ee01-4739-b7bb-fb403d2387ba)

Now that we have the captured request, we can go ahead to insert a payload marker

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4f9a9449-f479-4153-ac63-7f2d1f373aff)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/235e7b0c-7374-4b97-bc30-e678e78ee30b)

Now, lets configure our payloads, for the first payload set, we'll copy the content of the candidate usernames provided to us in this lab

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f21c4426-7ee3-4158-9fef-0cc642a4e93a)

For the second payload set, we'll copy the content of the candidate passwords provided to us in this lab

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/086222dc-c227-4889-b270-04cca9423c2b)

Now we can start the attack after configuring both payloads

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/12244b08-8f36-40bf-8a4b-e180ad12d0c9)

We can see that the status code and length for that request is actually different. Lets try to login with this creds

username:```vagrant```      password:```hunter```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/289a2819-2664-495e-8113-81168f6d0cf4)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cfe0adea-3376-4823-8431-cf375d9a2a0f)

We have successfully solved this lab

-------------------------------

# Lab: Username enumeration via subtly different responses
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cca4ec44-b363-4faa-9b79-89993c959dba)

Our task is to access this account by performing a valid username enumeration and bruteforce the user's password

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0a24050f-8d70-4ecb-a1ca-6409e8048dce)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2b5c01db-1285-4916-bd29-2a2b0c25e8d6)

Lets login with something random, then we capture the request using burpsuite and send it over to burp intruder

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/20afcb95-ecad-4022-b197-c97bf339953a)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b37ad6f8-b3cf-49de-aec0-0e53b382c8da)

Now that we have the captured request, we can go ahead to insert a payload marker

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/46b5a931-3185-4541-a7d0-6cbbeca2fe09)

Now, lets configure our payloads, for the first payload set, we'll copy the content of the candidate usernames provided to us in this lab

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2980cfa4-3743-4827-adb5-69df6d768d9b)

For the second payload set, we'll copy the content of the candidate passwords provided to us in this lab

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d6d900e0-97f2-4ae5-913a-fc37cf704bfa)

Now we can start the attack after configuring both payloads















































