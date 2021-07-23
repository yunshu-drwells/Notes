<font size = 4 face = "黑体">

##### pip安装python的dns包出错：Could not find a version that satisfies the requirement install (from versions: None) 

	pip install dns
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201224211718594.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)

##### 解决办法1更新pip

win+r 输入cmd回车进命令行输入以下命令确保成功
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020122421194558.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)

更新pip成功后

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201224212041117.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)
再输入pip install dns试试，如果不行尝试方法2

##### 解决办法2
继续在命令行操作在安装的包后面加python

	pip install dnspython
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020122421205870.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)
安装成功，发现pycharm已经可以成功引入dns包了
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020122421241238.png)



除了在windows的CMD中使用pip工具安装包外，在pycharm的Terminal中安装或者在pycharm的settings-project-Python Interpreter中也是一样的

###### Terminal


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210127111947229.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)

###### settings-project-Python Interpreter

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210127112021514.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)


</font>