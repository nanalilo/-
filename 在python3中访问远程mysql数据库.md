# -在python3中访问远程mysql数据库

import pymysql
db = pymysql.connect("172.16.149.129","root","","TESTDB")
cursor = db.cursor()
cursor.execute("select version()")
data = cursor.fetchone()
print(data)
cursor.execute("select * from employee")
data = cursor.fetchone()
print(data)
