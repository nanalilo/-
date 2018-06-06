# -MySQL5.7更改密码，及解决远程1698错误.
MySQL5.7更改密码，及解决远程1698错误.

1.终端输入mysql直接登录
 mysql
2.切换到mysql数据库
 use mysql
3.建议采用命令方式更改密码，密码须由至少一个大、小写字母、符号、数字组成
 alter user 'root'@'localhost' idendified by 'newPwd';
  也可采用语句来直接操作数据库表
 update mysql.user set authentication_string=PASSWORD('newPwd'),plugin='mysql_native_password' where user='root';
4.要解决远程登录的问题，需要更改root用户的plugin字段
  用密码登陆的plugin应该是mysql_native_password
 update mysql.user set plugin = 'mysql_native_password' where user = 'root'
5.注意还应修改/etc/mysql/mysql.conf.d/mysqld.cnf文件，将其中的绑定地址行注释掉
 #bind-address = 127.0.0.1
6.重新启动mysql服务即可使用远程登录
 service mysql restart
