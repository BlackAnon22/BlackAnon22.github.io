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

Now we can add the leather jacket to our cart,

![image](https://github.com/user-attachments/assets/2ecfc908-6ce3-4f2b-b701-cf0bb470e64c)
![image](https://github.com/user-attachments/assets/0761480b-8617-4e84-bcff-d33efaa0f1cf)

We have successfully completed this lab

-------------------------------------------

# Lab: Exploiting a mass assignment vulnerability
<hr>

## Task

![image](https://github.com/user-attachments/assets/dfd4a52d-365a-41df-af92-b6efb5f551e7)

So the task is to exploit the mass assignment vulnerability

Navigate to the webpage

![image](https://github.com/user-attachments/assets/5b9344e5-6a86-4720-8f4d-386e91cbb881)

Login with the given credentials

![image](https://github.com/user-attachments/assets/f760ccbb-a371-4123-8844-ccbffaab9557)

Lets do a bit of directory fuzzing using dirsearch

command:```dirsearch -u https://0ac30071046b997e82cb8d7300fd0059.web-security-academy.net/ -w /usr/share/wordlists/dirb/common.txt```

![image](https://github.com/user-attachments/assets/ff6e4ce9-8efa-4d7c-b0a2-eec60d01e64c)

Navigating to the `/api` directory

![image](https://github.com/user-attachments/assets/ea00fe7e-b57c-486b-a05a-5c591f49cd07)

We found an endpoint `/checkout`

First, lets add the leather jacket to our cart, then we'll capture a fresh request and navigate to the `/checkout` endpoint

![image](https://github.com/user-attachments/assets/4e09e571-f064-44b1-8fcd-1482a6861332)
![image](https://github.com/user-attachments/assets/840cde0a-0a89-4a3e-bcb2-3142b1936e1f)

```json
{"chosen_discount":{"percentage":0},"chosen_products":[{"product_id":"1","name":"Lightweight \"l33t\" Leather Jacket","quantity":1,"item_price":133700}]}
```
From the json output above we have the "chosen_discount" parameter, this means we can specify the percentage discount that applies to the product. As at this point the percentage discount is 0%, this means the price of the leather jacket is still `133700`.

Now we'll change the `content-type` of our request to `application/json`

![image](https://github.com/user-attachments/assets/75021da1-1bbd-4496-9e64-6bef1f2722b8)

Next thing to do is to add the json output we got from our `GET` request

![image](https://github.com/user-attachments/assets/7538856c-a16e-4195-a9f4-9f99f32a2ae5)

We set the percntage discount to "100" which means we can get the Leather Jacket for free

Checking the webpage

![image](https://github.com/user-attachments/assets/883f8008-dc2e-4f87-8e30-da2f70208800)

We have successfully completed this lab

--------------------------------------------------------





















