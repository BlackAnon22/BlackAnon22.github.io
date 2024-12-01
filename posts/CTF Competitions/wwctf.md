![image](https://github.com/user-attachments/assets/d4d99342-4666-4db5-bee8-bc4f1c2828cc)

Navigating to the webpage

![image](https://github.com/user-attachments/assets/9750472d-b36c-42df-8297-537ccf48424e)

I got this, now from the looks of things here I knew immediately that it has something to do with command injection

Running the `ls` command, I got this

![image](https://github.com/user-attachments/assets/105c10af-e6dd-4b9b-8ad4-e41e6669f0df)

There's an `index.php` file

But then this command `cd ../../ && ls` gets flagged

![image](https://github.com/user-attachments/assets/8ae8addb-373d-4572-8a90-ec67fc8735f6)

This didn't bother me actually because I saw something similar when I played `picoctf 2023`, you can read the writeup [here](https://github.com/BlackAnon22/BlackAnon22.github.io/blob/main/posts/CTF%20Competitions/picoCTF_2023.md)

![image](https://github.com/user-attachments/assets/1ee40418-34f7-43b5-8bb4-fa3cf7ef9842)

This should work actually
