<font size = 4 face = "黑体">

### 查看Block 的大小

    sudo dumpe2fs /dev/sda1 | grep "Block size:"

的时候遇到如下错误：

xxx is not in the sudoers file. This incident will be reported

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210422091511642.png)


### 原因

xxx是当前的用户名,原因是用户没有加入到sudo的配置文件里

### 解决办法


#### 1.切换到root用户，运行visudo命令

    visudu


#### 2.在打开的配置文件中增加内容

在
    
    root ALL=(ALL) ALL

下面添加一行

    xxx ALL=(ALL) ALL 

> 其中xxx是你要加入的用户名称


### 在执行查看Block 的大小就可以了

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210422091411187.png)





</font>