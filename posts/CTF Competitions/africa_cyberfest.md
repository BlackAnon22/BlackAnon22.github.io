I participated in the LACTF competition with my friend Sensei and I was able to solve 5 challs. Yeah, welcome challs and discord challs inclusive, that's my specialty afterall😂. I wasn't available throughout the CTF though, this was because of exams hehe.

Lets take a look at the challs I solved

# Challenges Solved
## General
-      Do you read
-      Say Hello
-      Do you read 2

## Misc
-     infinite loop
-     mixed signals


## Web
-     terms and conditions



# General

## Do you read
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/84770bcb-cb3b-49ce-bc53-092666f8e6bb)

There's a landing page which is the url where the challs are hosted on, this [url](https://afr1cacyb3rfe5t.ctfd.io).

Checking the page source should fetch you the flag

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b02694fa-80cc-478b-8264-82cb455505d5)

FLAG:-```ACTF{dont_skip_cutscenes}```

-----------------------------

## Say Hello
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d364c740-4429-464c-86c2-69c8c621a90b)

The question asked here was "Are you following these twitter accounts??", since I already follow all of them before now my response is "yes"

FLAG:-```yes```

-----------------------------------

## Do you read 2
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/643e8a87-ade6-4ec6-afcc-e04f19971bfa)

Yeah, you can already see the flag there😅

FLAG:-```actf{i_did_not_skip_this_cutscene}```

--------------------

# Misc

## Nulock's nemesis 1
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/859b6242-68ae-4a3c-bae6-f3fe9c0f3414)

Lets connect to the challenge instance

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/53d956f9-1383-4a76-a76f-7eeca761bd14)

You can see from the above screenshot that we can't use the normal linux commands here. 

To solve this chall we'll make use of wildcards

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
Lets try to cause an error

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b14923cc-88b0-4e88-99c4-d594e2380340)

You can see that theere's a bash script in that directory but then we don't know the directory we are sitted at

To try to read a file in this directory we can try using the wildcards we can just use the wildcard ```. ????``` where ```??? represents the length of the file we want to read``` and ```. when used as a standalone character refers to the current working directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/42fcf6c7-97fc-46c6-b4ae-4005264b2a82)

We were able to read the ```lol.txt``` file

Lets make an assumption here, we'll assume that the flag is in the ```flag.txt``` file, so to read this we can use the wildcard ```. ????????```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/63e5b86f-efe9-4022-973c-658e4f5f08a1)

We got our flag

FLAG:-```ACTF{Th4t_w4s_5impl3_wasnt_it?}```

------------------------------

# Web

## Troll
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/72590bd2-aaa2-4fe6-bca7-f1a414f660b9)

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/34409e37-1c2e-49ae-ab65-c3ee87d72e6c)

You see it's blank, viewing the page source

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/53c028ef-b714-49ac-969e-a43069a389d7)

Also blank



























