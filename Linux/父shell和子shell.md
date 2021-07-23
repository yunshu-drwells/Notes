<font size = 4 face = "黑体">












### 得到当前shell的进程号


执行

    echo $BASHPID
    
或者

    echo $$

如果该值和父bash进程的pid值不同，则表示进入了子shell。



<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=50>









### 开启和关闭子shell


##### 首次进入bash

记录shell tree形状和当前shell的进程号

    pstree
    
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404140501985.png)
    
    
    echo $$
    
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404140513163.png)


##### 开启一个子bash

    bash
    
##### 记录开启一个子bash之后shell tree形状和当前shell的进程号
    
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404140628529.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404140644892.png)



##### 退出当前bash

    exit
    

##### 记录退出一个子bash之后shell tree形状和当前shell的进程号


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404141137783.png)


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404141147940.png)




<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=50>
















### 何时产生子shell

要解释清楚子shell以及产生何种类型的子shell，需要搞清楚Linux中如何产生子进程。Linux上创建子进程的方式有三种：一种是fork出来的进程，一种是exec出来的进程，一种是clone出来的进程(此处无需关心clone，因为它用来实现Linux中的线程)。

1.fork是复制进程，它会复制当前进程的副本(不考虑写时复制的模式)，以适当的方式将这些资源交给子进程。所以子进程掌握的资源和父进程是一样的，包括内存中的内容，所以也包括环境变量和变量。但父子进程是完全独立的，它们是一个程序的两个实例。

2.exec是加载另一个应用程序，替代当前运行的进程，也就是说在不创建新进程的情况下加载一个新程序。exec还有一个动作：在进程执行完毕后，退出exec所在的shell环境。



**为了保证进程安全，若要形成新的且独立的子进程，都会先fork一份当前进程，然后在fork出来的子进程上调用exec来加载新程序替代该子进程**

除了上面可以通过bash命令手动开启一个子shell；例如在bash下执行cp命令，会先fork出一个bash，然后再exec加载cp程序覆盖子bash进程变成cp进程。




#### 不进入子shell的情况：




###### 1.执行bash内置命令时

bash内置命令是非常特殊的，父进程不会创建子进程来执行这些命令，而是直接在当前bash环境中执行


    echo $BASHPID 
    
    let a=$BASHPID
    
    echo $a

> let是内置命令，不进入子shell



![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404203004982.png)




<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=20>


###### 2.执行shell函数时



其实shell函数就是命令，它和bash内置命令的情况一样，直接执行时不会进入子shell。


定义一个函数，输出BASHPID变量的值

    fun_test (){ echo $BASHPID; } 
    
得到当前BASHPID
    
    echo $BASHPID


执行函数

    fun_test 


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404162620528.png)

执行函数前后BASHPID相同说明没有进入子shell




<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=20>





###### 3.执行非bash内置命令时

例如执行cp命令、grep命令等，它们直接fork一份bash进程，然后使用exec加载程序替代该子bash。此类子进程会继承所有父bash的环境。但**严格地说，这已经不是子shell，因为exec加载的程序已经把子bash进程替换掉了，这意味着丢失了很多bash环境**。在bash文档中，直接称呼这种环境为"单独的环境"，和子shell的概念类似。


    echo $BASHPID
    
    expr $BASHPID

> cd是内置命令、expr是外部命令

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404171345371.png)

<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=20>











#### 进入子shell的情况：

###### 1.将命令放在管道后




如果将命令放在管道后，则此命令将和管道左边的进程同属于一个进程组，所以仍然会创建子shell。这时候的子shell的作用是为bash内置命令提供执行环境。


    echo "https://blog.csdn.net/qq_43808700?spm=1000.2115.3001.5343" | read
    
    echo $REPLY
    
    
    
> echo是内置命令、read也是内置命令
>
> 使用 read 读取数据时，如果没有提供变量名，那么读取到的数据将存放到环境变量REPLY中
>
> 使用管道操作符“|”可以把一个命令的标准输出传送到另一个命令的标准输入中，连续的|意味着第一个命令的输出为第二个命令的输入，第二个命令的输出为第三个命令的输入，依次类推...。

read内置命令位于管道后，read会在子shell中执行

echo命令在父Shell中执行，echo通过管道将内容输出到子进程中，管道可以用于父子进程之间通信，因此子shell可以拿到父shell输出的内容，因此子shell中read一定将拿到的内容保存在了环境变量REPLY中，而子进程的环境变量对父进程是不可见的，所以读取失败。


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404172748946.png)




    echo $BASHPID
    
    
    cd | expr $BASHPID 
    
    
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404203145994.png)



    echo $BASHPID
    
    
    ls | expr $BASHPID 


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404203433950.png)

> cd是内置命令，ls是非内置命令，<a href="expr命令">expr</a> ^[expr命令是一个手工命令行计数器，用于在UNIX/LINUX下求表达式变量的值，一般用于整数值，也可用于字符串。]也是非内置命令



结论：只要放在管道符之后的命令，则此命令将和管道左边的进程同属于一个进程组 ^[]，就会创建子shell，管道符右边的命令就会在子shell中运行



<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=20>


###### 2.执行bash命令本身时

bash命令本身是bash内置命令，在当前shell环境下执行内置命令本不会创建子shell，也就是说不会有独立的bash进程出现，而实际结果则表现为新的bash是一个子进程。其中一个原因是执行bash命令会加载各种环境配置项，为了父bash的环境得到保护而不被覆盖，所以应该让其以子shell的方式存在。虽然fork出来的bash子进程内容完全继承父shell，但因重新加载了环境配置项，所以子shell没有继承普通变量，更准确的说是覆盖了从父shell中继承的变量。

