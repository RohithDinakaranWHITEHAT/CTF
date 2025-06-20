![image](https://github.com/user-attachments/assets/5ac7f289-c4bc-4bac-a469-26387d0e08d1)

Looks like the level 6 challenge. lets look at the source code.

![image](https://github.com/user-attachments/assets/61b3b23b-d49c-4989-8385-a364aafde4e7)

Its similar to level 6, but here the actual secret is encoded and given to us.

bin2hex(strrev(base64_encode($secret))

I think we should do all this in reverse to get the key.


![image](https://github.com/user-attachments/assets/6307efe9-7d26-4bee-8303-a82c2598a2f5)

Thats our secret key.

![image](https://github.com/user-attachments/assets/9dd056f1-7f39-4701-9298-1b567fdda809)

Gotcha!
