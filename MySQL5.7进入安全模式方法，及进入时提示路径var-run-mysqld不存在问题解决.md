# -MySQL5.7进入安全模式方法，及进入时提示路径var-run-mysqld不存在问题解决

<br><br>
1.停止MySQL服务
<br>service msyql stop
<br>或者
<br>killall -TERM mysqld
<br>2.跳过安全检查启动mysql服务
<br>/usr/bin/mysqld_safe --skip-grant-tables &
<br>3.如执行没有出错，那么当前shell已经被mysql进程占用，如需进行其他操作，必须Ctrl+Alt+F2～F4，切换到其他控制台后进行（比如登录mysql修改密码）
<br><br>
如果启动服务时出现以下错误
<br>'/var/run/mysqld' for UNIX socket file don't exists
<br>解决的方法就是建立该文件夹并授权即可
<br>mkdir -p /var/run/mysqld
<br>chown mysql:mysql /var/run/mysqld
<br><br>在安全模式中做了修改后，别忘了重新加载权限表
<br>flush privileges;
