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

Sent the request to burp repeater, using burpsuite makes the exploitation easier

![image](https://github.com/user-attachments/assets/e301d50d-dcc3-4f1a-bdd5-052d3c78b4df)



























