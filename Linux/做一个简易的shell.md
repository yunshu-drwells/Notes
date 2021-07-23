<font size = 4 face = "黑体">


### 分析shell运行机制

的时间轴来表示事件的发生次序。其中时间从左向右。shell由标识为bash的方块代表，它随着时间的流逝从左向右移动。shell从用户读入字符串"ls"。shell创建一个子进程，然后在那个进程中运行ls程序并等待那个进程结束,子进程退出，回到父进程。然后shell读取新的一行输入，建立一个新的进程，在这个进程中运行程序 并等待这个进程结束......循环往复


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210405115418228.png)


这个过程仅限于需要在子shell中运行的命令


<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=50>




### shell运行过程


1. 获取命令行
2. 解析命令行
3. 建立一个子进程（fork）
4. 替换子进程（execvp）


```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>
#include <fcntl.h>
#define MAX_CMD 1024
char command[MAX_CMD];
int do_face()
{
	memset(command, 0x00, MAX_CMD);
	printf("minishell$ ");
	fflush(stdout); //刷新缓冲区，有内容就显示
	if (scanf("%[^\n]%*c", command) == 0) {
		getchar();
		return -1;
	}
	return 0;
}
char** do_parse(char* buff)
{
	int argc = 0;
	static char* argv[32];
	char* ptr = buff;
	while (*ptr != '\0') {
		if (!isspace(*ptr)) {
			argv[argc++] = ptr;
			while ((!isspace(*ptr)) && (*ptr) != '\0') {
				ptr++;
			}
			continue;
		}
		*ptr = '\0';
		ptr++;
	}
	argv[argc] = NULL;
	return argv;
}
int do_exec(char* buff)
{
	char** argv = { NULL };
	int pid = fork();
	if (pid == 0) {
		argv = do_parse(buff);
		if (argv[0] == NULL) {
			exit(-1);
		}
		execvp(argv[0], argv);
	}
	else {
		waitpid(pid, NULL, 0);
	}
	return 0;
}
int main(int argc, char* argv[])
{
	while (1) {
		if (do_face() < 0)
			continue;
		do_exec(command);
	}
	return 0;
}
```

%[^\n]%*c将逐个读取缓冲区中的’\n’字符之前的其它字符，％后面的*表示将读取的这些字符丢弃，前遇到’\n’字符时便停止读取操作，此时，缓冲区中尚有一个’\n’字符遗留，所以后面的％*c将读取并丢弃这个遗留的换行符，这里的星号和前面的星号作用相同。由于所有从键盘的输入都是以回车结束的，而回车会产生一个’\n’字符，所以将’\n’连同它之前的字符全部读取并丢弃之后，也就相当于清除了输入缓冲区。

</font>