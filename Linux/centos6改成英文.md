<font size = 4 face = "黑体">

### 使用locale查看当前使用的编码和字符集

    local

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404111517132.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)


### 使用locale -a查看当前支持的编码和字符集

    locale -a | grep en_US  
    
> locale -a会输出当前系统支持的所有编码和字符集，这里使用grep只过滤en_US的字符集

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404111755494.png)



### 在/etc/profile中修改LANG变量

#### 首先切换到root用户不然/etc/profile只可读

    su root

#### etc在根目录下，cd ../一直到根目录/

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404111931839.png)

#### 修改

    vi /etc/profile
    
#### 在/etc/profile最后追加


echo 'export LANG=en_US.UTF-8' >> /etc/profile
reboot

</font>