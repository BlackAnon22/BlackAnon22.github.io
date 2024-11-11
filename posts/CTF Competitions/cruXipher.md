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

After downloading the text file, I checked the content and saw this

![image](https://github.com/user-attachments/assets/f570fff5-7baf-4ed6-85dc-bb2cf1cc893d)

Can you see that?? 

The first time I saw a null width chall was during the Africa Cyberfest CTF, yeah yeah Nerdy set it😂. He's a maniac trust me

Opening the txt file in either vscode or sublime text shows you its true color

![image](https://github.com/user-attachments/assets/4206a2a1-c331-4023-865e-813a8ebc199c)

Yup, that's the file

I extracted the hidden file here using this [webpage](https://330k.github.io/misc_tools/unicode_steganography.html)

![image](https://github.com/user-attachments/assets/85238d8b-9841-41be-b7bd-ad5484d17aaf)

Checking the content of the hidden data

```
┌──(bl4ck4non💀bl4ck4non-sec)-[~/…/CTF/cruxipher/forensics/Ricks_diary]
└─$ ls -la hidden_data 
-rw-r--r-- 1 bl4ck4non bl4ck4non 1717 Nov 11 04:03 hidden_data
                                                                                                                                                                                              
┌──(bl4ck4non💀bl4ck4non-sec)-[~/…/CTF/cruxipher/forensics/Ricks_diary]
└─$ cat hidden_data       
getattr(globals()[''.join([(lambda x: chr(ord(x) + 1))(x) for x in '^^athkshmr^^'])],(dir(globals()[''.join([(lambda x: chr(ord(x) + 1))(x) for x in '^^athkshmr^^'])])[107]))(getattr(__import__("bkacsee3624"[::2]),''.join([(lambda x: chr(ord(x) + 1))(x) for x in 'cdbncdaxsdr']))(b'QSA9IFsxNTYyNiwgMjkxNywgMjcwNSwgMjQwMiwgMTA0MDUsIDkwMjYsIDY1NjIsIDI2MDIsIDk4MDIsIDEwODE3LCA3NzQ1LCAzMDI2LCAxMDYxMCwgOTAyNiwgNzU3MCwgMTM2OTAsIDMyNTAsIDIzMDUsIDE0MTYyLCAxNDY0MiwgMjcwNSwgOTAyNiwgMTQxNjIsIDI2MDIsIDY1NjIsIDEzOTI1LCAxMDAwMSwgMjQwMiwgMzcyMiwgMjkxNywgMTM5MjUsIDkwMjYsIDM5NzAsIDI3MDUsIDEwODE3LCAxMjEwMSwgOTgwMiwgMTIxMDEsIDEzNDU3LCAyMzA1LCA5NDEwLCAyOTE3LCAxNDE2MiwgOTAyNiwgMjIxMCwgMTI5OTcsIDExODgyLCAyNjAyLCAxMjMyMiwgMTM5MjUsIDk4MDIsIDI2MDIsIDIxMTcsIDEyMTAxLCAxMDIwMiwgOTAyNiwgOTYwNSwgMjgxMCwgMTM2OTAsIDI0MDIsIDEzNDU3LCA5MDI2LCAxMzY5MCwgMTE0NTAsIDEyMzIyLCA5ODAyLCAxNDY0MiwgMjQwMiwgMjExNywgMTI5OTcsIDE0MTYyLCAxNTEzMCwgMTI5OTcsIDE0MTYyLCAxMjk5NywgMTAyMDIsIDE0MTYyLCAxMDIwMiwgMTMyMjYsIDIyMTAsIDEwODE3LCAxNDE2MiwgMjIxMCwgMTI1NDUsIDEyMzIyLCAzMzY1LCAxMTAyNiwgMTI5OTcsIDEzMjI2LCA3NzQ1LCA5NjA1LCAxMjU0NSwgMTM2OTAsIDk2MDUsIDEzNDU3LCAxMjk5NywgMTAyMDIsIDEzNDU3LCA5ODAyLCAxNDE2MiwgMTA4MTddCkMgPSBbMTAxLCA3OCwgMTAxLCAxMzYsIGdldGF0dHIsIGRpciwgZXZhbCwgMTAxXQpZID0gJycuam9pbihbW2NocihpbnQoKGktMSkqKjAuNSkpIGZvciBpIGluIEFdWzo6LTFdW2ldIGZvciBpIGluIHJhbmdlKDEsIENbMF0gLy8gMyAtIDIsIDMpXSkKWiA9ICcnLmpvaW4oW1tjaHIoaW50KChpLTEpKiowLjUpKSBmb3IgaSBpbiBBXVs6Oi0xXVtpXSBmb3IgaSBpbiByYW5nZSgwLCBDWzJdIC8vIDMgLSAyLCAzKV0pICsgJycuam9pbihbW2NocihpbnQoKGktMSkqKjAuNSkpIGZvciBpIGluIEFdWzo6LTFdW2ldIGZvciBpIGluIHJhbmdlKDEwMSAvLyAzIC0gMSwgQ1stMV0gLSA1LCAyKV0pCkNbLTRdKENbLTJdKENbLTNdKF9fYnVpbHRpbnNfXylbQ1sxXV0pKFkpLCBDWzVdKF9fYnVpbHRpbnNfXylbQ1szXV0pKFop'))
```
Decoding the encoded text using Cyberchef

![image](https://github.com/user-attachments/assets/81899029-2fa7-4d5e-8c52-7493825bd213)

```
A = [15626, 2917, 2705, 2402, 10405, 9026, 6562, 2602, 9802, 10817, 7745, 3026, 10610, 9026, 7570, 13690, 3250, 2305, 14162, 14642, 2705, 9026, 14162, 2602, 6562, 13925, 10001, 2402, 3722, 2917, 13925, 9026, 3970, 2705, 10817, 12101, 9802, 12101, 13457, 2305, 9410, 2917, 14162, 9026, 2210, 12997, 11882, 2602, 12322, 13925, 9802, 2602, 2117, 12101, 10202, 9026, 9605, 2810, 13690, 2402, 13457, 9026, 13690, 11450, 12322, 9802, 14642, 2402, 2117, 12997, 14162, 15130, 12997, 14162, 12997, 10202, 14162, 10202, 13226, 2210, 10817, 14162, 2210, 12545, 12322, 3365, 11026, 12997, 13226, 7745, 9605, 12545, 13690, 9605, 13457, 12997, 10202, 13457, 9802, 14162, 10817]
C = [101, 78, 101, 136, getattr, dir, eval, 101]
Y = ''.join([[chr(int((i-1)**0.5)) for i in A][::-1][i] for i in range(1, C[0] // 3 - 2, 3)])
Z = ''.join([[chr(int((i-1)**0.5)) for i in A][::-1][i] for i in range(0, C[2] // 3 - 2, 3)]) + ''.join([[chr(int((i-1)**0.5)) for i in A][::-1][i] for i in range(101 // 3 - 1, C[-1] - 5, 2)])
C[-4](C[-2](C[-3](__builtins__)[C[1]])(Y), C[5](__builtins__)[C[3]])(Z)
```
This is basically where the struggle started from💀

This can be solved using the formula given 

I used this python script a friend cooked though

```python
import math

A = [15626, 2917, 2705, 2402, 10405, 9026, 6562, 2602, 9802, 10817, 7745, 3026, 10610, 9026, 7570, 13690, 3250, 2305, 14162, 14642, 2705, 9026, 14162, 2602, 6562, 13925, 10001, 2402, 3722, 2917, 13925, 9026, 3970, 2705, 10817, 12101, 9802, 12101, 13457, 2305, 9410, 2917, 14162, 9026, 2210, 12997, 11882, 2602, 12322, 13925, 9802, 2602, 2117, 12101, 10202, 9026, 9605, 2810, 13690, 2402, 13457, 9026, 13690, 11450, 12322, 9802, 14642, 2402, 2117, 12997, 14162, 15130, 12997, 14162, 12997, 10202, 14162, 10202, 13226, 2210, 10817, 14162, 2210, 12545, 12322, 3365, 11026, 12997, 13226, 7745, 9605, 12545, 13690, 9605, 13457, 12997, 10202, 13457, 9802, 14162, 10817]

# Calculate square roots of each element in A
roots = [math.sqrt(i - 1) for i in A]
print(roots)
# Manually define the square_roots array #output of roots
square_roots = [125.0, 54.0, 52.0, 49.0, 102.0, 95.0, 81.0, 51.0, 99.0, 104.0, 88.0, 55.0, 103.0, 95.0, 87.0, 117.0, 57.0, 48.0, 119.0, 121.0, 52.0, 95.0, 119.0, 51.0, 81.0, 118.0, 100.0, 49.0, 61.0, 54.0, 118.0, 95.0, 63.0, 52.0, 104.0, 110.0, 99.0, 110.0, 116.0, 48.0, 97.0, 54.0, 119.0, 95.0, 47.0, 114.0, 109.0, 51.0, 111.0, 118.0, 99.0, 51.0, 46.0, 110.0, 101.0, 95.0, 98.0, 53.0, 117.0, 49.0, 116.0, 95.0, 117.0, 107.0, 111.0, 99.0, 121.0, 49.0, 46.0, 114.0, 119.0, 123.0, 114.0, 119.0, 114.0, 101.0, 119.0, 101.0, 115.0, 47.0, 104.0, 119.0, 47.0, 112.0, 111.0, 58.0, 105.0, 114.0, 115.0, 88.0, 98.0, 112.0, 117.0, 98.0, 116.0, 114.0, 101.0, 116.0, 99.0, 119.0, 104.0]

# Convert square roots to corresponding characters
char_list = [chr(int(sqrt)) for sqrt in square_roots][::-1]

# Define the C array (for the sake of example)
C = [101, 78, 101, 136, "getattr", "dir", "eval", 101]

# Create Y
Y = ''.join([char_list[i] for i in range(2, C[0] // 3 - 2, 3)])

# Create Z
Z = ''.join([char_list[i] for i in range(2, C[2] // 3 - 2, 3)]) + ''.join([char_list[i] for i in range(102 // 3 - 1, C[-1] - 5, 2)])

# Print Y and Z
print("Y:", Y)
print("Z:", Z)
```
Running the script

```
┌──(bl4ck4non💀bl4ck4non-sec)-[~/…/CTF/cruxipher/forensics/Ricks_diary]
└─$ nano bankai.py
                                                                                                                                                                                              
┌──(bl4ck4non💀bl4ck4non-sec)-[~/…/CTF/cruxipher/forensics/Ricks_diary]
└─$ python bankai.py          
[125.0, 54.0, 52.0, 49.0, 102.0, 95.0, 81.0, 51.0, 99.0, 104.0, 88.0, 55.0, 103.0, 95.0, 87.0, 117.0, 57.0, 48.0, 119.0, 121.0, 52.0, 95.0, 119.0, 51.0, 81.0, 118.0, 100.0, 49.0, 61.0, 54.0, 118.0, 95.0, 63.0, 52.0, 104.0, 110.0, 99.0, 110.0, 116.0, 48.0, 97.0, 54.0, 119.0, 95.0, 47.0, 114.0, 109.0, 51.0, 111.0, 118.0, 99.0, 51.0, 46.0, 110.0, 101.0, 95.0, 98.0, 53.0, 117.0, 49.0, 116.0, 95.0, 117.0, 107.0, 111.0, 99.0, 121.0, 49.0, 46.0, 114.0, 119.0, 123.0, 114.0, 119.0, 114.0, 101.0, 119.0, 101.0, 115.0, 47.0, 104.0, 119.0, 47.0, 112.0, 111.0, 58.0, 105.0, 114.0, 115.0, 88.0, 98.0, 112.0, 117.0, 98.0, 116.0, 114.0, 101.0, 116.0, 99.0, 119.0, 104.0]
Y: cruXipher{
Z: cruXipher{1ck_15_n3v3r_60nn4_61v3_y0u_7h3_
```
This got me 80% of the flag, this is bsically where the guess work started from

Checking the chall description again

![image](https://github.com/user-attachments/assets/db4d660c-8949-4832-baf0-8884cc0063c5)

FLAG:-```cruXipher{1ck_15_n3v3r_60nn4_61v3_y0u_7h3_f146}```

------------------------------------------------

## xQcOw

![image](https://github.com/user-attachments/assets/57fdbe74-0f93-4956-9183-70cd169c2d62)

Upon downloading, I got a compressed file, which, after extracting, gave me a QEMU image.

I converted this image to a raw disk file using the `qemu-img` tool

![image](https://github.com/user-attachments/assets/954c2411-70a4-4b7b-8302-a98c06760a42)

Then I mounted this using autopsy

I won't be explaining how I imported the image though, I've done that in previous writeups. You can check [this](https://github.com/BlackAnon22/BlackAnon22.github.io/blob/main/posts/CTF%20Competitions/n00bz_ctf.md), [this](https://github.com/BlackAnon22/BlackAnon22.github.io/blob/main/posts/CTF%20Competitions/picoCTF_2023.md) or [this](https://github.com/BlackAnon22/BlackAnon22.github.io/blob/main/posts/CTF%20Competitions/picoCTF_2024.md)



















