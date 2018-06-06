# -ubuntu server 18.04 卸载 mysql

首先用dpkg --list|grep mysql查看自己的mysql有哪些依赖
\

先卸载sudo apt-get remove mysql-common

然后：sudo apt-get autoremove --purge mysql-server-5.0

再用dpkg --list|grep mysql查看，还剩什么就卸载什么

最后清楚残留数据：

dpkg -l |grep ^rc|awk '{print $2}' |sudo xargs dpkg -P
