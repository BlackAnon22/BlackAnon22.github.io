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


























