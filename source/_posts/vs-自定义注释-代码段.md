title: vs 自定义注释/代码段
date: 2015-07-28 11:35:10
tags: 
- tools
- visual studio
- all
---

***
***

1.  代码段管理：
    创建一个snippet文件，导入到vs中。键入自定义字符后，tab键两次，自动生成注释/代码段。
    snippet是讲一个key 与一段字符关联(可以使注释，可以是代码)
    如~~vs中输入tryf，两次tab后直接输出
```bash
try 
{	        		    
}
finally
{
}
```

2.  自定义文件注释模板
    vs中输入guccangFC ,tab键2次，自动生成如下注释。
```bash
/****************************************************************************
    File:		AutoTest.cs
    Desc:		Automated testing
    Date:		2015-7-27
    Author:		guccang
    URL:		http://guccang.github.io
    Email:		guccang@126.com
****************************************************************************/
```

3.  对应的snippet文件

```bash
<?xml version="1.0" encoding="utf-8"?>

<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">

  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>FileComment</Title>
      <Shortcut>guccangFC</Shortcut>
      <Description>FileComment 语句的代码段</Description>
      <Author>guccang</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
        <SnippetType>SurroundsWith</SnippetType>
      </SnippetTypes>
    </Header>
	
    <Snippet>
      <Declarations>
	    <Literal>
          <ID>Name</ID>
          <ToolTip>文件名</ToolTip>
          <Default>fileName</Default>
        </Literal>
		
        <Literal>
          <ID>License</ID>
          <ToolTip>授权</ToolTip>
          <Default>MIT</Default>
        </Literal>

        <Literal>
          <ID>Author</ID>
          <ToolTip>作者</ToolTip>
          <Default>guccang</Default>
        </Literal>

        <Literal>
          <ID>Date</ID>
          <ToolTip>日期</ToolTip>
          <Default>2015-7-21 11:11:11</Default>
        </Literal>
		
		<Literal>
          <ID>Desc</ID>
          <ToolTip>描述</ToolTip>
          <Default>添加文件描述</Default>
        </Literal>
		
		<Literal>
          <ID>URL</ID>
          <ToolTip>url</ToolTip>
          <Default>http://guccang.github.io</Default>
        </Literal>

		<Literal>
          <ID>Email</ID>
          <ToolTip>Email</ToolTip>
          <Default>guccang@126.com</Default>
        </Literal>
		

      </Declarations>

      <Code Language="csharp">
        <![CDATA[
		/****************************************************************************
			File:		$Name$
			Desc:		$Desc$
			Date:		$Date$
			Author:		$Author$
			URL:		$URL$
			Email:		$Email$
	    ****************************************************************************/
		$selected$ $end$]]>
      </Code>

    </Snippet>
  </CodeSnippet>
</CodeSnippets>

```
4.  将上述文件保存为fileComment.snippet , snippet文件扩展名
    打开vs导入snippet文件。
    vs-工具-代码段管理
    ![图片](\imgs\snippet.png)

5.  参考资料
    [官方]https://msdn.microsoft.com/zh-cn/library/ms165394(v=vs.120).aspx
    [博客01](http://blog.csdn.net/oyi319/article/details/5605502)
    [博客02](http://jingyan.baidu.com/article/ea24bc39b86ededa62b3311f.html)
    [博客03](http://blog.csdn.net/nuaalfm/article/details/1772551)
