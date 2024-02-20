I participated in the LACTF competition with my friend Sensei and I was able to solve 5 challs. Yeah, welcome challs and discord challs inclusive, that's my specialty afterall😂. I wasn't available throughout the CTF though, this was because of exams hehe.

Lets take a look at the challs I solved

# Challenges Solved
## Welcome
-      Discord
-      rules

## Misc
-     infinite loop
-     mixed signals


## Web
-     terms and conditions



# Welcome

## Discord
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a17a39a0-fd79-4312-bcda-d21a950794ec)

You can get this flag when you navigate to their discord server and then check the pinned message in `#general` 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/67933ac2-9f53-47fd-99e8-c320ac2ff024)

Yup that's the flag

FLAG:```lactf{i'm_in_the_discord_server!}```

------------------------------
 
## rules
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cdfc81ad-14a9-46d1-a7d3-cf4eca74c7f7)

Lets navigate to the home page

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2f80f40b-3660-454d-85cd-fa071d3ab9f3)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/191f056c-bc0a-43a9-90cf-4a50b9354fa6)

We got our flag

FLAG:```lactf{i_read_the_rules}```

----------------------

# Misc

## infinite loop
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cf4ba496-607c-4c38-b487-547bb57f7f58)

Navigating to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/17b44357-ea4e-4ad6-8e80-4f70595191b2)

We get this google form, now when you try to fill this form you'll notice it's in a loop

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/68e506c6-c9a5-49c2-bcc7-88a5509db74c)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b48f5d5e-5e10-4401-9a78-42ea4673a296)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c3dbc94a-19db-4fb1-8c29-4c0827d26ab9)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5bd9aa72-67a6-405f-88d2-cf44a834e06f)

As you can see it is more of an infinite loop thing.

Lets capture this request on burpsuite so we can see what's happening

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/dc70af16-588a-4f33-8636-20ed4601e6f0)

We don't need this request actually so you can just forward

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6c87d0b4-983e-42a8-acd7-303e5b7ef37a)

Yup, this is the request we are interested in. Send this over to burp repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d1ec7166-ae0e-4802-b235-5b8ac4b4dc7c)

Scrolling down to the end of the response should get you this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/afd85e15-c0fe-45b2-8a3d-adcd9bb32a2f)

Yup, that's the flag

FLAG:-```lactf{l34k1ng_4h3_f04mz_s3cr3tz}```

----------------------------

## mixed signals
<hr>

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8e227870-bd06-43c5-8f1f-b5e615f1dd01)

This one was quite easy though. I did a bit of overthinking though hehe

Open the ```.wav``` file using sonic visualizer. You can download using the command ```sudo apt-get install sonic-visualiser```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bb8a22a0-9063-4d3f-b926-07242922eada)

We have this. Well, all you just need to do is listen to the audio

When you listen you should hear something like

```
lemur
alpha
charlie
tango
foxtrap
open brace
charlie
four
november
underscore
yankee
zero
uniform
underscore
papa
lemur
zulu
underscore
uniform
november
mike
one
xray
underscore
mike
yankee
underscore
sierra
one
golf
november
four
lemur
zulu
end brace
```
Now what we'll do is since we know the ctf flag format to be ```lactf{}``` it should be obvious now😅. we'll treat the numers as numbers and also the symbols as symbols.
So we have this

```
Lemur
Alpha
Charlie
Tango
Foxtrap
{
Charlie
4
November
_
Yankee
0
Uniform
_
Papa
Lemur
Zulu
_
Uniform
November
Mike
1
Xray
_
Mike
Yankee
_
Sierra
1
Golf
November
4
Lemur
Zulu
}
```
smooth, we've gotten our flag😎

FLAG:-```lactf{c4n_y0u_plz_unm1x_my_s1gn4lz}```

-----------------------------------

# Web

## terms and conditions

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3d490ad9-36ec-4f29-b4eb-d49babadb3d3)

This also was a very easy web chall

Navigate to the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1ae336d1-cd75-4fb2-8640-7f264d4f4ec0)

You'll see from the webpage that whenever we try to click on the "I Accept" button, it moves the moment we move our cursor

Checking the page source you'll see this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/75332002-5c87-4223-83cf-b8757f5cdfe8)

This JavaScript code sets up event listeners to handle touch and mouse events on the webpage and track the coordinates of these event

There's another part to this code when you check the page source

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9f72bd22-d1ca-4d25-8135-088bbf4c033f)

This interval function continuously monitors the window size (window.innerHeight and window.innerWidth). If the window is resized, it replaces the entire body content with a message "NO CONSOLE ALLOWED". This is an attempt to prevent the user from accessing the console.

Well, to solve this we'll be using one of the developer tools

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/58d7e857-d7af-468c-8cba-262ef55e210d)

If you get a "NO CONSOLE ALLOWED" message, just refresh the tab when you get to `sources`, if you are using firefox as your browser, you'll have to go to `debugger` not `sources`. So, from the above screenshot we have the `analytics.js` script and also a file `index`. Checking out the `index` file and then scrolling all the way down you should see the Javascript code that sets up the event listeners. Also, you'll noticr that the `analytics.js` file is obfuscated. We can deobfuscate this using this [online tool](https://obf-io.deobfuscate.io/)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b668804e-4d92-4595-84d7-5e8eb8d32f4f)

```js
document.getElementById("accept").addEventListener("click", () => {
  const _0x4eb4e0 = document.getElementById("mainscript");
  if (!_0x4eb4e0 || _0x4eb4e0.innerText.length < 1000) {
    alert("silly you... you don't get to disable javascript...");
  } else {
    alert("ob`wexwkbw\\avwwlm\\tbp\\gfejmjwfoz\\mlw\\lmf\\le\\wkf\\wfqnp~".split``.map(_0x286792 => String.fromCharCode(_0x286792.charCodeAt(0) ^ 3)).join``);
  }
});
```
What we can do is run that ```alert``` script into the console

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b5062129-54bd-43bb-b037-5a9f214d1057)

We got our flag

FLAG:```lactf{that_button_was_definitely_not_one_of_the_terms}```

--------------------------------

You can find Sensei's writeup to the challs he solved [here](https://github.com/SENSEIXENUS2/SENSEIXENUS2.github.io/blob/main/posts/ctf/LActf2024/lactf.md)


Till Next Time :xD




<br> <br>
[Back To Home](../../index.md)

















