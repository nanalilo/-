# -MySQL5.7更改密码，及解决远程1698错误.
MySQL5.7更改密码，及解决远程1698错误.
<br><br>
1.终端输入mysql直接登录<br>
 mysql<br>
2.切换到mysql数据库<br>
 use mysql<br>
3.建议采用命令方式更改密码，密码须由至少一个大、小写字母、符号、数字组成<br>
 alter user 'root'@'localhost' idendified by 'newPwd';<br>
  也可采用语句来直接操作数据库表<br>
  (<b>特别注意！！一定不要忘记对密码字符应用password函数进行运算，否则会发现改完密码后无法登录了</b>)<br>
 update mysql.user set authentication_string=PASSWORD('newPwd'),plugin='mysql_native_password' where user='root';<br>
4.要解决远程登录的问题，需要更改root用户的plugin字段<br>
  用密码登陆的plugin应该是mysql_native_password<br>
 update mysql.user set plugin = 'mysql_native_password' where user = 'root'<br>
5.注意还应修改/etc/mysql/mysql.conf.d/mysqld.cnf文件，将其中的绑定地址行注释掉<br>
 #bind-address = 127.0.0.1<br>
6.重新启动mysql服务即可使用远程登录<br>
 service mysql restart<br>
