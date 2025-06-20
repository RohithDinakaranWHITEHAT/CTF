![image](https://github.com/user-attachments/assets/53ffe62e-f5e2-4013-bb69-d62b7e1a1535)

Seems like a input injection, something like sqli, htmli, xss.

Lets take a look at the source code.

![image](https://github.com/user-attachments/assets/4283fff7-3ff5-4ec8-bfa8-521e6035db04)


Alright, we see a JS code that checks whether the given input matches the Secret value. Lets see if we can access the secret.inc


http://natas6.natas.labs.overthewire.org/includes/secret.inc


![image](https://github.com/user-attachments/assets/c611ae7a-39ae-46ba-8265-f4a17ce423eb)

we get an empty page as the result. look at the source code.
![image](https://github.com/user-attachments/assets/e85b0497-6f1c-493c-ab1a-8862db1ce13f)

we got the secret, now we jus have to paste this in the input field.

![image](https://github.com/user-attachments/assets/77b005db-2ce4-4de8-8736-7780339bb211)

Gotcha!!
