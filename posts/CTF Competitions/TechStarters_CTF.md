I participated in the TechStarters CTF competition which took place on the 3rd of February 2023. This was a beginner level ctf actually (very beginner level lool)

This is a writeup of the challenges I solved during the event. Lets jump right into it

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/18277ef5-88df-49f2-be93-5ea479847c0e)


# Challenges Solved
-      We are Anonymous
-      Discord
-      Empty Folder
-      Logic Test
-      Safenet
-      Who are we
-      Hide Data
-      Finding Me
-      Who Am I
-      Ascii Player_101  


# We are Anonymous
<hr>

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/techstacon/01 - _we are anonymous_]
└─$ cat we\ are\ anonymous...\ we\ keep\ our\ word.txt                     
we are anonymous

















we keep our word.

































find me if you can






































on X













































my code is anon28148356789
```

At first I thought it was a steganography chall that requires using stegsnow, but nahh I was definitely overthinking it😂. Well, we were given the username to be ```anon28148356789```, lets go over to x to get this user's profle

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ab7eb311-8b02-4f1f-a4d7-7e894e1a3953)

We got a base64 text, lets decode this

command:```echo "dHNjQ1RGe3lvdV9jYW5fY29weSZwYXN0ZX0=" | base64 -d```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/techstacon/01 - _we are anonymous_]
└─$ echo "dHNjQ1RGe3lvdV9jYW5fY29weSZwYXN0ZX0=" | base64 -d                
tscCTF{you_can_copy&paste}
```
We got our flag hehe

FLAG:-```tscCTF{you_can_copy&paste}```

----------------------------------------------

# Discord
<hr>

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/techstacon/02 - disco... disco... discord]
└─$ cat disco...\ disco...\ discord.txt               
https://discord.gg/NTyTCmJr 
```
You can see we got a link to their discord server, so all you have to do is navigate to that link and complete the required processes

Well, once you've joined the discord server you should see this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5103a54f-d4b5-408e-89c9-a1fd124a0d68)

We have another base64 text, lets decode this

command:```echo "dHNjQ1RGe2lfYW1fd2hhdF95b3VfYXJlX2xvb2tpbmdfZm9yfQ==" | base64 -d```

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/techstacon/02 - disco... disco... discord]
└─$ echo "dHNjQ1RGe2lfYW1fd2hhdF95b3VfYXJlX2xvb2tpbmdfZm9yfQ==" | base64 -d
tscCTF{i_am_what_you_are_looking_for}
```
We got our flag

FLAG:-```tscCTF{i_am_what_you_are_looking_for}```

----------------------------

# Empty Folder
<hr>

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/techstacon/03 - empty.folder]
└─$ ls -la
total 12
drwxr-xr-x  3 bl4ck4non bl4ck4non 4096 Feb  3 13:09 .
drwxr-xr-x 12 bl4ck4non bl4ck4non 4096 Feb  3 13:31 ..
drwxr-xr-x  2 bl4ck4non bl4ck4non 4096 Feb  3 12:53 empty.folder.eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6InRzY0NURntpX2FtX2hlcmV9IiwiaWF0IjoxNTE2MjM5MDIyfQ.5aW29xJgAVDxEfpPeERVqxJVKnJByJYN3tEXC2meIus
```
Well this folder has a long name😂. It has no file in it actually. 

If you take a good look at the folder name you'll see something similar to a jwt token, yup ```eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6InRzY0NURntpX2FtX2hlcmV9IiwiaWF0IjoxNTE2MjM5MDIyfQ.5aW29xJgAVDxEfpPeERVqxJVKnJByJYN3tEXC2meIus``` this looks like a jwt token. Lets decode this using an online tool. You can crack it [here](https://jwt.io/)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d42b3278-0f52-4162-8dff-c52b53691e8c)

There's our flag

FLAG:-```tscCTF{i_am_here}```

--------------------

# Logic Test
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3e946285-c257-4808-9f08-0a7333064cd0)

We get this long boring text when we view the content of the file in the folder. Well, this didn't make sense to me actually🥲

Checked online for ```R@1n``` I got this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dfa89e75-09ad-4ef2-8b18-8d448259d1e4)

ALso looked up those texts online and found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/456ba045-52a3-4b01-9157-63220f089390)

Same wordings, well it still didn't make sense to me tho. But then I made an assumption

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f2a8cbd7-8fd9-4714-b0e3-05e754956125)

Yup, that's our flag hehe

FLAG:-```tscCTF{3xampl3F14g}```

----------------

# Safenet
<hr>

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/techstacon/05 - safenet]
└─$ cat follow\ safenet\ society.txt 
follow safenet society on instagram https://www.instagram.com/wesafenetwork?igsh=MzRlODBiNWFlZA==
```
We are asked to follow safenet on instagram page. Lets locate their instagram page

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/77b908cc-084f-4387-a618-44d9d2cca953)

