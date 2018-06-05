# -
在Ubuntu上安装mysql


1. 下载并安装mysql

sudo apt-get update

sudo apt-get install mysql-server

会弹出提示，让输入root的密码，根据提示操作即可

目前（2018-2-24）的mysql版本是5.7.21

2. 配置mysql

mysql_sequre_installation

根据提示操作，此处会首先让你输入安装时创建的root密码，然后根据提示选择你需要的设置

3. 验证mysql工作状态

systemctl status mysql.service

可以查看状态，默认为开启状态。如果未开启，可使用 sudo systemctl start mysql来开启

进一步，可使用mysqladmin -p -u root version来测试连接
