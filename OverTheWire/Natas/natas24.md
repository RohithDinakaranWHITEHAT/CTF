![image](https://github.com/user-attachments/assets/db15b619-4f6a-4a67-b50e-0c2340fe5f43)


The function used is: strcmp($a, $b)

!strcmp($_REQUEST["passwd"], "<censored>")

That means:
→ If the input is equal to <censored>, show credentials.

This normally looks secure — BUT strcmp() expects a string — and it will return NULL (or raise a warning) if passed a non-string (like an array). However, !strcmp(array, string) will evaluate to true because strcmp(array, string) returns false, and !false == true.

http://natas24.natas.labs.overthewire.org/?passwd[]=1

That will make $_REQUEST["passwd"] an array instead of a string. strcmp(array, string) will fail, and negation ! turns the result into true.

![image](https://github.com/user-attachments/assets/fb35a59d-e0ab-427e-a4d7-7d8343157154)
