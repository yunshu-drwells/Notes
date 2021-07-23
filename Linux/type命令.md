<font size = 4 face = "黑体">


#### 先看一个type的例子

使用 type 命令可以查看该命令是内建命令还是外部命令

    type cd

得到cd是一个内建命令
> cd is a shell builtin 


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404122221775.png)

    help cd
    
得到cd的帮助文档
> cd: cd [-L|[-P [-e]]] [dir]...


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404122249815.png)


---


    type mv

得到mv是一个外部命令(root用户下)
> mv is aliased to `mv -i'


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404122153397.png)

得到mv是一个外部命令(普通用户下)
> -bash: help: no help topics match `mv'.  Try `help help' or `man -k mv' or `info mv'.

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404131910646.png)


    help mv
    
无法通过help命令获得mv的帮助文档

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404132140876.png)


---

    help help
    
查看help命令的帮助文档

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404132330873.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)

Display information about builtin commands(显示有关内置命令的信息)

Displays brief summaries of builtin commands(显示内置命令的简要摘要)


结论：type 命令可以查看该命令是内建命令还是外部命令，只有内建命令能够使用help 命令查询帮助文档


#### 语法规则

    type [options]name


options:afptP


-a	display all locations containing an executable named NAME;includes aliases, builtins, and functions, if and only if	the `-p' option is not also used

-f	suppress shell function lookup

-P	force a PATH search for each NAME, even if it is an alias,builtin, or function, and returns the name of the disk filethat would be executed

-p	returns either the name of the disk file that would be executed,or nothing if `type -t NAME' would not return `file'.

-t	output a single word which is one of `alias', `keyword',`function', `builtin', `file' or `', if NAME is an alias, shellreserved word, shell function, shell builtin, disk file, or not found, respectively

#### 实例

1.判断一个名字当前是否是alias、keyword、function、<a href="">builtin</a>、file或者什么都不是：

- type ls 的输出是 ls 是 `ls --color=tty' 的别名

- type if 的输出是 if 是 shell 关键字(keyword)

- type type 的输出是 type 是 shell 内嵌(builtin)

- type frydsh 的输出是 bash: type: frydsh: 未找到(not found)

- type mv 



2.判断一个名字当前是否是alias、keyword、function、builtin、file或者什么都不是的另一种方法（适用于脚本编程）：

- type -t ls 的输出是 alias
 
- type -t if 的输出是 keyword
 
- type -t type 的输出是 builtin
 
- type -t gedit 的输出是 file
 
- type -t frydsh 没有输出

3.显示一个名字的所有可能：

- type -a kill 的输出是 kill 是 shell 内嵌 和 kill 是 /bin/kill

- type -at kill 的输出是 builtin 和 file

4.查看一个命令的执行路径（如果它是外部命令的话）：

- type -p gedit 的输出是 /usr/bin/gedit

- type -p kill 没有输出（因为kill是内置命令）

5.强制搜索外部命令：

- type -P kill 的输出是 /bin/kill



</font>