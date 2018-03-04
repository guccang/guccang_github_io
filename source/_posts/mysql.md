title: mysql
date: 2015-09-23 16:06:06
tags:
- mysql
- all
---
>> ##mysql

***

###1.0 mysql 停止启动
 * net stop mysql
   net start mysql

###2.0 mysql设置时区
 * 查看时区
   show variables like '%time_zone%'; 
   
 * 设置时区
    set time_zone = '+8:00'
    select now() 

###3.0 权限相关
 * 查看正在使用的用户名
 select user()
 
 * 查看用户权限
 show grants for 用户名
 
 * 修改用户权限
 mysql> GRANT <privileges> ON <what> #权限 & 数据库.表
 -> TO <user> [IDENTIFIED BY "<password>"] #提升用户
 -> [WITH GRANT OPTION]; #可否授权

 GRANT select,index ON phdata.*
 TO game_user@'%' IDENTIFIED BY '123';
 
 * 修改用户密码
 use mysql;
 UPDATE user SET password=PASSWORD('123') WHERER user='game_user';
 FLUSH PRIVILEGES;
 mysql quit;
 执行1.停止mysql，重启mysql。
    
