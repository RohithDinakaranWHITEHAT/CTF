![image](https://github.com/user-attachments/assets/34bf7a0e-f5ca-4186-a30e-d3e8242ab1f0)

Seems like they filter the input now. 
lets look at the source code.
![image](https://github.com/user-attachments/assets/529611ca-5ff6-4952-91ab-681af1907f74)

Seems like they filter ";" and also other command separators.


Looking at the source code, we know that our input is going to be placed inside the grep command.

so we have to manipulate the grep command to get the password.

. /etc/natas_webpass/natas11 #

this should work.

. means all,
/etc/natas_webpass/natas11 is the file location.
#- is to comment the rest of the command
![image](https://github.com/user-attachments/assets/719b6be3-5a1a-4160-a684-da9d5ad1aa1a)
