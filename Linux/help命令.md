<font size = 4 face = "黑体">


### 语法

    help [option] <command>



#### 先看一个type的例子

使用 type 命令可以查看该命令是内建命令还是外部命令

    type cd

得到cd是一个内建命令
> cd is a shell builtin 


    type mv


得到mv是一个外部命令(普通用户下)
> -bash: help: no help topics match `mv'.  Try `help help' or `man -k mv' or `info mv'.

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404131910646.png)


---




![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404122221775.png)

    help cd
    
得到cd的帮助文档
> cd: cd [-L|[-P [-e]]] [dir]...


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404122249815.png)


    help mv
    
无法通过help命令获得mv的帮助文档

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404132140876.png)



---

    help help
    
查看help命令的帮助文档

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404132330873.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)

Display information about builtin commands(显示有关内置命令的信息)

Displays brief summaries of builtin commands(显示内置命令的简要摘要)


**结论：只有内建命令能够使用help命令查询帮助文档**







</font>