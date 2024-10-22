# Lab: Exploiting an API endpoint using documentation
<hr>

## Task

![image](https://github.com/user-attachments/assets/0e638172-96ca-41b8-a510-1f8f5f42653c)

So we are find an exposed API documentation

First, lets navigate to the webpage

![image](https://github.com/user-attachments/assets/2b3450b0-e562-4712-845d-2d6b6101d2f4)

Logging in with the creds we were given

![image](https://github.com/user-attachments/assets/df7b3b24-95fd-4c9d-a8ff-94e9e60abfd8)

We are logged in, lets head back to the "Home" page

![image](https://github.com/user-attachments/assets/d0000145-db66-4681-b91f-ec94c2f90f61)

Lets perform directory fuzzing using dirsearch

command:```dirsearch -u https://0a0c004c037a9ea281dd253c00720078.web-security-academy.net/ -w /usr/share/wordlists/dirb/common.txt```

![image](https://github.com/user-attachments/assets/d8e8c8ae-96f8-4a62-8d5f-592ae92c3ba1)

We have the `/api` directory

Navigating to the directory you should see this

![image](https://github.com/user-attachments/assets/d5bd4cdc-48e6-4f58-a8a1-cb23e92ac318)

We can that to complete the task which is to delete the user `carlos` since we've gotten the endpoint to use from the documentation.

I sent the request to burp repeater, 

![image](https://github.com/user-attachments/assets/e301d50d-dcc3-4f1a-bdd5-052d3c78b4df)
![image](https://github.com/user-attachments/assets/334326e5-4b49-4af6-a758-8896ae49f2d6)

Refreshing the webpage

![image](https://github.com/user-attachments/assets/f3a7bc0b-1c6f-4bbd-9413-c89dba8ff9ca)

We have successfully completed this lab

----------------------------------------------

# Lab: Finding and exploiting an unused API endpoint
<hr>

## Task

![image](https://github.com/user-attachments/assets/ca64c13b-05f6-4605-a73d-76cab59e8e2a)

The task is to buy a `Lightweight l33t Leather Jacket` by exploiting a hidden api endpoint

Navigate to the webpage

![image](https://github.com/user-attachments/assets/1d221d66-5ab1-48dc-880c-3d33c6900167)

Since we have login creds, lets login

![image](https://github.com/user-attachments/assets/fbe73353-9fd7-4597-acaa-b42cd83dbf22)

Running a directory enumeration scan didn't show any api directory

![image](https://github.com/user-attachments/assets/3d3e5887-23da-4236-926c-4f891510394b)

I did a bit of crawling with burpsuite and I got this

![image](https://github.com/user-attachments/assets/4a53e5ef-c629-43c4-8ec2-81d1769b0326)

Send the request to repeater,

![image](https://github.com/user-attachments/assets/3f166ca9-3649-4705-a934-f64c57bddb22)

Lets try to change the HTTP method from `GET` to say `PATCH`

![image](https://github.com/user-attachments/assets/3a10a8bb-438d-47ec-9154-3f9cdf69a253)

We got an unauthorized error, what I did was go to the browser, login with the creds I was given then captured a fresh request

![image](https://github.com/user-attachments/assets/7e6166cc-6eb3-4268-a5a0-6ef140d81257)

From the error message we can see that our `content-type` is meant to be `application/json`. 

To change the content-type to application/json I used the BApp extension `content type converter`

![image](https://github.com/user-attachments/assets/0431829e-a6a7-45e3-97bd-edcb3ddb979b)

Now lets add the parameter

![image](https://github.com/user-attachments/assets/6b2d0ae3-ce72-463a-a87d-680f42ead657)

We've successfully updated the price

Showing this response in browser,






















