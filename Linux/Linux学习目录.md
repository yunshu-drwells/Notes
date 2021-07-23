
<font size = 4 face = "黑体">


### <a href="https://blog.csdn.net/qq_43808700/article/details/115832790?utm_source=app">1.认识进程</a>


&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115832790?utm_source=app#defination" target="_self" one-link-mark="yes">定义</a>

&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115832790?utm_source=app#guardProcess" target="_self" one-link-mark="yes">查看进程</a>

&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115832790?utm_source=app#StatusProcess" target="_self" one-link-mark="yes">进程状态</a>

&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115832790?utm_source=app#zombieProcess" target="_self" one-link-mark="yes">僵尸进程</a>

&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115832790?utm_source=app#orphanProcess" target="_self" one-link-mark="yes">孤儿进程</a>

&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115832790?utm_source=app#priorityProcess" target="_self" one-link-mark="yes">进程优先级</a>

&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115832790?utm_source=app#nice" target="_self" one-link-mark="yes">nice值</a>











### <a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app">2.进程控制</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#foundProcess">进程创建</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#fork">fork</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#vfork">vfork</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#waitProcess">进程等待</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#wait">wait方法</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#waitpid">waitpid方法</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#getStatus">获取子进程status</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#wait_get_status">wait方式获取子进程status</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#waitpid_get_status">waitpid方式获取status</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#waitProcess">进程等待</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#waitpid_block_wait">waitpid进程的阻塞方式等待</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#waitpid_noblock_wait">waitpid进程的非阻塞等待方式</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#replace_process">进程替换</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#Shell_replace">Shell进程替换</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#Shell_replace_face">Shell进程替换的本质</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#process_replace_face">进程替换原理</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115833226?utm_source=app#minishell">实现一个minishell</a>














### <a href="https://blog.csdn.net/qq_43808700/article/details/115834225?utm_source=app">3.进程间通信</a>


&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834225?utm_source=app#process_communication">进程间通信</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834225?utm_source=app#process_communication_progress">进程间通信发展</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834225?utm_source=app#communication_ways">通信方式</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834225?utm_source=app#pipeline">管道</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834225?utm_source=app#pipe">匿名管道</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834225?utm_source=app#mkfife">命名管道</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834225?utm_source=app#systemV_share">system V共享</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834225?utm_source=app#systemV_message_queue">system V消息队列</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834225?utm_source=app#systemV_semaphore">system V信号量</a>




















### <a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app">4.进程信号量</a>



&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#linux_semaphore">linux中的信号</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#Ctrl-C_characteristic">Ctrl-C特点</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#sign_defination">信号概念</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#sign_essence">信号本质</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#sign_handle_method">信号处理常见方式</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#linux_sign_sort_way">linux中的信号的两种分类方式</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#credibility_noncredibility_sign">可靠信号与不可靠信号</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#realTime_nonRealTime_sign">实时信号与非实时信号</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#gender_sign">产生信号</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#1.gender_by_push_button">1.通过终端按键产生信号(硬件)</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#2.gender_by_hardware">2.硬件异常产生信号</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#3.gender_by_killFunction">3.调用系统函数kill向进程发信号</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#4.gender_by_software">4.由软件条件产生信号</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#sign_catch">信号捕捉</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#siganl_function_catch">siganl函数进行信号捕捉</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#simulation_wild_pointer">模拟一下野指针异常</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#summary">总结</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#sign_handle_ways">信号处理的三种方式</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#sign_handle_flow">信号处理流程</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#sign_hangle_state_change">信号产生到处理的状态</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#sign_express_in_kernal">信号在内核中的表示</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834703?utm_source=app#sign_catch_in_kernal">内核实现信号捕捉</a>






















