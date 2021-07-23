<font size = 4 face = "黑体">




### source . 和mv

    type source
    
    type .
 
得知source和.都是一个内建命令   

> source is a shell builtin
>
> . is a shell builtin

##### <a href="Linux内置命令和外部命令">内建命令</a>可以使用help查看帮助文档



    help source
 
得到source帮助文档：source从当前Shell中的文件执行命令

> Execute commands from a file in the current shell(source从当前Shell中的文件执行命令)
    
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404133716995.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)


    help .
    
得到.的帮助文档：.从当前Shell中的文件执行命令

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404134244462.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzODA4NzAw,size_16,color_FFFFFF,t_70)



##### 已知<a href="help命令">mv是外部命令</a>

    help mv
    
才会得到：no help topics match `mv'(当前bash无匹配的mv)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210404134055685.png)





<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=50>







### 区别


- 内置命令在系统启动时就调入内存，是常驻内存的，所以执行效率高。

- 而外部命令是系统的软件功能，用户需要时才从硬盘中读入内存。

- 内置命令才能使用help获取命令的帮助文档




### 查看所有bash 内置命令

help | less


    GNU bash, version 4.2.46(2)-release (x86_64-redhat-linux-gnu)
    These shell commands are defined internally.  Type `help' to see this list.
    Type `help name' to find out more about the function `name'.
    Use `info bash' to find out more about the shell in general.
    Use `man -k' or `info' to find out more about commands not in this list.
    
    A star (*) next to a name means that the command is disabled.
    
     job_spec [&]                                                          history [-c] [-d offset] [n] or history -anrw [filename] or histor>
     (( expression ))                                                      if COMMANDS; then COMMANDS; [ elif COMMANDS; then COMMANDS; ]... [>
     . filename [arguments]                                                jobs [-lnprs] [jobspec ...] or jobs -x command [args]
     :                                                                     kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill>
     [ arg... ]                                                            let arg [arg ...]
     [[ expression ]]                                                      local [option] name[=value] ...
     alias [-p] [name[=value] ... ]                                        logout [n]
     bg [job_spec ...]                                                     mapfile [-n count] [-O origin] [-s count] [-t] [-u fd] [-C callbac>
     bind [-lpvsPVS] [-m keymap] [-f filename] [-q name] [-u name] [-r k>  popd [-n] [+N | -N]
     break [n]                                                             printf [-v var] format [arguments]
     builtin [shell-builtin [arg ...]]                                     pushd [-n] [+N | -N | dir]
     caller [expr]                                                         pwd [-LP]
     case WORD in [PATTERN [| PATTERN]...) COMMANDS ;;]... esac            read [-ers] [-a array] [-d delim] [-i text] [-n nchars] [-N nchars>
     cd [-L|[-P [-e]]] [dir]                                               readarray [-n count] [-O origin] [-s count] [-t] [-u fd] [-C callb>
     command [-pVv] command [arg ...]                                      readonly [-aAf] [name[=value] ...] or readonly -p
     compgen [-abcdefgjksuv] [-o option]  [-A action] [-G globpat] [-W w>  return [n]
     complete [-abcdefgjksuv] [-pr] [-DE] [-o option] [-A action] [-G gl>  select NAME [in WORDS ... ;] do COMMANDS; done
     compopt [-o|+o option] [-DE] [name ...]                               set [-abefhkmnptuvxBCHP] [-o option-name] [--] [arg ...]
     continue [n]                                                          shift [n]
     coproc [NAME] command [redirections]                                  shopt [-pqsu] [-o] [optname ...]
     declare [-aAfFgilrtux] [-p] [name[=value] ...]                        source filename [arguments]
     dirs [-clpv] [+N] [-N]                                                suspend [-f]
     disown [-h] [-ar] [jobspec ...]                                       test [expr]
     echo [-neE] [arg ...]                                                 time [-p] pipeline
     enable [-a] [-dnps] [-f filename] [name ...]                          times
     eval [arg ...]                                                        trap [-lp] [[arg] signal_spec ...]
     exec [-cl] [-a name] [command [arguments ...]] [redirection ...]      true
     exit [n]                                                              type [-afptP] name [name ...]
     export [-fn] [name[=value] ...] or export -p                          typeset [-aAfFgilrtux] [-p] name[=value] ...
     false                                                                 ulimit [-SHacdefilmnpqrstuvx] [limit]
     fc [-e ename] [-lnr] [first] [last] or fc -s [pat=rep] [command]      umask [-p] [-S] [mode]
     fg [job_spec]                                                         unalias [-a] name [name ...]
     for NAME [in WORDS ... ] ; do COMMANDS; done                          unset [-f] [-v] [name ...]
     for (( exp1; exp2; exp3 )); do COMMANDS; done                         until COMMANDS; do COMMANDS; done
     function name { COMMANDS ; } or name () { COMMANDS ; }                variables - Names and meanings of some shell variables
     getopts optstring name [arg]                                          wait [id]
     hash [-lr] [-p pathname] [-dt] [name ...]                             while COMMANDS; do COMMANDS; done
     help [-dms] [pattern ...]                                             { COMMANDS ; }


#### 得到Linux中所有的内置命令有

alias, bg, bind, break, builtin, caller, cd, command, compgen, complete, compopt,  continue,  declare,  dirs,  disown,  echo,enable,  eval,  exec, exit, export, false, fc, fg, getopts, hash, help,history, jobs, kill, let, local, logout, mapfile, popd, printf,  pushd,pwd,  read, readonly, return, set, shift, shopt, source, suspend, test,times, trap, true, type, typeset, ulimit, umask, unalias, unset, wait



</font>