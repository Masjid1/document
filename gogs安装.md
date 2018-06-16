
1. 解压到

		D:\Program\gogs

2. 在解压目录下以管理员权限运行

		gogs.exe web

3. 在浏览器中访问

		http://localhost:3000

4. 配置数据库和gogs的选项，完成后gogs会自动生成custom等目录。

5. 使用nssm将"gogs.exe web"设置成服务。

6. 为了使用域名gogs代替url(127.0.0.1),需要在hosts文件(C:\Windows\System32\drivers\etc)中添加如下一行：

		127.0.0.1:3000 gogs

7. 在cmd中执行**ipconfig /flushdns**，刷新dns, 使 hosts文件立即生效。
