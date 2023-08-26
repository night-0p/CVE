The /sys/ui/sys_ui_extend/sysUiExtend.do route is defined in `WEB-INF/KmssConfig/sys/ui/spring-mvc.xml`
and is handled by com.landray.kmss.sys.ui.actions.SysUiExtendAction class
<img width="1098" alt="image" src="https://github.com/night-0p/anh/assets/54882616/59cec375-92e2-4e53-b905-640aa5dcbd07">
Tracked to the SysUiExtendAction class, after accepting the `id` parameter, use ../ to filter, but in the windows environment, you can use ..\ to bypass.
Any files specified including folders will eventually be downloaded as a tarball.
<img width="1111" alt="image" src="https://github.com/night-0p/anh/assets/54882616/71208c2a-8b35-4e9a-b986-b62c527c0774">
<img width="944" alt="image" src="https://github.com/night-0p/anh/assets/54882616/9c94785a-a156-40c9-8ced-7ec0280d33db">
<img width="1004" alt="image" src="https://github.com/night-0p/anh/assets/54882616/a3345f2a-52d2-41e5-b6d9-d15ecf1602d7">

Then we will get the following file:  
<img width="973" alt="image" src="https://github.com/night-0p/anh/assets/54882616/68e1f587-110a-4df6-8b9e-af3157db6544">
<img width="705" alt="image" src="https://github.com/night-0p/anh/assets/54882616/6059dd28-ae4d-494c-a40e-3946ace8d3c6">


