# -在python3中访问远程mysql数据库

import pymysql
db = pymysql.connect(host="172.16.149.129",user="root",passwd="",db="TESTDB",port=3306,charset='utf8')
cursor = db.cursor()
cursor.execute("select version()")
data = cursor.fetchone()
print(data)
cursor.execute("select * from employee")
data = cursor.fetchone()
print(data)
