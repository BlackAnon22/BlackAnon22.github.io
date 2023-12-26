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













































