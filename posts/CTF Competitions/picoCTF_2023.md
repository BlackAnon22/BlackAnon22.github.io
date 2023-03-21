<h2>chrono Gneral Skills -- 100 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226687719-42b2846c-c3fc-41d5-81fd-2ba56610a025.png)

Starting the instance we were given ssh credentials to connect to, now lets connect

>command: ssh picoplayer@saturn.picoctf.net -p 53271

![image](https://user-images.githubusercontent.com/67879936/226688073-bc027985-c22f-45a5-8fc7-ce2fe56218db.png)

cool, we are logged in. Looking at the description of the challenge it says "**_How to automate tasks to run at interval on linux servers?_**". What came to mind when I saw this was a cronjob.

><font color="Green">A cronjob is a task or command that is scheduled to run automatically at specific intervals on a Unix or Linux system. Cron is a time-based job scheduler in Unix and Linux operating systems, which allows users to schedule jobs or scripts to run automatically at specified times or intervals. A cronjob consists of a set of instructions or a script that tells the system what to do and when to do it. For example, a cronjob could be set up to run a backup script every night at midnight or to update a database every hour.</font>

Now we can view a cronjob running when we reapicoCTF{Sch3DUL7NG_T45K3_L1NUX_1b4d8744}d the contents of the ```crontab``` file in the ```/etc``` directory.

![image](https://user-images.githubusercontent.com/67879936/226690638-c0eecc92-77c6-4011-88f8-041ac988e5b7.png)

cool, we got the flag

FLAG:- ```picoCTF{Sch3DUL7NG_T45K3_L1NUX_1b4d8744}```



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

```┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/picoCTF_2023/general]
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

We had to decode with base64 six times to get the flag 😂 

FLAG:- ```picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_dfe803c6}```


<h2>Rule-2023 General Skills -- 100 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226698018-0673dd13-8c37-4557-b5ce-ae5e1ae2c5b8.png)

They provided a link, navigatung to the link we saw the rules, and checking the hints we saw that ```Ctrl+F``` won't work. I found the flag anyways by reading through though lool

![image](https://user-images.githubusercontent.com/67879936/226698636-ce4b63d6-be21-4db5-bb03-a7f0ace70f57.png)

FLAG:- ```picoCTF{h34rd_und3r5700d_4ck_cba1c711}```



<h2>useless General Skills -- 100 points</h2>

![image](https://user-images.githubusercontent.com/67879936/226699237-4491b5bd-f08f-405f-98bd-8e38e528f9d9.png)

We were given an ssh instance to connect to. Lets connect to the instance

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

><font color="Green">On a Linux system, the man command is used to display the manual pages (or "man pages") for a given command or topic. To use the man command, you simply type "man" followed by the name of the command or topic you want to learn about</font>

running the command ```man useless```

![image](https://user-images.githubusercontent.com/67879936/226701284-9b2662e7-88ba-4979-bedd-72bcc0392347.png)

We got the flag hehe

FLAG:- ```picoCTF{us3l3ss_ch4ll3ng3_3xpl0it3d_3555}```





























