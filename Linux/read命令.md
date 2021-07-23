<font size = 4 face = "黑体">




### read

read 是 Shell 内置命令，用来从标准输入中读取数据并赋值给变量。如果没有进行重定向，默认就是从键盘读取用户输入的数据；如果进行了重定向，那么可以从文件中读取数据。

#### read 命令的用法


read [-options] [variables]

options表示选项，如下表所示；variables表示用来存储数据的变量，可以有一个，也可以有多个。

<font color="FF0000">options和variables都是可选的，如果没有提供变量名，那么读取的数据将存放到环境变量 REPLY 中。</font>


**Shell read 命令支持的选项**
|选项	|说明|
|:--|:--|
|-a array	|把读取的数据赋值给数组 array，从下标 0 开始。
|-d delimiter	|用字符串 delimiter 指定读取结束的位置，而不是一个换行符（读取到的数据不包括 delimiter）。
|-e	|在获取用户输入的时候，对功能键进行编码转换，不会直接显式功能键对应的字符。
|-n num	|读取 num 个字符，而不是整行字符。
|-p prompt	|显示提示信息，提示内容为 prompt。
|-r	|原样读取（Raw mode），不把反斜杠字符解释为转义字符。
|-s	|静默模式（Silent mode），不会在屏幕上显示输入的字符。当输入密码和其它确认信息的时候，这是很有必要的。
|-t seconds	|设置超时时间，单位为秒。如果用户没有在指定时间内输入完成，那么 read 将会返回一个非 0 的退出状态，表示读取失败。
|-u fd	|使用文件描述符 fd 作为输入源，而不是标准输入，类似于重定向。

#### 实例

##### 使用 read 命令给多个变量赋值并输出


    #!/bin/bash
    
    
    read -p "Enter some information > " name url age
    
    echo "网站名字：$name"
    echo "网址：$url"
    echo "年龄：$age"


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210403195819854.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)


> 注意，必须在一行内输入所有的值，不能换行，否则只能给第一个变量赋值，后续变量都会赋值失败


##### 只读取一个字符

使用-p选项，该选项会用一段文本来提示用户输入

-n 1表示只读取一个字符，运行脚本后，只要用户输入一个字符，立即读取结束，不用等待用户按下回车键


    #!/bin/bash
    
    
    read -n 1 -p "Enter a char > " char 
    
    echo $char

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210403200233149.png)


##### 在指定时间内输入密码

使用&&组合了多个命令，这些命令会依次执行，并且从整体上作为 if 语句的判断条件，只要其中一个命令执行失败（退出状态为非 0 值），整个判断条件就失败了，后续的命令也就没有必要执行了

    
    #!/bin/bash
    
    
    if
        read -t 20 -sp "Enter password in 20 seconds(once) > " pass1 && printf "\n" &&  #第一次输入密码
        read -t 20 -sp "Enter password in 20 seconds(again)> " pass2 && printf "\n" &&  #第二次输入密码
        [ $pass1 == $pass2 ]  #判断两次输入的密码是否相等
    then
        echo "Valid password"
    else
        echo "Invalid password"
    fi


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210403200605238.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)



</font>