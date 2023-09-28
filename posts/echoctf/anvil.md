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

















