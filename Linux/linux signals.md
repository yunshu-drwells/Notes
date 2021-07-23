

linux signals

|Signal Name|	Number|	Description|
|:---|:---|:---|
|SIGHUP	  |1	|Hangup (POSIX)|
|SIGINT	  |2	|Terminal interrupt (ANSI)|
|SIGQUIT  |3	|Terminal quit (POSIX)|
|SIGILL	  |4	|Illegal instruction (ANSI)|
|SIGTRAP  |5	|Trace trap (POSIX)|
|SIGIOT	  |6	|IOT Trap (4.2 BSD)|
|SIGBUS	  |7	|BUS error (4.2 BSD)|
|SIGFPE	  |8	|Floating point exception (ANSI)|
|SIGKILL  |9	|Kill(can't be caught or ignored) (POSIX)|
|SIGUSR1  |10	|User defined signal 1 (POSIX)|
|SIGSEGV  |11	|Invalid memory segment access (ANSI)|
|SIGUSR2  |12	|User defined signal 2 (POSIX)|
|SIGPIPE  |13	|Write on a pipe with no reader, Broken pipe (POSIX)|
|SIGALRM  |14	|Alarm clock (POSIX)|
|SIGTERM  |15	|Termination (ANSI)|
|SIGSTKFLT|16	|Stack fault|
|SIGCHLD  |17	|Child process has stopped or exited, changed (POSIX)|
|SIGCONT  |18	|Continue executing, if stopped (POSIX)|
|SIGSTOP  |19	|Stop executing(can't be caught or ignored) (POSIX)|
|SIGTSTP  |20	|Terminal stop signal (POSIX)|
|SIGTTIN  |21	|Background process trying to read, from TTY (POSIX)|
|SIGTTOU  |22	|Background process trying to write, to TTY (POSIX)|
|SIGURG	  |23	|Urgent condition on socket (4.2 BSD)|
|SIGXCPU  |24	|CPU limit exceeded (4.2 BSD)|
|SIGXFSZ  |25	|File size limit exceeded (4.2 BSD)|
|SIGVTALRM	|26	|Virtual alarm clock (4.2 BSD)|
|SIGPROF	|27	|Profiling alarm clock (4.2 BSD)|
|SIGWINCH	|28	|Window size change (4.3 BSD, Sun)|
|SIGIO	    |29	|I/O now possible (4.2 BSD)|
|SIGPWR	    |30	|Power failure restart (System V)|
|......|||


|信号代号	|信号名称	|说 明|
|:--|:--|:--|
|1	|<font color="0000FF">SIGHUP	|  该信号让进程立即关闭.然后重新读取配置文件之后重启|
|2	|<font color="0000FF">SIGINT	|  程序中止信号，用于中止前台进程。相当于输出 Ctrl+C 快捷键|
|3	|SIGQUIT|	和SIGINT类似, 但由QUIT字符(通常是Ctrl-/)来控制. 进程在因收到SIGQUIT退出时会产生core文件, 在这个意义上类似于一个程序错误信号。|
|4	|SIGILL	|  执行了非法指令. 通常是因为可执行文件本身出现错误, 或者试图执行数据段. 堆栈溢出时也有可能产生这个信号。|
|5	|SIGTRAP|	由断点指令或其它trap指令产生. 由debugger使用。|
|6	|SIGABRT|	调用abort函数生成的信号。|
|7	|SIGBUS	|  非法地址, 包括内存地址对齐(alignment)出错。|
|8	|<font color="0000FF">SIGFPE	|  在发生致命的算术运算错误时发出。不仅包括浮点运算错误，还包括溢出及除数为 0 等其他所有的算术运算错误|
|9	|<font color="0000FF">SIGKILL|	用来立即结束程序的运行。本信号不能被阻塞、处理和忽略。般用于强制中止进程|
|10	|SIGUSR1|	留给用户使用|
|11	|SIGSEGV|	试图访问未分配给自己的内存, 或试图往没有写权限的内存地址写数据.|
|12	|SIGUSR2|	留给用户使用|
|13	|SIGPIPE|	管道破裂。这个信号通常在进程间通信产生，比如采用FIFO(管道)通信的两个进程，读管道没打开或者意外终止就往管道写，写进程会收到SIGPIPE信号。|
|14	|<font color="0000FF">SIGALRM|	时钟定时信号，计算的是实际的时间或时钟时间。alarm 函数使用该信号|
|15	|<font color="0000FF">SIGTERM|	正常结束进程的信号，kill 命令的默认信号。如果进程已经发生了问题，那么这 个信号是无法正常中止进程的，这时我们才会尝试 SIGKILL 信号，也就是信号 9|
|17	|<font color="0000FF">SIGCHLD|	子进程结束时, 父进程会收到这个信号。|
|18	|<font color="0000FF">SIGCONT|	该信号可以让暂停的进程恢复执行。本信号不能被阻断|
|19	|<font color="0000FF">SIGSTOP|	该信号可以暂停前台进程，相当于输入 Ctrl+Z 快捷键。本信号不能被阻断|
|20	|SIGTSTP|	停止进程的运行, 但该信号可以被处理和忽略. 用户键入SUSP字符时(通常是Ctrl-Z)发出这个信号|
|21	|SIGTTIN|	当后台作业要从用户终端读数据时, 该作业中的所有进程会收到SIGTTIN信号. 缺省时这些进程会停止执行.|
|22	|SIGTTOU|	类似于SIGTTIN, 但在写终端(或修改终端模式)时收到.|
|23	|SIGURG	|  有"紧急"数据或out-of-band数据到达socket时产生.|
|24	|SIGXCPU|	超过CPU时间资源限制. 这个限制可以由getrlimit/setrlimit来读取/改变。|
|25	|SIGXFSZ|	当进程企图扩大文件以至于超过文件大小资源限制。|
|26	|SIGVTALRM|	虚拟时钟信号. 类似于SIGALRM, 但是计算的是该进程占用的CPU时间.|
|27	|SIGPROF|	类似于SIGALRM/SIGVTALRM, 但包括该进程用的CPU时间以及系统调用的时间.|
|28	|SIGWINCH|	窗口大小改变时发出.|
|29	|SIGIO	|  文件描述符准备就绪, 可以开始进行输入/输出操作.|
|30	|SIGPWR	|  Power failure|
|31	|SIGSYS	|  非法的系统调用。|
|......|||


