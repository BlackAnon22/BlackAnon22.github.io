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
