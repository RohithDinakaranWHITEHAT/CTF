![image](https://github.com/user-attachments/assets/5b49f40d-98f1-40cb-afaf-949fc0bc8843)

![image](https://github.com/user-attachments/assets/bc3e740d-aadd-4eb2-9c5a-f6a2ae8f2eca)

Lets check the source code.

![image](https://github.com/user-attachments/assets/d6031b4e-ebd5-4644-b119-6da58ba8f2c2)

here is my understanding of the code.

It first creates an array, something like this : {"showpassword":"no","bgcolor":"#ffffff"}.

Converts the array into JSON

Encrypts it with XOR using a secret key

Base64-encodes the result

Sets it as a cookie named data.

The server reads your data cookie

It:

Base64-decodes it

Decrypts it using XOR

Parses it back to JSON

Then it checks:

if ($data["showpassword"] == "yes")

**The goal is to:

Take the original JSON:
{"showpassword":"no","bgcolor":"#ffffff"}

Modify it to:
{"showpassword":"yes","bgcolor":"#ffffff"}

Re-encrypt it with the same XOR key

Base64-encode it

Set it as your new data cookie**



For this level we need cookie editor to get the data cookie.


![image](https://github.com/user-attachments/assets/91a4a531-9b36-4190-a3d8-62006bdbab30)

HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg%3D

%3D is the url encoded version of =, so our cookie will be:
HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg=


Now we have to find the key that is used in xor operation. 
we know xor is reversible. we have the plain text, cipher text, and by xor-ing the two we'll get the key.

HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg= is the cipher text.

to get the plain test, i wrote a python script.


![image](https://github.com/user-attachments/assets/70a95884-4eb3-4328-b85e-b9f6d55e3c87)


import base64
import json

default_data = {
    "showpassword": "no",
    "bgcolor": "#ffffff"
}

# Convert to JSON
json_str = json.dumps(default_data)

# Encode in Base64
encoded = base64.b64encode(json_str.encode()).decode()

print(encoded)

now its time for cyberchef.

![image](https://github.com/user-attachments/assets/49758d17-b003-4a37-b331-aec2d2409a4e)


put the plain text that we got from the python script at the key's place.
eDWoeDWoeDWoeDWogV"kJ*dLXo{	o|*eDW+~
we got this. 
it doesn't seem like a key. But iam guessing that eDWo is the key here. and its just repeating at again and again.

now put eDWo in the key's place to check if that's the actual key.

![image](https://github.com/user-attachments/assets/425cf3c1-5273-434a-aae7-172008633eed)

yes! it is. Now we got the key, that is used for xor operation.

![image](https://github.com/user-attachments/assets/f65b7135-4840-41c0-8758-f9d1d7549a20)


![image](https://github.com/user-attachments/assets/9757065b-6ae6-4bd7-a176-7d4c259eedbd)

Put the new found cookie in place, and that's it.





