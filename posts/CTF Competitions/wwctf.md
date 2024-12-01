![image](https://github.com/user-attachments/assets/fdb27919-3ef8-4661-82ac-368ea73d0e41)

# Challenges Solved
## Beginner
-      Secure Shell
-      Simpler RSA


# Beginner
<hr>

## Secure Shell

![image](https://github.com/user-attachments/assets/d4d99342-4666-4db5-bee8-bc4f1c2828cc)

Navigating to the webpage

![image](https://github.com/user-attachments/assets/9750472d-b36c-42df-8297-537ccf48424e)

I got this, now from the looks of things here I knew immediately that it has something to do with command injection

Running the `ls` command, I got this

![image](https://github.com/user-attachments/assets/a7688e55-0511-4591-a304-7ce67bd598a2)

There's an `index.php` file

But then this command `cd ../../../ && ls -la` gets flagged

![image](https://github.com/user-attachments/assets/8ae8addb-373d-4572-8a90-ec67fc8735f6)

This didn't bother me actually because I saw something similar when I played `picoctf 2023`, you can read the writeup [here](https://github.com/BlackAnon22/BlackAnon22.github.io/blob/main/posts/CTF%20Competitions/picoCTF_2023.md)

![image](https://github.com/user-attachments/assets/1ee40418-34f7-43b5-8bb4-fa3cf7ef9842)

This should work actually

Now, instead of using the `cd ../../../ && ls -la` command, I did this instead `echo "$(cd ../../../ && ls -la)"`

![image](https://github.com/user-attachments/assets/fb51142f-94cf-44c7-b1c9-5d1cfdb3ea6b)

All that's left now is to read the flag, this command should do it `echo "$(cd ../../../ && cat flag)"`

It is evident from the above screenshot that the `flag` file most likely contains the flag but then it has read-only access, while the `readflag` is an executable that likely allows me to read the `flag` file.

All I did to get the flag was to run `readflag` executable using the command `echo "$(cd ../../../ && ./readflag)"`

![image](https://github.com/user-attachments/assets/5bb269f8-9f28-488a-b7f7-13e6a0b6b735)

Got the flag

FLAG:-```wwf{th3_os_c0mm4nd_1nj3ct10n!}```

--------------------------


























