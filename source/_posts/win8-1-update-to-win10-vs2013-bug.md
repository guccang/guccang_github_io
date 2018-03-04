title: 'win8.1 update to win10,vs2013 bug'
date: 2015-07-30 10:51:47
tags:
- visual studio
- all
---

***
***

1.  windows8.1更新到windows10后
    vs2013bug无法创建项目，已有项目无法编译。提示如下错误。
        未找到与约束ContractName Microsoft.VisualStudio.Text.ITextDocumentFactoryService...匹配的导出。
    ![图1](\imgs\vs2013Error\vs2013Error01.png)
2.  AppData\Roaming\Microsoft\VisualStudio\12.0\ActivityLog.xml相关错误。
    ![图2](\imgs\vs2013Error\vs2013Error02.png)

3.  解决办法:删除ComponentModelCache文件夹内所有文件。
        Remove ComponentModelCache folder content.
        %AppData%\..\Local\Microsoft\VisualStudio\12.0\ComponentModelCache
