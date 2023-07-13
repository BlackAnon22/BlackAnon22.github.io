I will be solving the Natas Labs from OverTheWire. OverTheWire is a platform that can help you learn and practice security concepts in the form of fun-filled games.

PS: As I keep solving the labs, I'll be adding them to this writeup

Lets get started


# Level 0

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8db0502f-7e0c-4055-a754-7b15db9a8598)

Navigating to the webpage using the username and password provided

username:```natas0```          password:```natas0```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3acaf2bd-157c-4580-808b-e075e98350e4)

Viewing the source page,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/49879ba8-ec1e-4bcb-80c5-88f7b6065111)

We found the password for the next level.



# Level 1

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7f3c6dac-8014-4e32-a44e-c8c83a746ca0)

Navigating to the webpage and using the password we got from the previous level

username:```natas1```            password:```g9D9cREhslqBKtcA2uocGHPfMZVzeFK6```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/722e7670-42e3-478f-be2d-35bae9a46d80)

Rightclicking has been blocked, this means we can't rightclick on the webpage

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9dbb3f81-a213-4381-a495-83092c4ba523)

To view the source page, you can use ```ctrl + u``` 

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/58bdebd5-4fc0-45d5-af47-86bb6221c9d7)

cool, we found the password to the next level😎



# Level 2

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a4593d92-45be-463b-9d0f-66c4018cba35)

Navigating to the webpage and using the password we got from the previous level

username:```natas2```                password:```h4ubbcXrWqsTo7GGnnUMLppXbOogfBZ7```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e3d6602e-5b49-4b91-9d25-b9751903c9fb)

Checking the source page,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6a392a9b-209f-461e-9628-6b1e601a4831)

 From the above screenshot, you see this ```<img src="files/pixel.png">```.

This is a png image, this means the image is located in the url ```http://natas2.natas.labs.overthewire.org/files/pixel.png```, what if we were to go back a directory, we would then have ```http://natas2.natas.labs.overthewire.org/files```. Navigating to the webpage, you have this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2c0cc6d8-6224-4e06-a1d1-c9bcc114b1f9)

Viewing the ```users.txt``` file,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5f11fc2a-92c5-4a0f-86f1-e176b2286748)

We have the password for the next level.



# Level 3

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0c6847f0-a5db-46a3-95df-40ccd09a327e)

Navigating to the webpage and using the password we got from the previous level

username:```natas3```        password:```G6ctbMJ5Nb4cbFwhpMPSvxGHhQ7I6W8Q```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2b375b0b-ff94-45d7-bf95-4267fbceb35a)

Viewing the source page,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/431bf817-d077-4be5-96b8-46a4c9863a0d)

Now that was a bold statement😂.

Well, navigating to the ```/robots.txt``` directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/74a98d89-ec44-41f5-b134-8e366b0979df)

Navigating to the ```/s3cr3t/``` directory

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9b60e187-76a5-4441-a4b4-180d9b093c00)

Lets check out the ```users.txt``` file.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/159b1194-5fef-4980-839c-b232717226af)

cool, we got the password for the next level.



# Level 4

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a81cdd7a-1cba-47f9-b407-dd34b3fc70b8)

Navigating to the webpage and using the password we got from the previous level

username:```natas4```            password:```tKOcJIbzM4lTs8hbCmzn5Zr4434fGZQm```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9b1d174f-9d29-420c-871b-6a1e26d58087)

To access the website successfully, we need to ensure that you are visiting it from the specified URL.

To do this, we'll try to modify our request to include the correct source url.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2e5b9515-9c6c-46de-8d4f-c3bc36b283b6)

We'll be using the "Referer" header here

<font color="green">The Referer header in an HTTP request provides information about the URL of the previous webpage that linked to the current page. It helps websites and servers track the origin of incoming traffic and understand how users navigate through different webpages.</font>

Modifying our request,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/374c7456-fc44-437c-92c1-fc2b4d008bbf)

Cool, we found the passowrd for the next level.



# Level 5

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2e3413fc-d301-45c8-9d61-59fdcd26954d)

Navigating to the webpage and using the password we found in the previous level

username:```natas5```          password:```Z0NsrtIkJoKALBCLi5eqFfcRN82Au2oD```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4eb4c242-7337-4751-b27c-5c6b61b36d43)

It is saying here that we are not logged in. Lets capture the request using burpsuite

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bb0e5685-de9f-483a-b023-ff9d83baee42)

Looking at the captured request again;

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b62aa7a9-8a8e-4de2-bc4e-87f25e55286b)

For the cookie header, you see that ```loggedin``` has a value of ```0```. 

What happens when we change that value to ```1```??

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/efa40c80-31b3-44bc-a5e4-d3e4dd747084)

cool, we got the password for the next level😎



# Level 6

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f149d3fc-8764-4fbf-89ef-747cb403047e)

Navigating to the webpage and using the password we found in the previous level

username:```natas6```        password:```fOIvE0MDtPTgRhqmmvvAOt2EfXR6uQgR```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/67486b51-ad4c-4d7a-a814-499b3373467c)

We are asked to provide a secret.

Well, let me try this secret, be sure not to tell anybody hehe. **_I am spiderman_**, inputting that secret

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/28b5e367-891a-4d3d-9814-f33b9a084a37)

As you can see we got an error message.

Viewing the source page;

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/40147890-6d1a-4e77-af75-b130580eddf6)

We got this php code

