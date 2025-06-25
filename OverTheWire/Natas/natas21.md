![image](https://github.com/user-attachments/assets/7cd0cb8c-c943-49fb-af5a-b24e95e5dfb8)


in this level, there are two websites.
![image](https://github.com/user-attachments/assets/14f815b0-f814-4365-922c-4f0a8c1a45dc)
Both website have different source code.

looking at the source code we get the insight that we can set arbitrary session keys in the experimenter site

Now what does that mean?  it means that we can set admin=1 parameter in the request header of the experimenter site and we get the cookie of the experimenter site and paste it in the natas21 site to get the password.

we can use burp for it.

first, capture the request sent from experimenter site and add admin=1 to the parameter.
![image](https://github.com/user-attachments/assets/e423f4d5-9d9a-40e2-8ae3-147e7450a995)


copy the PHPSESSID of that request.

Now capture the request sent from the 1st site and replace the PHPSESSID with the one we copied earlier.

do this until you get the answer.
![image](https://github.com/user-attachments/assets/9a1e3cd1-70db-4176-93b4-8eaf0ef7bfad)


d8rwGBl0Xslg3b76uh3fEbSlnOUBlozz
