I participated in the TechStarters CTF competition which took place on the 3rd of February 2023. This was a beginner level ctf actually (very beginner basic lool)

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


