```php
<?

include "includes/secret.inc";

    if(array_key_exists("submit", $_POST)) {
        if($secret == $_POST['secret']) {
        print "Access granted. The password for natas7 is <censored>";
    } else {
        print "Wrong secret";
    }
    }
?>
```
Explaining the code
```
1.It includes the contents of the file "includes/secret.inc" using the include statement. This allows the code to access variables or functions defined in that file.
2.It checks if the "submit" key exists in the $_POST superglobal array, indicating that a form has been submitted via the HTTP POST method.
3.If the "submit" key exists, it compares the value of the $secret variable with the value of the 'secret' field submitted through the form ($_POST['secret']).
4.If the values match, it prints the message "Access granted. The password for natas7 is <censored>". This suggests that upon successful submission of the correct secret, it reveals the password for the "natas7" user.
5.If the values do not match, it prints the message "Wrong secret", indicating that the submitted secret is incorrect.
```
Now, lets navigate to the directory ```/includes/secret.inc```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b77b9b19-8ebe-4d67-b153-a71cf7d4c413)

oops, a blank page😰

Viweing the page source;

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/257b747b-0c4f-468a-b99b-093734846546)

We found our secret hehe, submitting the secret should get us the password for the next level

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d6d51558-b97f-42a4-bad0-62418c6c5460)

Cool, we found the password for the next level



# Level 7

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2f3c4572-4128-47cc-857d-d5c4cba090f9)

Navigating to the webpage and using the password we got from the previous level

username:```natas7```          password:```jmxSiH3SP6Sonf8dv66ng8v1cIEdjXWr```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1e0fd5cf-de9a-40e8-b6c6-9e4afe847a8c)

Viewing the page source;

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/50880754-c635-44cf-bf38-88d2b9ade22d)

We got a hint saying the password for the next level is in ```etc/natas_webpass/natas8```

Going back to the webpage and clicking on ```Home```,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/aae0a694-6f55-4a0a-9c87-0cf3b93bf9e2)

From the url we can tell that there's a possible LFI (Local File Inclusion) vulnerability, which can enable us to read files.

Lets try to read the ```/etc/passwd``` file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/963582a6-bd83-45f4-a2c4-b5ffae665de9)

cool stuff😎

Now, using the hint they gave us earlier, lets get the  password for the next level

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7765c1c9-9a77-42da-8c42-9bf1998ab648)

Nice, we got the password for the next level



# Level 8

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e48f580b-f5cc-440b-8ddd-153c0090fc1d)

Navigating to the webpage and using the password we got from the previous level

username:```natas8```          password:```a6bZCNYwdKqN5cGP11ZdtPg0iImQQhAB```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/da44f7dc-dd4b-4b3c-9ede-b4ce3f3fd07d)

Viewing the source page I got this php code

```php
<?

$encodedSecret = "3d3d516343746d4d6d6c315669563362";

function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}

if(array_key_exists("submit", $_POST)) {
    if(encodeSecret($_POST['secret']) == $encodedSecret) {
    print "Access granted. The password for natas9 is <censored>";
    } else {
    print "Wrong secret";
    }
}
?>
```
Explaining the code
```
1. The encoded secret is stored in the variable $encodedSecret. It is a hexadecimal representation of the original secret.
2. The function encodeSecret($secret) is defined. This function takes a secret as input, performs three operations on it, and returns the result.
   a. The secret is base64 encoded using base64_encode($secret).
   b. The resulting base64 string is reversed using strrev().
   c. The reversed string is converted to its hexadecimal representation using bin2hex().
3. The code checks whether the form has been submitted (array_key_exists("submit", $_POST)). It assumes that there is an HTML form with an input field named "secret" and a submit button.
4. If the form has been submitted, the code compares the encoded secret generated from the submitted secret with the original encoded secret (encodeSecret($_POST['secret']) == $encodedSecret).
5. If the comparison is true, it prints the message "Access granted. The password for natas9 is <censored>," where <censored> indicates that the password is intentionally hidden.
6. If the comparison is false, it prints the message "Wrong secret."
```
Taking the encodedsecret ```3d3d516343746d4d6d6c315669563362```, since it is hex encoded, lets decode it using [cyberchef](https://gchq.github.io/CyberChef/)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/19a19f4b-dcd1-47c0-b03c-413e4cf5a7c9)

Now, we'll try to use the ```strrev()``` function to reverse the base64 we got. For this we'll use a python script

```python
import base64

def reverse_base64(encoded_base64):

    # Step 1: Reverse the decoded bytes
    reversed_bytes = encoded_base64[::-1]

    # Step 2: Decode the Base64 string
    decoded_bytes = base64.b64decode(reversed_bytes)

    # Step 3: Encode the reversed bytes back to Base64
    reversed_base64 = base64.b64encode(decoded_bytes).decode()

    return reversed_base64

# Example usage
encoded_base64 = "==QcCtmMml1ViV3b"
reversed_base64 = reverse_base64(encoded_base64)
print(reversed_base64)
```
After running the script, you should get this

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/over_the_wire]
└─$ python abeg.py
b3ViV1lmMmtCcQ==
```
Now, lets go ahead and decode this base64

command:```echo "b3ViV1lmMmtCcQ==" | base64 -d```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/over_the_wire]
└─$ echo "b3ViV1lmMmtCcQ==" | base64 -d
oubWYf2kBq
```
Applying the output we got as the secret, that is ```oubWYf2kBq```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1aacba88-da8a-4f30-874d-74db1c62769f)

Cool, we got the password for the next level







    























  