### <a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app">5.多线程</a>
&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_conception">线程概念</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_defination">线程定义</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_advantage">线程的优点</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_disadvantage">线程的缺点</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_exception">线程异常</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_application">线程用途</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#process_vs_thread">进程与线程比较</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#process_concurrency">进程可以并发并行</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_concurrency">线程可以并发并行</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_shared_resource">进程的多个线程共享的内容</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#Linux_thread_control">Linux线程控制</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#POSIX_thread_library">POSIX线程库</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#pthread_create">pthread_create</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#pthread_error_checking">pthread_族函数错误检查</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#use_pthread_creat_to_found_a_thread">使用pthread_creat创建一个新的线程</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_ID">线程ID</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_terminate">线程终止</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_wait">线程等待</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#detach_thread">分离线程</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_mutex">线程互斥</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#mutex_conception">进程线程互斥相关概念</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#mutex">互斥量mutex</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#mutex_lock">互斥量(锁)</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#mutex_theory">互斥量实现原理</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_safe">线程安全</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#reentry">重入</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#reentry_vs_threadSafe">可重入与线程安全的关系</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#common_lock">常见锁</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#deadly_lock">死锁</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#deadly_lock_necessary_condition">死锁发生的必要条件(4)</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#avoid_deadly_lock">避免死锁</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#avoid_deadly_lock_arithmetic">避免死锁算法</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_synchronization">线程同步</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#defination">定义</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#race_conditon">竞态条件</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_syn_ways">线程同步四种方式</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#condition_variable">条件变量</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#conditon_function">条件变量函数</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#production_consumption_model">生产者消费者模型</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#BlockingQueue_production_consumption_model">基于BlockingQueue的生产者消费者模型</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#C++_imitate_blocked_queue_production_consumption_model">C++ queue模拟阻塞队列的生产消费模型</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#POSIX_semaphore">POSIX信号量</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#initialize_semaphore">初始化信号量</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#destory_semaphore">销毁信号量</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#wait_semaphore">等待信号量</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#release_semaphore">发布信号量</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_pool">线程池</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_pool_application">线程池的应用场景</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_pool_example">线程池示例</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#thread_safe_Singleton">线程安全的单例模式</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834782?utm_source=app#STL_auto_ptr_threadSafe">STL,智能指针和线程安全</a>
















### <a href="https://blog.csdn.net/qq_43808700/article/details/115834797?utm_source=app">6.网络1</a>
&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834797?utm_source=app#network_protocol">网络协议</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834797?utm_source=app#protocol_delamination">网络协议分层</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834797?utm_source=app#OSI_model">OSI七层模型</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834797?utm_source=app#TCP/IP_model">TCP/IP五层(或四层)模型</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834797?utm_source=app#network_transportation_flow">网络传输流程</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834797?utm_source=app#package_packaging_minuting">数据包封装和分用</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834797?utm_source=app#packing">数据封装的过程</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834797?utm_source=app#minuting">数据分用的过程</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834797?utm_source=app#address_management">网络中的地址管理</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834797?utm_source=app#IP_adress">IP地址</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834797?utm_source=app#MAC_adress">MAC地址</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834797?utm_source=app#IP_adress和MAC_adress_effect">IP地址和MAC地址作用</a>

















### <a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app">7.网络2</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#application_layer">应用层</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#HTTP">HTTP</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#URL">URL</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#urlencode_urldecode">urlencode和urldecode</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#port">端口号</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#transfer">传输层</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#UDP">UDP协议</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#TCP">TCP</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#TCP_segmentation_form">TCP协议段格式</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#connection_management">连接管理机制</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#three_handshake">三次握手</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#Confirm_response_Wave_four_times">确认应答(ACK)机制和四次挥手</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#Confirm_response">确认应答(ACK)机制</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#Wave_four_times">四次挥手</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#timeout_retransmission">超时重传机制</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#Sliding_window">滑动窗口</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#flow_control">流量控制</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#congestion_control">拥塞控制</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#Delayed_response">延迟应答</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#piggyback_acknowledgement">捎带应答</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#Byte_stream_oriented">面向字节流</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#Sticky_bag_problem">粘包问题</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#TCP_exception">TCP异常情况</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#TCP/UDP_VS">TCP/UDP对比</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#TCP_UDP_distinguish_head">TCP 和 UDP 的区别及头部结构</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115834813?utm_source=app#MSL">MSL</a>













