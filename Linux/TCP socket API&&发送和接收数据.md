<font size = 4 face = "黑体">


# TCP socket API

**socket API的函数都在sys/socket.h**

## socket()函数

socket()打开一个网络通讯端口,如果成功的话,就像open()一样返回一个文件描述符;应用程序可以像读写文件一样用read/write在网络上收发数据;如果socket()调用出错则返回-1;

### 原型及参数

    int socket(int af, int type, int protocol);

- af^[Address Family] 为地址族，也就是 IP 地址类型，常用的有 AF\_INET(IPv4) 和 AF\_INET6(IPv6)^[INET是“Inetnet”的简写;AF\_INET 表示 IPv4 地址，例如 127.0.0.1(它是一个特殊IP地址，表示本机地址)；AF_INET6 表示 IPv6 地址，例如 1030::C9B4:FF12:48AA:1A2B。]。

- type 为数据传输方式/套接字类型，常用的有 SOCK\_STREAM（流格式套接字/面向连接的套接字） 和 SOCK_DGRAM（数据报套接字/无连接的套接字）

- protocol 表示传输协议，常用的有 IPPROTO\_TCP 和 IPPTOTO_UDP，分别表示 TCP 传输协议和 UDP 传输协议

> SOCK_STREAM对应IPPROTO_TCP;SOCK_DGRAM对应IPPROTO_UDP。可以将 protocol 的值设为 0，系统会自动推演出应该使用什么协议

### 代码示例

#### Linux

```
    int tcp_socket = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);  //IPPROTO_TCP表示TCP协议
    int udp_socket = socket(AF_INET, SOCK_DGRAM, IPPROTO_UDP);  //IPPROTO_UDP表示UDP协议
    
    //可以将 protocol 的值设为 0，系统会自动推演出应该使用什么协议
    int tcp_socket = socket(AF_INET, SOCK_STREAM, 0);  //创建TCP套接字
    int udp_socket = socket(AF_INET, SOCK_DGRAM, 0);  //创建UDP套接字
```

#### Windows

> 原型：SOCKET socket(int af, int type, int protocol);

与Linux平台唯一不同的是返回值不同，返回 SOCKET 类型的句柄

```
    SOCKET sock = socket(AF_INET, SOCK_STREAM, 0);  //创建TCP套接字
```

<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=30>










## bind()函数

服务器端要用 bind() 函数将套接字与特定的IP地址和端口绑定起来，只有这样，流经该IP地址和端口的数据才能交给套接字处理。类似地，客户端也要用 connect() 函数建立连接。

bind()成功返回0,失败返回-1

### 原型及参数


    int bind(int sock, struct sockaddr *addr, socklen_t addrlen);  //Linux
    int bind(SOCKET sock, const struct sockaddr *addr, int addrlen);  //Windows


- sock 为 socket 文件描述符

- addr 为 sockaddr 结构体变量的指针

- addrlen 为 addr 变量的大小，可由 sizeof() 计算得出

### 代码示例

#### 将创建的套接字与IP地址 127.0.0.1、端口 1234 绑定

```
    //创建套接字
    int serv_sock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);
    
    //创建sockaddr_in结构体变量
    struct sockaddr_in serv_addr;
    memset(&serv_addr, 0, sizeof(serv_addr));  //每个字节都用0填充。先用 memset() 将结构体的全部字节填充为 0的目的就是将最后8个预留的sin_zero置为0
    //serv_addr还可以使用bzero函数初始化
    bzero(&serv_addr, sizeof(serv_addr));
    serv_addr.sin_family = AF_INET;  //使用IPv4地址
    serv_addr.sin_addr.s_addr = inet_addr("127.0.0.1");  //具体的IP地址
    serv_addr.sin_port = htons(1234);  //端口
    
    //将套接字和IP、端口绑定
    bind(serv_sock, (struct sockaddr*)&serv_addr, sizeof(serv_addr));
```



##### 以上例子使用 sockaddr_in 结构体，然后再强制转换为 sockaddr 类型的原因：使用 sockaddr_in 结构体就是为了方便给AF、IP地址和端口赋值

###### struct in_addr 结构体


```
    struct in_addr{
        in_addr_t  s_addr;  //32位的IP地址
    };
```
> in_addr_t 在头文件 <netinet/in.h> 中定义，等价于 unsigned long，长度为4个字节。
> s_addr 是一个整数，而IP地址是一个字符串，所以需要 inet_addr() 函数进行转换


###### sockaddr_in 结构体


