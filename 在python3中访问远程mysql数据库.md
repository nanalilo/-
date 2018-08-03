# -在python3中访问远程mysql数据库


先要安装pymysql组件：

sudo pip3 install pymysql

然后访问数据库的代码如下：

import pymysql
<br>
db = pymysql.connect(host="172.16.149.129",user="root",passwd="",db="TESTDB",port=3306,charset='utf8')
<br>
cursor = db.cursor()
<br>
cursor.execute("select version()")
<br>
data = cursor.fetchone()
<br>
print(data)
<br>
cursor.execute("select * from employee")
<br>
data = cursor.fetchone()
<br>
print(data)
<br>
