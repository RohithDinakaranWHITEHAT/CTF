![image](https://github.com/user-attachments/assets/25bafcee-9435-49f5-a599-b618096ddc96)

![image](https://github.com/user-attachments/assets/58e78eea-605b-4281-a193-0c4d06e39ca4)

Looking at the code, i could see a potential for simple file upload vulnerability.

seems like there is no MIME type extension. 
so lets write a simple php shell and try uploading it.

![image](https://github.com/user-attachments/assets/9177e4c9-66da-4c41-a3cd-2cd9aab8a739)

![image](https://github.com/user-attachments/assets/1f09b8f2-8eba-4810-91a9-83e8e73e839c)

File is uploaded. But it is uploaded as jpg. we don't need that.
lets fire up the burp to find the issue.

![image](https://github.com/user-attachments/assets/1b3cdacd-1f04-4fb9-beea-8e39c409497e)

Content-Disposition: form-data; name="filename"

o5mvapaisr.jpg

Change this line to shell.php.
![image](https://github.com/user-attachments/assets/862f8ac1-426f-4ec7-a104-d0910d14d429)

Now the PHP file is uploaded as it is.

head over to http://natas12.natas.labs.overthewire.org/upload/7t5xnmct92.php?cmd=cat%20/etc/natas_webpass/natas13


![image](https://github.com/user-attachments/assets/effd8789-4eb9-432e-ad5c-a9120f7d85bf)

