I participated in the CyberStarters CTF qualifier competition organized by the Diary of Hackers, took place between April 28th to April 30th 2023. For me personally I got to learn new things

This is a writeup of the challenges I solved during the event. Lets jump right into it



# Challenges Solved
## Sanity Check
-      Discord (10 points)
-      DoHCTF{_colwSPs:(} (10 points)
-      Twitter (10 points)

## Steg
-     OK (46 points)


## Web
-     None Shall Pass (68 points)
-     ^_^ (200 points)


## Cryptography
-     di_sease (100 points)
-     Hensel's Mystery (376 points)


## Osint
-      Rogue Agent (151 points)


## BlockChain
-      Ask The Block (100 points)



# Sanity Check

## Discord (10 points)
<hr>

![image](https://user-images.githubusercontent.com/67879936/235298234-316fc094-2892-444f-a66a-6a258315dde4.png)

Clicking on the link takes us to the Disocrd Server

![image](https://user-images.githubusercontent.com/67879936/235298977-63e8fe07-b028-4bf5-9614-45dd85909311.png)

Well, scrolling down that channel we find a base64 code just sitting there

![image](https://user-images.githubusercontent.com/67879936/235298435-21aed267-1e13-41fa-a6ab-96ed6172fb96.png)

Let's go ahead and crack this ```RG9IQ1RGe3RyeV90b19iZV9oYWNrdGl2ZV9vbl9kaXNjb3JkX2hlaGVoZWhlaGVoZX0K``` since we already know it's base64 hehe

command:```echo RG9IQ1RGe3RyeV90b19iZV9oYWNrdGl2ZV9vbl9kaXNjb3JkX2hlaGVoZWhlaGVoZX0K | base64 --d```

![image](https://user-images.githubusercontent.com/67879936/235298519-6c868042-ff8f-4387-b23e-15f0485a8bf7.png)

Cool, we got our flag hehe😎

FLAG:- ```DoHCTF{try_to_be_hacktive_on_discord_hehehehehehe}```

------------------------------

## DoHCTF{_colwSPs:(} (10 points)

![image](https://user-images.githubusercontent.com/67879936/235298743-b5cd9a91-5380-4ad9-9efd-b7ce445d334c.png)

Yeah, this challenge is just to check if your sanity is still intact lool. The flag is the name of the challenge.

FLAG:- ```DoHCTF{_colwSPs:(}```

------------------------------

## Twitter (10 points)

![image](https://user-images.githubusercontent.com/67879936/235298853-a35e8f5e-9771-4aa4-bba1-2650457f6850.png)

The link redirects you to their twitter page

![image](https://user-images.githubusercontent.com/67879936/235298905-a5087195-83e5-40d0-8b24-2c1dfd228d22.png)

Following them gives us the answer to this challenge.

FLAG:- ```yes```




# Steg

## OK (46 points)
<hr>

![image](https://user-images.githubusercontent.com/67879936/235299236-3f349c01-0ba6-4f76-8a1b-7d9ebfa79359.png)

Lets download the file to our machine

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/CyberStarters_CTF/Steg]
└─$ ls    
0cold_flag.txt
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/CyberStarters_CTF/Steg]
└─$ file 0cold_flag.txt 
0cold_flag.txt: ASCII text
```
A text file, cool. Lets try to read the contents of the file

command:```cat 0cold_flag.txt```

![image](https://user-images.githubusercontent.com/67879936/235299347-304d9af4-77f9-40fc-a5ea-22af9c2c52fe.png)

oops, there seems to be some spacing after the word "Iceeeedddd". I have once solved a similar challenge and I remember using ```stegnow``` to solve it. To install stegsnow ```sudo apt install stegsnow```

command:```stegsnow -C 0cold_flag.txt```

![image](https://user-images.githubusercontent.com/67879936/235299633-dfdbafb1-b835-4209-8f5f-3d70ab972732.png)

cool, we got our flag

FLAG:- ```DoHCTF{another_quite_simple_one}```




# Web

## None Shall Pass (68 points)
<hr>

![image](https://user-images.githubusercontent.com/67879936/235300184-17bfa685-775a-4926-9a3d-187e12a8e2ca.png)

Goint to the link provided should get you this

![image](https://user-images.githubusercontent.com/67879936/235300226-dee0305c-722f-42f0-aa98-20d6211e0876.png)

Who are you?? I am BlackAnon lool😂. There was nothing else asides the ```who are you?```. There was also nothing in the source page. 

At this point I had to invite Burpsuite to join the party😎. Lets try to capture requests

![image](https://user-images.githubusercontent.com/67879936/235300773-122cb180-5928-4594-bc62-756960c8f7f6.png)
![image](https://user-images.githubusercontent.com/67879936/235300776-4ef661db-0241-426e-851c-84cda0adc453.png)

Lets send this to repeater

![image](https://user-images.githubusercontent.com/67879936/235300822-0c533f61-5461-40e6-b5a3-9f21f86cff21.png)

We can see that the cookie uses a jwt token. Lets try to crack this token. You can do that [here](https://jwt.io) 

![image](https://user-images.githubusercontent.com/67879936/235300902-08fa1697-9757-4030-b5d7-e3d24034f52c.png)

Lets try changing the guest name to ```admin```

![image](https://user-images.githubusercontent.com/67879936/235300949-a4c53bc2-4d9a-40b0-9129-b998a73ed6f6.png)

Now, lets replace the ```jwt token``` with this new one

![image](https://user-images.githubusercontent.com/67879936/235300983-415e0c71-57f3-46a5-a25e-8c2efb4ec9c0.png)

oops, We got the **_Invalid Token_** error

Well, after a bit of research I found something interesting. I remember completing the ```owasptop10 2021``` room on TryHackMe. Checking the notes I took down I saw this

![image](https://user-images.githubusercontent.com/67879936/235301152-04ee2265-0571-4cf4-8a41-457b33ad04df.png)

Now, this vulnerability falls under the owasptop10, the name of the vulnerability is ```Data Integrity Failures```. You can learn more about it [here](https://tryhackme.com/room/owasptop102021).

At this point I just had to follow what I had in my note😎. Let's go this [webpage](https://appdevtools.com/base64-encoder-decoder)

![image](https://user-images.githubusercontent.com/67879936/235301405-80656728-26e0-4111-99bf-12608fc78850.png)

This is my JWT Token ```eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Imd1ZXN0In0.iJ9U4tIUxxLbbOb_YXVkpvkBqtPsFtAxWIvmcakDfL0```. So the first part
```eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9``` is the header. The second part ```eyJ1c2VybmFtZSI6Imd1ZXN0In0``` is the payload while the last part ```iJ9U4tIUxxLbbOb_YXVkpvkBqtPsFtAxWIvmcakDfL0``` is the signature. 

So, we'll be modifying only the header and the payload. Lets start with the header

![image](https://user-images.githubusercontent.com/67879936/235301517-a5615f76-8a87-4b6c-bdee-102b37b2db08.png)

Lets go ahead and change the alg ```HS256``` to ```none```. Then we encode in base64

![image](https://user-images.githubusercontent.com/67879936/235302449-99d3c8ae-36b8-4067-b9ab-1933f9bc361d.png)

cool we have modified the header ```eyJhbGciOiJub25lIiwidHlwIjoiSldUIn0=```. Lets do the same for the payload


![image](https://user-images.githubusercontent.com/67879936/235301769-1e6b017b-40ab-4820-ba05-0fa0be7e667c.png)

Lets go ahead and change the username ```guest``` to ```admin```. Then we encode in base64

![image](https://user-images.githubusercontent.com/67879936/235301845-a267e430-85e5-40bb-a090-7234ac19d657.png)

cool, we have also modified the payload ```eyJ1c2VybmFtZSI6ImFkbWluIn0=```. 

Now, joining the ```header```, ```payload``` and ```signature``` together, we have ```eyJhbGciOiJub25lIiwidHlwIjoiSldUIn0=.eyJ1c2VybmFtZSI6ImFkbWluIn0=.iJ9U4tIUxxLbbOb_YXVkpvkBqtPsFtAxWIvmcakDfL0```.

The last thing left to do is replacing the old ```jwt token``` to the modified one

![image](https://user-images.githubusercontent.com/67879936/235302491-284ce616-81b5-4af2-85e6-08b83fe27d83.png)

showing this response in the web browser

![image](https://user-images.githubusercontent.com/67879936/235302623-902b5b79-bddb-4b66-94b4-f75bfe8b3c80.png)

We got our flag😎

FLAG:- ```DoHCTF{jwt_has_a_none_algo_loll}```

------------------------------

## ^_^ (200 points)

![image](https://user-images.githubusercontent.com/67879936/235378245-a1d74b2d-b358-4f74-869b-f9c393468763.png)

We were told not to bruteforce lool, this means we don't need directory fuzzing tools. Lets navigate to the webpage

![image](https://user-images.githubusercontent.com/67879936/235378390-a7436bb1-bcce-42cf-8a70-89b25f205501.png)

We get this, take note of the url

![image](https://user-images.githubusercontent.com/67879936/235378439-a6e49bb8-d52e-401e-bff8-b2589bfcacf7.png)

Now, those look like base64 code. Checking the source page

![image](https://user-images.githubusercontent.com/67879936/235378469-748ca325-60c8-4caa-be6c-238dda6d5d6f.png)

We get 2 more directories also looking like base64 code. Now, trying to crack this was giving me some weird strings.

What do I mean??

These are the directories that look base64 ish

```
/GgoXAQ4QGxMCHA4ZA1JKDFlWAEFRG1YQGw/c2RzZHZ5dXdnZGd3ZzcyZTcyZTk4dTJ1Yw
/HwEBBw0WGQ0HAQEaVBYcEAwHHw0QHRAaHxAdEAEQ/c2R1c2hkdWhzdWRoOHNoZGl1c2hkaXVoc3VpZGRi
/ISdFLDRLKitfPDRKRT0SCRcHEBIIFwsTEg/QEUqWUAqSEQqSFUoKkhmaHVoZWZpdWRmZg
```
Lets try to crack one of these example ```ISdFLDRLKitfPDRKRT0SCRcHEBIIFwsTEg```

command:```echo ISdFLDRLKitfPDRKRT0SCRcHEBIIFwsTEg | base64 --d ```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/CyberStarters_CTF/Web]
└─$ echo ISdFLDRLKitfPDRKRT0SCRcHEBIIFwsTEg | base64 --d                  
!'E,4K*+_<4JE=  
               base64: invalid input
```
Now, this is the weird string I was talking about. 

Well, I had to sacrifice 20 points to get hint so as to know the next course of action

![image](https://user-images.githubusercontent.com/67879936/235379173-8eb2e2b2-a518-4f34-a1df-41c318b5f8dc.png)

Now, from the hint we got ```^ bitwise operation```. I also noticed that for the directories the base64 has the same length (i.e before and after the /). 

We'll be xoring ```HwEBBw0WGQ0HAQEaVBYcEAwHHw0QHRAaHxAdEAEQ``` with ```c2R1c2hkdWhzdWRoOHNoZGl1c2hkaXVoc3VpZGRi``` to see if we can get something.

I'll be using this python script

```
import base64

# Example base64 encoded strings
encoded_str1 = "HwEBBw0WGQ0HAQEaVBYcEAwHHw0QHRAaHxAdEAEQ"
encoded_str2 = "c2R1c2hkdWhzdWRoOHNoZGl1c2hkaXVoc3VpZGRi"

# Base64 decode the encoded strings
decoded_str1 = base64.b64decode(encoded_str1)
decoded_str2 = base64.b64decode(encoded_str2)

# XOR the two decoded strings
xored_str = bytes([a ^ b for a, b in zip(decoded_str1, decoded_str2)])

# Print the result
print(xored_str)
```
This script demonstrates how to perform XOR operation between two base64-encoded strings

Lets run it

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/CyberStarters_CTF/Web]
└─$ ls
abeg.py
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/CyberStarters_CTF/Web]
└─$ python abeg.py
b'letterletterletterletterletter'
```
cool, I got this. Fortunately they gave a free hint which goes like this

```
indexindexindexindexindex
aboutaboutaboutaboutabout
letterletterletterletterletter
flagflagflagflagflag
```
From our script we ran earlier we can tell that we are on the right path. Now, what we have to do is to look for a way to encode the ```flagflagflagflagflag``` to it's base64 representation then we xor null byte with null byte which will give A. After we can make the length of the base64 encoded form of A to be equal to len of null byte which is 28.

The reason why we are using null byte is because when you xor something with zero you get that samme value being xored and when you xor two things that are the same you get zero.

For this we'll be using a python script

```
from pwn import xor
import base64 as b

flag = b'flagflagflagflagflag'
encoded_flag = b.b64encode(flag)

null = b'0x0'
xored = xor(null, null)
second_ = b.b64encode(xored) * 7


print(encoded_flag+b'/'+second_)
```
Save this script and run it

![image](https://user-images.githubusercontent.com/67879936/235380419-ae235849-fdd3-4310-a6b3-a4da7799cc66.png)

We got the output we wanted, lets navigate to this directory, hopefully we get our flag

![image](https://user-images.githubusercontent.com/67879936/235380484-4591b648-3999-4b52-a8c4-9450537d9bee.png)

cool, we got our flag😎

FLAG:- ```DoHCTF{xor_rox_xor}```




# Cryptography

## di_sease (100 points)
<hr>

![image](https://user-images.githubusercontent.com/67879936/235299869-af38d1d0-65e4-4b34-8599-bacb7c4d4719.png)

Lets download the file to our machine

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/CyberStarters_CTF/Cryptography]
└─$ ls 
flag.png
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/CyberStarters_CTF/Cryptography]
└─$ file flag.png      
flag.png: PNG image data, 814 x 156, 8-bit/color RGBA, non-interlaced
```
Okay,this is a PNG image. Lets try to use ```zsteg``` on the image, we might find something interesting hehe

command:```zsteg flag.png```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/CyberStarters_CTF/Cryptography]
└─$ zsteg flag.png      
meta Software       .. text: "gnome-screenshot"
meta Creation Time  .. text: "Thu 27 Apr 2023 14:24:34"
b1,r,msb,xy         .. file: Unicode text, UTF-32, big-endian
b1,rgba,lsb,xy      .. text: ["w" repeated 8 times]
b1,abgr,msb,xy      .. text: ["w" repeated 8 times]
b2,r,lsb,xy         .. text: "UUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUP"
b2,rgba,lsb,xy      .. text: ["?" repeated 17 times]
b2,abgr,msb,xy      .. text: ["?" repeated 17 times]
b4,r,lsb,xy         .. text: ["U" repeated 247 times]
b4,g,lsb,xy         .. text: ["w" repeated 247 times]
b4,b,lsb,xy         .. text: "333333337wwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwwww"
b4,rgb,lsb,xy       .. text: "5wWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwW"
b4,bgr,lsb,xy       .. text: "uwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuwWuw"
```
oops, nothing

Lets try to check what the image is all about

![image](https://user-images.githubusercontent.com/67879936/235300118-10580208-924d-4487-89c6-7cc19dd31c40.png)

hehe, this is a ```navy signal code```. We'll be using [dcode.fr](https://www.dcode.fr/symbols-ciphers) for this.

![image](https://user-images.githubusercontent.com/67879936/235303013-e68435de-769d-4e30-a125-681cdc736e80.png)

![image](https://user-images.githubusercontent.com/67879936/235305412-497a3665-26af-4d28-aa8e-50bb3724127e.png)

We got something ```DOHCTFTHEFLAGSREVEALED009```, looks like the flag, but it is not the flag because that is not the right format.

Lets rearrange it

FLAG:- ```DoHCTF{The_flags_revealed_009}```

------------------------------

## Hensel's Mystery (360 points)

![image](https://user-images.githubusercontent.com/67879936/235305639-2c32e020-561d-4c1e-99f1-c95e1e226819.png)

Lets download the files to our machine

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/CyberStarters_CTF/Cryptography]
└─$ ls    
flag.png  output.txt  ring.py
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/CyberStarters_CTF/Cryptography]
└─$ file output.txt  
output.txt: ASCII text, with very long lines (884)
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/CyberStarters_CTF/Cryptography]
└─$ file ring.py   
ring.py: Python script, ASCII text executable
```
We got ourselves an ASCII text and a Python script.

The content of both files

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/CyberStarters_CTF/Cryptography]
└─$ cat output.txt 
45406770103725904509890104231914678754265961643298482440409237765195072368733672685631587979562241346*x^4 + 42764372489624602989152383173709795403796386376344802703066528962696589468564501897000324538498812883*x^3 + 37672731284607729155480237866218406485893919987814572486490754064498223292180995037432012350216544417*x^2 + 55462425449896168600390367564436787134741290054741525865807795492693442375757671549228298754153509613*x + 6778690755895128168751737959454411972187106669733266559106651743590246692689398562032067795146717162848413292299573013038367117575935673619248776925892672201933424467005517162118712395701681263279585553299544107860626811206695844212433182471614373859755499052750286667585910623259340579702249091680614010546399687179863049582625671630876108790555962058243905551470611736992489702159306356102118074450673803009393106039180751255185874156459283395261688861
                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/CyberStarters_CTF/Cryptography]
└─$ cat ring.py   
from sage.all import *
import codecs

def read_flag():
    with open('flag.txt', 'r') as file:
        return file.read().strip()

def encode_flag(flag):
    encoded = codecs.encode(flag.encode(), 'hex')
    return int(encoded, 16)

def generate_polynomial(flag):
    ranges = int(log(flag, 2))
    p = 35671
    k = 100
    N = p**k
    d = 5
    P = PolynomialRing(Zmod(N), names='x', implementation='NTL')
    x = P.gen()
    poly = 0
    for c in range(d):
        poly += ZZ.random_element(2**ranges, 2**(ranges+1))*x**c
    remainder = poly(flag)
    poly = poly - remainder
    assert poly(flag) == 0
    return poly

def main():
    flag = read_flag()
    encoded_flag = encode_flag(flag)
    poly = generate_polynomial(encoded_flag)
    print(poly)

if __name__ == '__main__':
    main()
```
what does this script do??

<font color="Green">This Python script uses the SageMath library to generate a polynomial with a specific property. The polynomial is generated based on an encoded flag read from a file called "flag.txt". The encoding of the flag is done by converting the flag string to its hexadecimal representation and then converting the hexadecimal representation to an integer.</font>







# Osint

## Rogue (151 points)
<hr>

![image](https://user-images.githubusercontent.com/67879936/235303832-d12a0b72-2bb4-457e-9adf-b439d7fc8149.png)

So task is to look for a guy whose name is ```Mustapha```.

What information were we provided with?

1. Third Name which is ```Mustapha```
2. A phone number ``` +2348109439442 ```

I tried lots of stuffs, downloaded lots of osint tools and still didn't get anywhere😞. Not until I thought of PalmPay😂, and this is because PalmPay do use the phone number of their clients as their account numbers. In this case the account number will be ```8109439442```. Lets try sending money to this account number, if we are lucky we'll see his full name there.

![image](https://user-images.githubusercontent.com/67879936/235340128-0ce8c8a6-fe0b-46a4-91cd-9f38864efacc.png)

Well Well Well, We found a name ```Adebayo Ekeh```, if you recall they provided us with a third name ```Mustapha```. Now, lets go over to LinkedIn to look for our rogue hacker. 

fullname: ```Adebayo Mustapha Ekeh```

![image](https://user-images.githubusercontent.com/67879936/235340215-102c4624-dec7-4026-a72f-1a4e94d1e209.png)

cool we found our rogue hacker😎. Lets decode the base64 code

command:```echo  RG9IQ1RGe3RoYXRfd2FzX2Vhc3lfcmlnaHQ/X3JpZ2h0P30K  | base64 --d```

![image](https://user-images.githubusercontent.com/67879936/235340319-0404652e-2be1-4ac2-b725-af10eea60230.png)

We found our flag

FLAG:- ```DoHCTF{that_was_easy_right?_right?}```





# BlockChain

## Ask The Block (96 points)
<hr>

![image](https://user-images.githubusercontent.com/67879936/235304296-1918bc10-e1ca-4d8e-b6a0-aff69138c203.png)

I really don't know much about Web3, so I used chatgpt for this chall. When I asked chatgpt what Goerli means and how I can identify the blocks, I got this response

Here are the steps you can follow:

1. Go to a blockchain explorer website such as Etherscan or Blockchair.
2. Search for the Goerli testnet.
3. Look for the block explorer or block search function.
4. Enter the block number that you want to check.
5. Look for the list of transactions in that block.
6. Check if there is at least one transaction with a non-zero value.

Doing further research I found this [site](https://goerli.etherscan.io/blocks). 

![image](https://user-images.githubusercontent.com/67879936/235304641-133d5365-ed86-4e64-ab03-75a54929f39a.png)
![image](https://user-images.githubusercontent.com/67879936/235304673-eaa62991-4a08-4772-a35c-e01f2c5ece45.png)

change the ```show rows``` to ```100```, this made the search faster. Also, we'll be starting from the last transactions

![image](https://user-images.githubusercontent.com/67879936/235304749-3380c9dc-de3c-4a4d-8c10-fa5d276308eb.png)

when the ```Txn``` has the value ```1``` we are going to take note of that block. If you recall the task description was to get **_First block on Goerli with non-zero transaction_**. 

After lots of clicking, I eventually found one

![image](https://user-images.githubusercontent.com/67879936/235304912-2237cf55-aa64-4c79-8dbc-ddfcf4d09a54.png)

cool, we got our flag already😎

FLAG:- ```DoHCTF{5644}```
    
    
    





