```
    struct sockaddr_in{
        sa_family_t     sin_family;   //地址族（Address Family），也就是地址类型
        uint16_t        sin_port;     //16位的端口号 端口号需要用 htons() 函数转换
        struct in_addr  sin_addr;     //32位IP地址 sin_addr 是 struct in_addr 结构体类型的变量
        char            sin_zero[8];  //不使用，一般用0填充
    };
```

> sin_prot 为端口号。uint16_t 的长度为两个字节，理论上端口号的取值范围为 0~65536，但 0~1023 的端口一般由系统分配给特定的服务程序，例如 Web 服务的端口号为 80，FTP 服务的端口号为 21，所以我们的程序要尽量在 1024~65536 之间分配端口号。
>
> 端口号需要用 htons() 函数转换


**in\_addr是sockaddr_in的成员变量**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210419163401619.png)



IP地址是sockaddr\_in结构体中嵌套的in_addr结构体,或许是历史原因吧，后面的接口总要兼容前面的代码




###### sockaddr 结构体



```
    struct sockaddr{
        sa_family_t  sin_family;   //地址族（Address Family），也就是地址类型
        char         sa_data[14];  //IP地址和端口号
    };
```


**sockaddr 与 sockaddr_in 的对比**


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210419165613664.png)



sockaddr 和 sockaddr\_in 的长度相同，都是16字节，只是将IP地址和端口号合并到一起，用一个成员 sa\_data 表示。要想给 sa\_data 赋值，必须同时指明IP地址和端口号，例如"127.0.0.1:80"，遗憾的是，没有相关函数将这个字符串转换成需要的形式，也就很难给 sockaddr 类型的变量赋值，所以使用 sockaddr_in 来代替。这两个结构体的长度相同，强制转换类型时不会丢失字节，也没有多余的字节。


可以认为，sockaddr 是一种通用的结构体，可以用来保存多种类型的IP地址和端口号，而 sockaddr\_in 是专门用来保存 IPv4 地址的结构体。另外还有 sockaddr_in6，用来保存 IPv6 地址


###### sockaddr_in6 结构体


```
    struct sockaddr_in6 { 
        sa_family_t sin6_family;  //(2)地址类型，取值为AF_INET6
        in_port_t sin6_port;  //(2)16位端口号
        uint32_t sin6_flowinfo;  //(4)IPv6流信息
        struct in6_addr sin6_addr;  //(4)具体的IPv6地址
        uint32_t sin6_scope_id;  //(4)接口范围ID
    };
```

> sockaddr、sockaddr_in、sockaddr相关结构体在<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#socket编程接口_结构体">9.网络编程套接字文章中socket编程接口</a>中有介绍


<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=30>














## connect()函数

connect()用来将参数sockfd 的socket 连至参数serv_addr 指定的网络地址,connect() 函数是客户端用来与服务端建立连接的。

如果连接或绑定成功返回0，错误返回-1


### 原型及参数


    int connect(int sock, struct sockaddr *serv_addr, socklen_t addrlen);  //Linux
    int connect(SOCKET sock, const struct sockaddr *serv_addr, int addrlen);  //Windows
    
    
- sock：标识一个未连接socket
- serv_addr：指向要连接套接字的sockaddr结构体的指针(要连接的目标IP和端口)
- addrlen：sockaddr结构体的字节长度


### 代码示例




```
    //创建套接字
    int serv_sock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);
    
    //创建sockaddr_in结构体变量
    struct sockaddr_in serv_addr;
    memset(&serv_addr, 0, sizeof(serv_addr));  //每个字节都用0填充。先用 memset() 将结构体的全部字节填充为 0的目的就是将最后8个预留的sin_zero置为0
    //serv_addr还可以使用bzero函数初始化
    bzero(&serv_addr, sizeof(serv_addr));
    serv_addr.sin_family = AF_INET;  //使用IPv4地址
    serv_addr.sin_addr.s_addr = inet_addr("127.0.0.1");  //具体的IP地址
    serv_addr.sin_port = htons(1234);  //端口
    
    //将套接字和IP、端口绑定
    connect(serv_sock, (struct sockaddr*)&serv_addr, sizeof(serv_addr));
```




<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=30>













## listen()函数

对于服务器端程序，使用 bind() 绑定套接字后，还需要**使用 listen() 函数让套接字进入被动监听状态**，再调用 accept() 函数，就可以随时响应客户端的请求了。


所谓**被动监听**，是指当没有客户端请求时，套接字处于“睡眠”状态，只有当接收到客户端请求时，套接字才会被“唤醒”来响应请求。


listen()成功返回0,失败返回-1


### 原型及参数

    int listen(int sock, int backlog);  //Linux
    int listen(SOCKET sock, int backlog);  //Windows

