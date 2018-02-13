title: django
date: 2015-08-12 14:35:25
tags:
- django
---

***
##使用django开发游戏web管理后台
   为什么需要这个web后台：运行时修改游戏服务器内容。比如活动开启,黑名单。。。
   在修改服务器数据时，做一些输入的限制性操作。即使你在地铁上也能够通过手机
   随时了解服务器的运行状况。
   使用方式：web后台修改mysql数据后，通知GameServer重新载入mysql配置文件。
   web后台在GameServer运行期间，增加，删除，修改GameServer中的数据。

***              
***

  * 环境搭建。 
    apache2.4
    Django1.8
    python3.3.3
    mod_wsgi.so模块，
    mysql
  * Django admin与GameServer服务器交互，http协议实现交互
  * Django 与mysql交互，Django自带admin管理（增删改）
  * 使用Django的template进行交互UI展示（特定交互UI实现）
  * 部署相关
 
***

###完成后看上去像是这样子
1.  webUI后台,login，logout，config，userinfo，restore(从mysql回滚数据到GameServer)
    是webUI和GameServer交互的入口，根据需求任意增加
    
    ![图片](\imgs\django\django-01.png)

2.  django的admin后台，用来操作mysql数据库

    ![图片](\imgs\django\django-02.png)
    ![图片](\imgs\django\django-03.png)

***

##Django和GameServer之间的交互
* 使用http协议，与GameServer之间进行数据交互。
* python的相关教程。Python3.x与python2.x差异,在使用过程中可以体会得到
  [python教程](http://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000)
    
***

##Django和MySql之间的交互
* Django自带的admin模块，提供了非常好的交互UI,对mysql数据库的增删改查，支持很容易使用
* Django相关教程
  [官方,非常详细的教程](https://docs.djangoproject.com/en/1.8/)
  [可以了解Django的运作机制](http://www.ziqiangxuetang.com/django/django-tutorial.html)

***

##代码路径
1.  scut框架 
https://github.com/guccang/Scut 
从scutgame官方fork过来的代码，用于更新scutgame框架错误
2.  服务器逻辑代码服务器逻辑代码 
https://github.com/guccang/scutlogic 
服务器逻辑代码，写的action逻辑
3.  webUI
https://github.com/guccang/django-GM-tools.git

***
##环境搭建

1.  apache/django/python版本选择问题
    * apache部署的时候需要用到，生产环境的mod_wsgi.so
      因此需要根据mod_wsgi.so的支持来选择apache和python的版本。
    
    * apache2.4 下载的地址：官方网站只提供了源码下载，不提供二进制安装文件。
      以下是apache官方推荐的下载地址之一，也是wsgi官方链接推荐的下载地址。
      http://www.apachelounge.com/download/
      copy xxxx.whl 到 apache2.4 modual目录下
      配置apache2.4各种目录
    
    * apache2.4对应的运行环境下载的地址：使用vc2015编译的apache2.4，需要安装对应的运行时vs环境
      http://www.microsoft.com/en-us/download/details.aspx?id=48145
    
    * apache2.4上述路径下载玩apache后。是一个包含所有apache组建的文件夹。然后需要安装apache服务
      到windows中区。
      进入apache bin目录。httpd -k install
    
2.  * mod_wsgi官方网址：http://www.modwsgi.org/
    找到mod_wsgi.so的windows下载的地址现在(2015/8/13)是：
    http://www.lfd.uci.edu/~gohlke/pythonlibs/#mod_wsgi
    找得到如下whl文件下载地址：
    mod_wsgi-4.4.13+ap24vc10-cp33-none-win_amd64.whl
    mod_wsgi-4.4.13+ap24vc10-cp33-none-win32.whl
    ap24=apache2.4
    cp33=python3.3.x
    win_amd64=windows os 64 
    win32=windows os 32
    
    * 根据自己的环境找到对应的whl文件。
    目前win64的只找到了python3的版本，没有python2.7。
    因此python版本选择为3.3.32
    apache选择apache2.4
    pc是windows10,64位，选则win_amd64.whl
    最后选择结果:mod_wsgi-4.4.13+ap24vc10-cp33-none-win_amd64.whl
    
    * whl文件。
    使用pip 安装whl文件
    pip install whl完整路径
    会将mod_wsgi.so文件下载下来。
    mod_wsgi.so下载的地址：
    http://www.modwsgi.org/
    http://www.lfd.uci.edu/~gohlke/pythonlibs/#mod_wsgi
    pip install xxxx.whl

3.  python下载的地址：
    * https://www.python.org/downloads/
    pip 工具下载地址：
    https://pypi.python.org/pypi/pip#downloads
    python setup.py install 
    
4.  django 安装
    pip install django
    
5.  mysqldb安装
    http://www.lfd.uci.edu/~gohlke/pythonlibs/#mysqlclient
    
####至此搭建环境所需的所有东西都齐全了。apache2.4 python3.3.3 
   
***
##部署问题

1.  apache + wsgi + django
    apache配置wsgi相关
    apache配置django静态文件路径
    django配置静态文件搜集路径

    *无法载入css，img，js相关静态文件问题：
    *apache配置 config
        LoadModule wsgi_module modules/mod_wsgi.so
        WSGIScriptAlias / C:/Python33/src/mysite/mysite/wsgi.py
        WSGIPythonPath C:/Python33/src/mysite
        <Directory C:/Python33/src/mysite/mysite>
        <Files wsgi.py>
            Require all granted
            Require ip 127.0.0.1
        </Files>
        </Directory>

    *这个目录是django 配置的静待资源根目录。
    *有这个后，再加上django配置，就可以顺利的找到css，img，js相关文件。
        Alias /static/ C:/Python33/src/mysite/mysite/static/
        <Directory C:/Python33/src/mysite/mysite/static/>
            Require all granted
        </Directory>

2.  setting配置
    django部署后，css、js、图片都无法显示。
    setting.py 设置：
        STATIC_URL = '/static/'
        STATIC_ROOT = 'c:/Python33/src/mysite/mysite/static/'
    其他不变即可。
    运行 python manage.py collectstatic 
    将app的static文件夹下的所有资源放到STATIC_ROOT之下

3.  数据库修改后同步
    数据表重建：数据库模型修改后同步给开发服务器。
    数据库model和view、template不同,修改后无法及时同步。
    python makemigrations
    python migrate

    数据表导出,将连接的数据库的所有表导出到models_all.py文件中
    python manage.py inspectdb > models_all.py 

4.  运行时网站反应速度慢
    使用apache自带的工具启动apache服务。
      
5.  BUG
    * 1264 - Out of range value adjusted for column 'ID' at row 1  
      byte类型  mysql tinyint 有符号
      mysql默认有符号,应该改为无符号。
    * 将apache bin的目录弄错了。导致httpd.cfg 读取别的,修改无用
    * 
    