### <a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app">8.网络3</a>
&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#network_layer">网络层</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#IP">IP协议</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#segmentation_form">协议头格式</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#Network_segmentation">网段划分(重要)</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#private_public_IP_address">私有IP地址和公网IP地址</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#route">路由</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#route_table_build">路由表生成算法</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#data_link_layer">数据链路层</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#Ethernet">以太网</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#Ethernet_frame_form">以太网帧格式(链路层)</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#MAC">MAC地址</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#MTU">MTU</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#ARP">ARP协议</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#ARP_application">ARP协议的作用</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#ARP_work_flow">ARP协议的工作流程</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#ARP_message_form">ARP数据报的格式</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#protocols">重要协议</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115855142?utm_source=app#DNS">DNS</a>









### <a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app">9.网络编程套接字</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#Socket">网络编程基础知识</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#IP">IP</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#port">端口号</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#TCP">TCP协议</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#UDP">UDP协议</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#network_Byte_order">网络字节序</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#socket_API">socket编程接口</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#API">常见API</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#sockaddr">sockaddr 结构体</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#sockaddr_in">sockaddr_in 结构体</a>

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#in_addr">in_addr 结构体</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#UDP_program">简单的UDP网络程序</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#address_converted_function">地址转换函数</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#str_2_in_addr">字符串转in_addr的函数</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#in_addr_2_str">in_addr转字符串的函数</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#str_both_convert_in_addr">字符串和in_addr转换</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#inet_ntoa">inet_ntoa函数</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#TCP_program">简单的TCP网络程序(CS结构的英译汉)</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115870749?utm_source=app#multi-Progress">将以上英译汉改成多进程版本</a>











### <a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app">10.IO1</a>


##### 基础知识

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#File_descriptor">文件描述符</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#File_descriptor_essence">文件描述符本质</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#fd_Distribution_rules">文件描述符的分配规则</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#redirect">重定向</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#FILE">库函数中的FILE</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#struct _IO_FILE">struct _IO_FILE</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#library_function_has_buffer">库函数带缓冲区</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#fd_FIFE">文件描述符与文件流指针的关系</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#dynamic_static_lib">动态库和静态库</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#Ext">文件系统Ext</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#basic_construction">基本结构</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#command">相关命令</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#save_file_flow">文件存储流程</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#read_file">文件读取</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#creat_new_file">创建一个新文件</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#Symbolic_link">符号链接文件</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#creat_Hard_link_file">创建硬链接文件</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#creat_Soft_link_file">创建软链接文件</a>

##### IO标准库和系统调用接口



&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#lib_function">库函数</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/115941000?utm_source=app#sys_API">系统调用接口</a>












### <a href="https://blog.csdn.net/qq_43808700/article/details/116057119?utm_source=app">11.IO2</a>

##### 基本概念


&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/116057119?utm_source=app#syn_Communication">同步通信</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/116057119?utm_source=app#asynchronism_Communication">异步通信</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/116057119?utm_source=app#block_vs_unblock">阻塞 vs 非阻塞</a>

##### 五种IO模型
&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/116057119?utm_source=app#block_IO">阻塞IO</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/116057119?utm_source=app#unblock_IO">非阻塞IO</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/116057119?utm_source=app#signal_drive_IO">信号驱动IO</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/116057119?utm_source=app#IO_Multiplexing">IO多路转接复用</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/116057119?utm_source=app#select">select</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/116057119?utm_source=app#poll">poll</a>

&emsp;&emsp;&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/116057119?utm_source=app#epoll">epoll</a>

&emsp;&emsp;<a href="https://blog.csdn.net/qq_43808700/article/details/116057119?utm_source=app#asynchronism_IO">异步IO</a>








</font>