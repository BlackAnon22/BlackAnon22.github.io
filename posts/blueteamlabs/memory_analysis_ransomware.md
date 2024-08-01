![image](https://github.com/user-attachments/assets/06835cbf-6700-498d-8a4c-6c54c3f9953b)


## First Question

Run “vol.py -f infected.vmem --profile=Win7SP1x86 psscan” that will list all processes. What is the name of the suspicious process?
<hr>

command:```python3 vol.py -f ../../../blue_team_labs/memory_forensics/BTLO\ Memory\ Analysis\ -\ Ransomware/infected.vmem windows.psscan.PsScan```

![image](https://github.com/user-attachments/assets/53c76108-7172-4fc4-9233-828400537d28)

Yeah that's the suspicious process running


Answer:-```@WanaDecryptor```

----------------------------------

## Second Question

What is the parent process ID for the suspicious process?
<hr>

We can tell from the output we got when we ran our command

![image](https://github.com/user-attachments/assets/0f806229-5a5a-4db4-b08c-23b6205a48b9)

Answer:-```2732```

----------------------

## Third Question

What is the initial malicious executable that created this process?
<hr>

![image](https://github.com/user-attachments/assets/d2bb0a21-d00a-45f3-84df-20dbe67b340c)

We can see from the above screenshot that the executable ```or4qtckT.exe``` has the said the PPID of ```@WanaDecryptor``` as its PID

Answer:-```or4qtckT.exe```

----------------------

## Fourth Question

If you drill down on the suspicious PID (vol.py -f infected.vmem --profile=Win7SP1x86 psscan | grep (PIDhere)), find the process used to delete files
<hr>

command:```python2 vol.py -f ../../../blue_team_labs/memory_forensics/BTLO\ Memory\ Analysis\ -\ Ransomware/infected.vmem --profile=Win7SP1x86 psscan | grep "2732"```

![image](https://github.com/user-attachments/assets/adb3c6ba-6dd8-4d7c-81ee-c19f0be01d77)

That's the process that's used to delete files

Answer:-```taskdl.exe```

-----------------------

## Fifth Question

Find the path where the malicious file was first executed
<hr>

Since we know the malicious executable to be ```or4qtckT.exe```, we can get the path using the ```filescan``` module

command:```python2 vol.py -f ../../../blue_team_labs/memory_forensics/BTLO\ Memory\ Analysis\ -\ Ransomware/infected.vmem --profile=Win7SP1x86 filescan | grep "or4qtckT.exe"```

![image](https://github.com/user-attachments/assets/7b1edb42-ae6f-4d5f-a395-4ac1878b2d8e)

Using volatility3 for this game a more accurate answer though

![image](https://github.com/user-attachments/assets/ed7f812e-18f4-4b3f-9089-66dbcc7dd891)

Answer:-```\Users\hacker\Desktop\or4qtckT.exe```

----------------------

## Sixth Question

Can you identify what ransomware it is? (Do your research!) 
<hr>

If you recall we found the process that's used to delete files ```taskdl.exe```, doing our research on this

![image](https://github.com/user-attachments/assets/0e44f9d6-4af8-4f80-96df-a923cb397c83)

Found the name of the ransomware

Answer:-```WannaCry```

------------------------

## Seventh Question

What is the filename for the file with the ransomware public key that was used to encrypt the private key? (.eky extension)
<hr>

To solve this question we'll use the `filescan` module, since we know the extension we'll just grep it out hehe

![image](https://github.com/user-attachments/assets/46278e0c-83b1-4ade-8009-f669e2d53264)

We got our answer

Answer:-```00000000.eky```

----------------------------

![image](https://github.com/user-attachments/assets/99281c60-05cb-4128-ac8c-1de825cc3e07)

--------------------------------



Till Next Time :xD





<br> <br>
[Back To Home](../../index.md)

























