![image](https://github.com/user-attachments/assets/62552eef-55fd-4115-b9f9-6922b137a85b)

This code uses custom session storage using a file-based method with mysess_<sid> filenames.
So sessions are stored in 
/tmp/mysess_<session_id>

inside the file, data is saved as:

name filename
admin 0

so we have to find a way to create a session file with:
name admin
admin 1


Payload that'll work is : %0Aadmin 1

send the request in repeater and send this for couple of times till you get the password.