切换到root用户

    su root

在/etc/bashrc文件中定义一个变量

    echo "var=55" >>/etc/bashrc
    
    echo $var //55 只有文件中定义的变量

再在当前shell中export名称相同值却不同的环境变量

    export var=66
    
    echo $var //66 此时在当前shell中查看var的值就是66，加载变量的顺序是先环境变量再/etc/bashrc文件中的变量
    
    
> echo和export都是内置命令因此不会产生新的子shell


然后到子shell中看看该变量的值

    bash
    echo $var

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404150108664.png)



发现是55，虽然fork出来的bash子进程内容完全继承父shell，但因重新加载了环境配置项，所以子shell没有继承普通变量，更准确的说是覆盖了从父shell中继承的变量。


<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=10>


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404151606647.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)

BASH_SUBSHELL 是记录一个 Bash 进程实例中多个子Shell（subshell）嵌套深度的累加器。bash前后BASH_SUBSHELL的值都为0，可以认为没有进入子shell。

bash前后BASHPID的值不同可以认为算是进入了子shell。



结论：其实执行bash命令，既可以认为进入了子shell，也可以认为没有进入子shell。从bash是内置命令的角度来考虑，它不会进入子shell，这一点在执行bash命令后从变量$BASH_SUBSHELL的值为0可以验证出来。但从执行bash命令后进入了新的shell环境来看，它有其父bash进程，且$BASHPID值和父shell不同，所以它算是进入了子shell。



<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=20>







###### 3.执行shell脚本时



创建一个sh文件

    #!/bin/bash
    echo $BASHPID
    echo $SHLVL


> SHLVL是记录多个 Bash 进程实例嵌套深度的累加器

保存为test_bash.sh




获取当前BASHPID

    echo $BASHPID
    
执行test_bash.sh脚本文件

    sh -x test_bash.sh 
    
    
> 使用sh -x调试shell脚本，只需要文件所有者拥有可读权限就可以正常调试^[<img src="https://img-blog.csdnimg.cn/20210404161204991.png">]。或者切换到root用户修改文件权限，就可以./test_bash.sh执行
    
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404160351691.png)


发现一旦执行sh文件获取的BASHPID就发生了改变，说明产生了子shell
    
    
    
<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=10>
 


(如果想要./test_bash.sh运行，需要切换到root用户，<a href="查看更改文件权限">更改文件权限</a>
    

查看test_bash.sh权限

    ls -l | grep test_bash
    
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404153411920.png)


对所有者增加可执行权限（对test_bash.sh赋可执行的权限 chmod 731 test_bash.sh or chmod u+x  test_bash.sh）：

    chmod u+x test_bash.sh


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404155710205.png)


)

<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=20>







###### 4.执行shell函数时




其实shell函数放在管道后会进入子shell。


定义一个函数，输出BASHPID变量的值

    fun_test (){ echo $BASHPID; } 
    
得到当前BASHPID
    
    echo $BASHPID


放在管道后会执行

    cd | fun_test


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404162842184.png)


执行函数前后BASHPID不同说明进入子shell


<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=20>









###### 5.命令替换

当命令行中包含了命令替换部分时，将开启一个子shell先执行这部分内容，再将执行结果返回给当前命令。因为这次的子shell不是通过bash命令进入的子shell，所以它会继承父shell的所有变量内容。这也就解释了"echo $(echo &&)"中")"中"echo &&"的结果是当前bash的pid号，而不是子shell的pid号，但"echo $(echo $BASHPID)"却和父bash进程的pid不同，因为它不是使用bash命令进入的子shell。


    echo $BASHPID
    
    echo $ $$

    echo $(echo $BASHPID) 


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404164730576.png)



<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=20>












###### 6.使用括号()组合一系列命令

例如(ls;date;echo haha)，独立的括号将会开启一个子shell来执行括号内的命令。这种情况等同于执行非bash内置命令的情况。

    echo $BASHPID
    
    (echo $BASHPID)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404165038729.png)


使用括号()的命令组合进入子shell


<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=20>








###### 7.放入后台运行的任务

它不仅是一个独立的子进程，还是在子shell环境中运行的。例如"echo hahha &"。
    
    echo $BASHPID
    
    echo $BASHPID &  
    
    
> echo $BASHPID &  :放入后台运行的任务进入子shell


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404165154275.png)

<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=20>









###### 8.进程替换

既然是新进程了，当然进入子shell执行。例如"cat <(echo haha)"。


    echo $BASHPID
    
    cat <(echo $BASHPID) 

> cat <(echo $BASHPID) :进程替换"<()"进入子shell


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404165433383.png)



<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=20>





除了直接执行bash命令和shell脚本这两种子shell，其他进入子shell的情况都会继承父shell的值。前面也已经说了，其实shell脚本和直接执行bash命令开启子shell的方式是一样的，它们都不会继承父shell的值









<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=50>


### 查看shell树

    pstree
    
上半部分shell树

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021040413504788.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)

往下观察，就能看到我们刚执行的pstree命令开启了一个子shell

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404135152355.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)



连续exit两次并查看shell tree

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404135427793.png)

发现少了两个bash，结果与操作相符

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404135340225.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)


继续exit发现会退出shell,说明已经到父shell，再退出就会退出整个shell


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404135703242.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)










</font>