<font size = 4 face = "黑体">

### dumpe2fs查看Block 的大小出错

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210422092443199.png)


### 原因


tune2fs和dumpe2fs只能打开ext3/ext4等文件类型

    dumpe2fs - dump ext2/ext3/ext4 filesystem information
    　　
    tune2fs - adjust tunable filesystem parameters on ext2/ext3/ext4 filesystems


### 解决办法

#### 1.首先查看，此分区的文件类型
> blkid - locate/print block device attributes

    blkid /dev/sda1

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210422093124227.png)


#### 2.查看XFS的文件系统的命令：xfs_info | xfs_growfs
> xfs_growfs, xfs_info - expand an XFS filesystem

    xfs_info /defv/sda1
    
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210422093241843.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)


得到Block size = 4096

</font>