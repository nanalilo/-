# -MySQL数据库改名（脚本bash）


#! /bin/bash

# 假设将TESTDB数据库名改为testdb
# MyISAM直接更改数据库目录下的文件即可

mysql -h 172.16.149.129 -u root -p -e 'create database if not exists testdb'
list_table=$(mysql -h 172.16.149.129 -u root -p -Nse "select table_name from information_schema.TABLES where TABLE_SCHEMA='TESTDB'")

for table in $list_table
do
    mysql -h 172.16.149.129 -u root -p -e "rename table TESTDB.$table to testdb.$table"
done
