![image](https://github.com/user-attachments/assets/0dc2f9d9-3931-4658-9253-f625b3c9cc3d)

![image](https://github.com/user-attachments/assets/7645d550-3d35-4afe-8484-7738d9d5e2b5)

Looking at the code, this level looks like it is vulnerable to command injection.

What ever we enter will be ran by the server
grep -i $key dictionary.txt

so we now have to get the password from /etc/natas_webpass/natas10.
lets do cat.

; cat /etc/natas_webpass/natas10

I think this payload will work.


![image](https://github.com/user-attachments/assets/f1b761b9-8ab5-4934-af72-e5673f8b907d)

It does.