- sock 为需要进入监听状态的套接字
- backlog 为请求队列的最大长度,意思最多允许有backlog个客户端处于连接等待状态

### 请求队列

当套接字正在处理客户端请求时，如果有新的请求进来，套接字是没法处理的，只能把它放进缓冲区，待当前请求处理完毕后，再从缓冲区中读取出来处理。如果不断有新的请求进来，它们就按照先后顺序在缓冲区中排队，直到缓冲区满。这个缓冲区，就称为请求队列（Request Queue）。

缓冲区的长度（能存放多少个客户端请求）可以通过 listen() 函数的 backlog参数指定，但究竟为多少并没有什么标准，可以根据需求来定，并发量小的话可以是10或者20。

如果将 backlog 的值设置为 SOMAXCONN，就由系统来决定请求队列长度，这个值一般比较大，可能是几百，或者更多。

当请求队列满时，就不再接收新的请求，对于 Linux，客户端会收到 <a href="https://blog.csdn.net/qq_43808700/article/details/115868629?utm_source=app">ECONNREFUSED</a> 错误，对于 Windows，客户端会收到 WSAECONNREFUSED 错误。

**注意：listen() 只是让套接字处于监听状态，并没有接收请求。接收请求需要使用 accept() 函数。**



<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=30>









## accept()函数

当套接字处于监听状态时，可以通过 accept() 函数来接收客户端请求


### 原型及参数


    int accept(int sock, struct sockaddr *addr, socklen_t *addrlen);  //Linux
    SOCKET accept(SOCKET sock, struct sockaddr *addr, int *addrlen);  //Windows


- sock 为服务器端套接字
- addr 为 sockaddr_in 结构体变量;addr是一个输出型参数,accept()返回时传出客户端的地址和端口号;如果给addr 参数传NULL,表示不关心客户端的地址
- addrlen 为参数 addr 的长度，可由 sizeof() 求得。addrlen参数是一个传入传出参数(value-result argument), 传入的是调用者提供的缓冲区addr的长度,以避免缓冲区溢出问题,传出的是客户端地址结构体的实际长度(有可能没有占满调用者提供的缓冲区);


> accept的参数与 listen() 和 connect() 是相同的
>
> **accept() 返回一个新的套接字来和客户端通信，addr 保存了客户端的IP地址和端口号，而 sock 是服务器端的套接字**
>
> **listen() 只是让套接字进入监听状态，并没有真正接收客户端请求，listen() 后面的代码会继续执行，直到遇到 accept()。accept() 会阻塞程序执行（后面代码不能被执行），直到有新的请求到来。**



<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=30>
<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=30>






# Linux发送和接收数据

Linux 不区分套接字文件和普通文件，使用 write() 可以向套接字中写入数据，使用 read() 可以从套接字中读取数据。

## write()函数

write() 函数会将缓冲区 buf 中的 nbytes 个字节写入文件 fd，成功则返回写入的字节数，失败则返回 -1


### 原型及参数

    ssize_t write(int fd, const void *buf, size_t nbytes);
    
- fd 为要写入的文件的描述符
- buf 为要写入的数据的缓冲区地址
- nbytes 为要写入的数据的字节数

> size_t 是通过 typedef 声明的 unsigned int 类型；ssize_t 在 "size_t" 前面加了一个"s"，代表 signed，即 ssize_t 是通过 typedef 声明的 signed int 类型

<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=30>




## read()函数


read() 函数会从 fd 文件中读取 nbytes 个字节并保存到缓冲区 buf，成功则返回读取到的字节数（但遇到文件结尾则返回0），失败则返回 -1。


### 原型及参数

    ssize_t read(int fd, void *buf, size_t nbytes);


- fd 为要读取的文件的描述符
- buf 为要接收数据的缓冲区地址
- nbytes 为要读取的数据的字节数




<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=30>


<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=30>





# Windows发送和接收数据

Windows 和 Linux 不同，Windows 区分普通文件和套接字，并定义了专门的接收和发送的函数。


## send()函数

send函数会将缓冲区 buf 中的 len 个字节写入sock，成功则返回写入的字节数，失败则返回 -1

### 原型及参数

    int send(SOCKET sock, const char *buf, int len, int flags);

- sock 为要发送数据的套接字
- buf 为要发送的数据的缓冲区地址
- len 为要发送的数据的字节数
- flags 为发送数据时的选项,最后的 flags 参数一般设置为 0 或 NULL

## recv()函数

recv函数会从sock读取len 个字节到缓冲区 buf中，成功则返回读取到的字节数，失败则返回 -1

### 原型及参数

    int recv(SOCKET sock, char *buf, int len, int flags);

> 参数与send意义相同


</font>