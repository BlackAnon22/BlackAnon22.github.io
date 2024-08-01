![image](https://github.com/user-attachments/assets/06835cbf-6700-498d-8a4c-6c54c3f9953b)


## First Question

Run “vol.py -f infected.vmem --profile=Win7SP1x86 psscan” that will list all processes. What is the name of the suspicious process? 

command:```python3 vol.py -f ../../../blue_team_labs/memory_forensics/BTLO\ Memory\ Analysis\ -\ Ransomware/infected.vmem windows.psscan.PsScan```

![image](https://github.com/user-attachments/assets/53c76108-7172-4fc4-9233-828400537d28)

Yeah that's the suspicious process running


Answer:-```@WanaDecryptor```

----------------------------------

## Second Question

What is the parent process ID for the suspicious process?

We can tell from the output we got when we ran our command

![image](https://github.com/user-attachments/assets/0f806229-5a5a-4db4-b08c-23b6205a48b9)

Answer:-```2732```

----------------------

## Third Question

What is the initial malicious executable that created this process?

![image](https://github.com/user-attachments/assets/d2bb0a21-d00a-45f3-84df-20dbe67b340c)

We can see from the above screenshot that the executable ```or4qtckT.exe``` has the said the PPID of ```@WanaDecryptor``` as its PID

Answer:-```or4qtckT.exe```

----------------------

## Fourth Question

If you drill down on the suspicious PID (vol.py -f infected.vmem --profile=Win7SP1x86 psscan | grep (PIDhere)), find the process used to delete files

command:```python2 vol.py -f ../../../blue_team_labs/memory_forensics/BTLO\ Memory\ Analysis\ -\ Ransomware/infected.vmem --profile=Win7SP1x86 psscan | grep "2732"```

![image](https://github.com/user-attachments/assets/adb3c6ba-6dd8-4d7c-81ee-c19f0be01d77)

That's the process that's used to delete files

Answer:-```taskdl.exe```

-----------------------

## Fifth Question