But there's no flag here. Well look closely hehe

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/64b8d4a0-26e6-4163-8474-0f5cdf14b22c)

Navigating to that webpage should get you the flag

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d20a6a5d-97cc-49ea-be1d-3686709864cc)

Yup, that's the flag

FLAG:-```tscCTF{XyZ_987_CTF}```

---------------------------------------

# Who are we
<hr>

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/techstacon/06 - Who are we _]
└─$ ls    
'06 - who are we.mp3'
```
We get this mp3 file.

Lets analyze with sonic visualiser. To install on kali you can use the command ```sudo apt-get -y install sonic-visualiser```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9891a21f-e74b-422b-bbe8-d8a687acc61a)

Good, now ```Pane > Add Spectogram > 06-who are we.mp3: Channel 1```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c44bfa23-7bf4-458e-9c8e-5bf9e4605e84)

cool, we got our flag😎

FLAG:-```tscCTF{W3_Ar3_Saf3N3t}```

----------------------------

# Hide Data
<hr>

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/techstacon/07 - Hide Data]
└─$ cat 07\ -\ Hide\ Data.txt       
gur synt vf gfpPGS:{gur_znfgre_vf_urer} Vg vf cerggl rnfl gb frr gur synt ohg pna lbh frr vg v gbbx arneyl ab zvahgr gb rapbqr guvf jvgu {EBG13:} tbbq yhpx va fbyivat gung
```
We were given this cipher.

First, lets identify the type of cipher this is, you can do that using this [webpage](https://www.dcode.fr/cipher-identifier)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/da4d0074-27ce-4b5f-b6f2-79a054a9545a)

It's a ROT13 cipher, cool. Now lets decode with [this](https://www.dcode.fr/rot-13-cipher)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/59cccaa5-b275-4093-9e85-6d07c2b5fcb1)

Got our flag hehe

FLAG:-```tscCTF{the_master_is_here}```

-------------------------------

# Ascii Player_101
<hr>

```
┌──(bl4ck4non👽bl4ck4non-sec)-[~/Downloads/CTF/techstacon/10 -ASCII Player_101]
└─$ cat 10\ -\ ASCII.txt     
[116, 115, 99, 67, 84, 70, 58, 123, 87, 104, 97, 116, 95, 105, 102, 95, 97, 108, 108, 95, 116, 104, 105, 115, 95, 119, 97, 115, 95, 97, 95, 106, 111, 107, 101, 125]


#I might be the biggest snake_find me if you can
```
This is another cipher.

The name of the challenge already gave us a hint though

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0cd180ad-3d21-4e5a-a92e-2b32f35dfcfd)

Now lets decode using an online decoder. You can use [this](https://www.dcode.fr/ascii-code) to decode

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/afaef7a3-d027-4a2d-854a-4f2b86a32160)

We got our flag

FLAG:-```tscCTF{What_if_all_this_was_a_joke}```

-----------------------

# Finding Me
<hr>

I couldn't solve this particular challenge because it requires a windows box and I don't use windows. Once I find a solution I'll drop the link here

--------------------


Till Next Time :xD




<br> <br>
[Back To Home](../../index.md)






















