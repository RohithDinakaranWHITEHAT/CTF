Capture the request.
this level has a login form, which works as a register form as well.
if the given username is not already present it will create a new user.
And looking at the source code, we can see that, the username is truncated with a function.

So that will be our way for exploiting the website.
intercept the request,
add natas28 as the username and append null characters(more than 64) and also add any valid character (just for validation that truncation part is working).
![image](https://github.com/user-attachments/assets/0a764db3-8612-4644-a8bc-5b1af9d70a70)

now remove the null characters ans send the same request.
you will be logged in as natas28.
![image](https://github.com/user-attachments/assets/2e0b57d2-7232-4a50-993b-a6be9b879462)
