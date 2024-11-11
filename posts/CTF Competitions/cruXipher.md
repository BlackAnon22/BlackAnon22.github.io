![image](https://github.com/user-attachments/assets/cf5774df-f410-4aac-ab2d-8545bbf2a296)

I participated in the cruXipher CTF, I joined late though (5hrs before it ended). I was in search of forensics chall and yeah I found some interesting ones here.

I solved 3 forensics challs, submitted 2 flags before the ctf ended, I just completed the last one now

# Challenges Solved

## Forensics
-     objects in the mirror
-     Rick's Diary
-     xQcOw



## objects in the mirror
<hr>

![image](https://github.com/user-attachments/assets/d0d58bc8-81ea-422d-9788-45f2c4fe20de)

Upon downloading the file I got a file in the .docx format

```
┌──(bl4ck4non💀bl4ck4non-sec)-[~/…/CTF/cruxipher/forensics/objects_in_the_mirror]
└─$ ls -la           
total 84
drwxr-xr-x 2 bl4ck4non bl4ck4non  4096 Nov 11 03:37 .
drwxr-xr-x 7 bl4ck4non bl4ck4non  4096 Nov 11 01:36 ..
-rw-r--r-- 1 bl4ck4non bl4ck4non 75486 Nov  9 23:55 aviation.docx
```
When I opened the docx file with Libre Office I got this

![image](https://github.com/user-attachments/assets/66508d87-4113-4c39-8e7d-8021ad71da82)

Nothing out of the ordinary

Ever heard of `oletools`??

Well, that's what I used

![image](https://github.com/user-attachments/assets/c4d48b5f-9d9d-4e53-9efd-04b80d8b9441)

Yup, that's it

You can install with pip `sudo -H pip install -U oletools`

I started out by using `oleid`

oleid is a script to analyze OLE files such as MS Office documents (e.g. Word, Excel), to detect specific characteristics usually found in malicious files (e.g. malware). For example it can detect VBA macros and embedded Flash objects.​

![image](https://github.com/user-attachments/assets/6b2385fe-6f68-4cd8-8e1b-4b703b70dd2d)

Nothing out of the ordinary

I used the next oletool `oleobj`

![image](https://github.com/user-attachments/assets/e4ebaef3-1164-424d-9874-a350358964e9)

It extracted a png image from the docx file

Checking out the image,

![image](https://github.com/user-attachments/assets/a244f37d-633d-497c-8abf-6dff8f7867be)

I found this base64 encoded text

Decoding the text gave me the flag

```
┌──(bl4ck4non💀bl4ck4non-sec)-[~/Downloads/CTF/cruxipher/forensics]
└─$ echo "Y3J1WGlwaGVye24wd195MHVfNWUzX20zX04wd195MFVfRDBuVH0=" | base64 -d
cruXipher{n0w_y0u_5e3_m3_N0w_y0U_D0nT}
```

FLAG:-```cruXipher{n0w_y0u_5e3_m3_N0w_y0U_D0nT}```

---------------------------------------------

## Rick's Diary
<hr>

![image](https://github.com/user-attachments/assets/75edf473-9f51-44e1-93b3-251ea78e5174)













# xQcOw

![image](https://github.com/user-attachments/assets/57fdbe74-0f93-4956-9183-70cd169c2d62)
