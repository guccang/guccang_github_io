title: Python3.x和Python2.x差别
date: 2015-09-06 14:25:59
tags:
- python
- django
------
## 区别

1.  print
    3.x: print(info) 必须带()
    2.x: print info  可要可不要()
    
2.  类别名
    3.x: 
        def __str__(self):
            pass
    2.x:
        def __unicode__(self):
            pass
          
3.  字符集
    3.x: 默认unicode, py文件格式为utf-8格式即可
    2.x: ansic默认，中文需要 u'中文' 形式来实现。并且在py文件中显示声明 utf-8