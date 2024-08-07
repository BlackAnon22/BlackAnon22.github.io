![image](https://github.com/user-attachments/assets/19e5fe6f-9afa-4778-b421-8df1226d34e6)


# Challenges Solved
## Misc
-      Sanity Check

## OSint
-     Tail

## Forensics
-     Plane
-     Wave
-     Disk Golf

## Blockchain
-     EVM - The Basics
-     EVM - Conditions


# Misc

## Sanity Check
<hr>

![image](https://github.com/user-attachments/assets/786a91ea-840c-4e59-86e1-b63a437dfcbb)

Checking the announcement channel on the discord server should get you the flag

![image](https://github.com/user-attachments/assets/d835ae86-386a-4400-9adb-f0756ce0efbd)

FLAG:-```n00bz{w3lc0m3_t0_n00bzCTF2024!}```

--------------------------------

# Osint

## Tail
<hr>

![image](https://github.com/user-attachments/assets/db03886c-812c-45e5-b693-29407eccc01a)

Checking the image

![image](https://github.com/user-attachments/assets/972b2423-2cbc-471d-9918-90c62dd3105a) 

We have this, so the task is to find the airline's hub (the airport where they mostly operate from). Use the three letter airport IATA code and wrap it in n00bz{}.

Doing a reverse image search

![image](https://github.com/user-attachments/assets/1d6473a6-ac0e-4bda-b8b6-0eb340dd9d5b)

I didn't find anything interesting, so I just did this instead

![image](https://github.com/user-attachments/assets/598dae29-eae0-4f71-9f2b-bfa6595f4f77)

Yup😂, So I found the airplane's hub to be ```Air Tahiti Nu```, the next thing now is to find the IATA code

![image](https://github.com/user-attachments/assets/d7dd7577-df87-4964-a549-9fd2ed75f50a)

That's the IATA code

FLAG:-```n00bz{PPT}```

---------------------------------------

# Forensics

## Plane
<hr>

![image](https://github.com/user-attachments/assets/f78aa717-f8d0-478a-83aa-9d5703856ce9)

Download the file to your machine

![image](https://github.com/user-attachments/assets/cc138ba2-364b-4299-a5b5-c59c101bbd63)

Checking the content of the image

![image](https://github.com/user-attachments/assets/847bddb5-73a2-4867-a5c4-88b1b5c217bc)

The task is to get the latitude, longitude of the place this picture is taken from, rounded upto two decimal places. 

Lets use ```exiftool``` on this image

![image](https://github.com/user-attachments/assets/73582024-6297-427c-8257-8416cb0e4f46)

Using [this](https://latlongdata.com/lat-long-converter/) online calculator I was able to solve this challenge

![image](https://github.com/user-attachments/assets/e21bcd57-176c-4202-acf4-6ac460e3a896)

We got our flag

FLAG:-```n00bz{13.37,-13.37}```

------------------------

## Wave
<hr>

![image](https://github.com/user-attachments/assets/df47bb94-8f54-4499-ac75-a073737b8318)

Download the file to your machine

![image](https://github.com/user-attachments/assets/db3df228-41e8-407e-8c9e-f33682c86ea1)

We have a wav file but as you can see from the above screenshot, it's not showing that. This can only mean one thing (the file signature has been messed with)

Lets use Hexeditor to check the file signature

command:```hexeditor chall.wav```

![image](https://github.com/user-attachments/assets/2d65abb3-2c1c-4241-8995-dacacfbc3424)

Yup, it has been messed with.

Lets get the correct file signature

I downloaded a wav sample online 

![image](https://github.com/user-attachments/assets/ed46eb6d-c424-4095-bd6d-f95c259b0e25)

Then I checked the magic bytes using ```hexeditor```

command:```hexeditor (filename)```

![image](https://github.com/user-attachments/assets/266dc846-b817-42b1-8403-6b5c379a2a34)

Niceeeeeeeee, now lets correct our ```chall.wav`` file

![image](https://github.com/user-attachments/assets/032bb233-9ec2-4600-b27e-c49032c9b0cd)

```ctrl + x``` to save

Runnng the ```file``` command again

![image](https://github.com/user-attachments/assets/3032e4c0-72d3-4ca9-9ab2-4f781a584136)

Niceeeeeeeeeee, playing the wav file I found it to be morse code, to solve the challenge we can use morse decoder

Lets use [this](https://morsecode.world/international/decoder/audio-decoder-adaptive.html)

![image](https://github.com/user-attachments/assets/0a6adc16-fcea-4ccc-b933-cf1132fad15c)

We found our flag

FLAG:-```n00bz{BEEPBOPMORSECODE}```

-------------------------

## Disk Golf
<hr>

![image](https://github.com/user-attachments/assets/991eac61-66b9-4482-a5fe-98a07ab13f3d)

Download the file to your machine and extract

![image](https://github.com/user-attachments/assets/78eb1dd2-c9b9-4cb1-a2d4-f32524b0a34e)

I love disk challs hehe, this one was quite easy though (easier than sanity check hehe💀)

For some unknown reasons I couldn't mount this using the mount command, so I used Autopsy instead

![image](https://github.com/user-attachments/assets/e8e9d864-a0f7-404d-ab90-cb60d6696583)
![image](https://github.com/user-attachments/assets/2b595494-5022-4fe9-8dbb-513c54886e6e)
![image](https://github.com/user-attachments/assets/501a6592-bef9-4c24-a248-b8d6ac726a2a)
![image](https://github.com/user-attachments/assets/c14d4aa6-e037-4370-976e-0b0593e7e57a)
![image](https://github.com/user-attachments/assets/b97d9528-c476-4414-94cf-2954b54c4a85)
![image](https://github.com/user-attachments/assets/f21fe897-1019-4c84-8915-f6ad710adc75)
![image](https://github.com/user-attachments/assets/ff6ff031-265f-4e85-b3a5-8c39dced6deb)
![image](https://github.com/user-attachments/assets/5e827a4f-c88f-43bf-abeb-7c7107a84b74)
![image](https://github.com/user-attachments/assets/cdf5b580-0987-4513-9823-d8d42e6e7efe)
![image](https://github.com/user-attachments/assets/3265031d-0111-4664-bdb2-cf0f006d2e38)
![image](https://github.com/user-attachments/assets/c7004702-d0ed-40af-88e1-09054e169a77)
![image](https://github.com/user-attachments/assets/507248e6-22bd-422e-8942-944261e27985)
![image](https://github.com/user-attachments/assets/43f55253-604c-4729-882f-7cfe83e48e7f)

We've successfully mounted the disk image

Now, to get the flag just search for "flag.txt" (ezzzz right??)

![image](https://github.com/user-attachments/assets/f947ff03-7d4d-4316-8a40-82daaad6a58f)

Checking the content

![image](https://github.com/user-attachments/assets/eb9f2cd2-c725-4296-a91a-1554a705cbb7)

This looks like Ascii Code, lets decode

![image](https://github.com/user-attachments/assets/858457f5-0d3d-4bda-aabf-eb5977524838)

FLAG:-```	n00bz{7h3_l0ng_4w41t3d_d15k_f0r3ns1c5}```

------------------------------------------------

# Blockchain

## EVM - The Basics
<hr>

![image](https://github.com/user-attachments/assets/b5f7e563-a3a1-48e2-9e06-68468283d2f1)

The task is to find the value, in hex, that you need to send to make the contract STOP and not self destruct.

We were given a txt file, checking the contents of the file

![image](https://github.com/user-attachments/assets/9cfc1d36-f7e0-4ff2-9083-81d41446e8ed)

This is an EVM ByteCode, so we can use an online bytecode decompiler to decompile

Lets use [this](https://ethervm.io/decompile)

![image](https://github.com/user-attachments/assets/5c15e67c-57d1-4f19-ace4-1a07d50211fe)
![image](https://github.com/user-attachments/assets/ef0ddb37-0aa6-43b6-b5a4-2e0ce8039154)

This is a code snippet written in EVM (Ethereum Virtual Machine) bytecode. Specifically, it appears to be a smart contract written in a low-level, assembly-like language used for Ethereum smart contracts.

I actually can't read this so I had to look for another decompiler

I found [this](https://app.dedaub.com/decompile)

![image](https://github.com/user-attachments/assets/ab01f220-570a-4263-88f6-b4334a6cc1ad)
![image](https://github.com/user-attachments/assets/73eaa1a1-4f2a-4fa4-9163-b0c798bd6618)

Finally, a code I can read

```sol
function function_selector() public payable { 
    assert(0xfdc29ff358a3 != 4919 * msg.value);
    selfdestruct(0);
}
```
Before I explain this, lets convert that hex value to decimal hehe

```sol
function function_selector() public payable { 
    assert(279012349008035 != 4919 * msg.value);
    selfdestruct(0);
}
```
Now I can explain what this piece of code does

```
1. Receives Ether: The function can accept Ether when called due to the payable keyword.

2. Assertion Check: It checks if the product of 4919 and the amount of Ether sent (msg.value) does not equal 279012349008035. If this condition is false, the transaction reverts.

3. Self-Destruct: If the assertion passes, the contract self-destructs and sends all its remaining Ether to the zero address (0), effectively burning the Ether.
```
Let me break it down further, the contract stops if
```
279012349008035 == 4919 * msg.value
```
This is more a maths issue lool, to get the ```msg.value``` we can just do this
```
msg.value == 279012349008035/4919
```
Lets get the value

![image](https://github.com/user-attachments/assets/9fd033cc-b118-4de0-adf1-17a614811ddd)

Niceeee, lets convert that to hex using [this](https://www.dcode.fr/hexadecimal-system)

![image](https://github.com/user-attachments/assets/c78e4f44-4044-4eb4-bfbd-c3a4ffea5582)

We found our flag already😎

FLAG:-```n00bz{0xd34db33f5}```

-----------------------------------

## EVM - Conditions
<hr>

![image](https://github.com/user-attachments/assets/c07f248e-9c2a-4d04-9b27-75bd371397fc)

A similar task, lets check the content of the txt file we were given

![image](https://github.com/user-attachments/assets/6d2342c9-5bd4-406c-85be-140780faa43f)

Lets decompile with [this](https://app.dedaub.com/decompile)

![image](https://github.com/user-attachments/assets/725a67aa-d598-41ea-9f6c-2833ea726ee3)
![image](https://github.com/user-attachments/assets/b7b6fe4d-a894-4b1d-9cc6-1939fa0d0df2)

I'm not reading this😂

![image](https://github.com/user-attachments/assets/e08cf989-4d0c-4f84-b54a-aa0fe12a4e4c)

Yup, this is better

```sol
function function_selector() public payable { 
    assert(6750 + msg.value != 0xdb15fe);
    selfdestruct(0);
}
```
Just as I did in the last challenge, I'll be converting the hex to decimal

```sol
function function_selector() public payable { 
    assert(6750 + msg.value != 14358014);
    selfdestruct(0);
}
```
Now, let me explain what this piece of code does

```
1. Function: function_selector can receive Ether (payable) and is publicly accessible (public).

2. Assertion Check: It checks if 6750 + msg.value is not equal to 14358014. If they are equal, the assertion fails, and the transaction reverts.

3. Selfdestruct: If the assertion passes (meaning 6750 + msg.value is not equal to 14358014), the contract self-destructs and sends all its remaining Ether to the zero address (0), effectively burning the Ether.
```
Let me break it down further, the contract stops if
```
6750 + msg.value == 14358014
```
So, to get our ```msg.value``` we can do this
```
msg.value == 14358014 - 6750
```
Lets calculate this

![image](https://github.com/user-attachments/assets/b8c1d4d2-097d-4568-aac9-efb4e61bba86)

Now, we can convert ```14351264``` to hex using [this](https://www.dcode.fr/hexadecimal-system)

![image](https://github.com/user-attachments/assets/660e42a0-0c92-4ec9-88c2-22bea6a06cf6)

Yup, that's our flag

FLAG:-```n00bz{0xdafba0}```

-------------------

You can check out sensei's writeup [here](https://senseixenus.github.io/posts/ctf/n00bzctf/writeup.html)

Till Next Time :xD




<br> <br>
[Back To Home](../../index.md)


















