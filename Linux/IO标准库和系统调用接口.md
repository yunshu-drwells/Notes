### 标准库接口

> fopen/fread/fwrite/fseek/fclose
> 
> #include <stdio.h>

> FILE *fopen(const char *path, const char *mode);</br>
> size_t fread(void *ptr, size_t size, size_t nmemb, FILE *stream);</br>
> size_t fwrite(const void *ptr, size_t size, size_t nmemb,FILE *stream);</br>
> int fseek(FILE *stream, long offset, int whence);
> int fclose(FILE *stream);


</br></br>

- FILE *fopen(const char *path, const char *mode);</br>
#include <stdio.h>
> **description:**</br>
> The fopen() function opens the file whose name is the string pointed
to by pathname and associates a stream with it.

> The argument mode points to a string beginning with one of the
following sequences (possibly followed by additional characters, as
described below):

> **made:**</br>
> r+     Open for reading and writing.  The stream is positioned at the
beginning of the file.

> w      Truncate file to zero length or create text file for writing.
The stream is positioned at the beginning of the file.

> w+     Open for reading and writing.  The file is created if it does
not exist, otherwise it is truncated.  The stream is
positioned at the beginning of the file.

> a      Open for appending (writing at end of file).  The file is
created if it does not exist.  The stream is positioned at the
end of the file.

> a+     Open for reading and appending (writing at end of file).  The
file is created if it does not exist.  Output is always
appended to the end of the file.  POSIX is silent on what the
initial read position is when using this mode.  For glibc, the
initial file position for reading is at the beginning of the
file, but for Android/BSD/MacOS, the initial file position for
reading is at the end of the file.




</br></br>

- size_t fread(void *ptr, size_t size, size_t nmemb, FILE *stream);</br>
#include <stdio.h>
> **description:**</br>
The function fread() reads nmemb items of data, each size bytes long,
from the stream pointed to by stream, storing them at the location
given by ptr.  
> **return value:**</br>
On success, fread() and fwrite() return the number of items read or
written.  This number equals the number of bytes transferred only
when size is 1.  If an error occurs, or the end of the file is
reached, the return value is a short item count (or zero).</br>
fread() does not distinguish between end-of-file and error, and
callers must use feof(3) and ferror(3) to determine which occurred.





</br></br>

- size_t fwrite(const void *ptr, size_t size, size_t nmemb,FILE *stream);</br>
#include <stdio.h>
> **description:**</br>
> The function fwrite() writes nmemb items of data, each size bytes
long, to the stream pointed to by stream, obtaining them from the
location given by ptr.</br>
> **return value:**</br>
On success, fread() and fwrite() return the number of items read or
written.  This number equals the number of bytes transferred only
when size is 1.  If an error occurs, or the end of the file is
reached, the return value is a short item count (or zero).</br>




</br></br>

- int fseek(FILE *stream, long offset, int whence);</br>
#include <stdio.h>
> **description:**</br>
The fseek() function sets the file position indicator for the stream
pointed to by stream.  The new position, measured in bytes, is
obtained by adding offset bytes to the position specified by whence.
If whence is set to SEEK_SET, SEEK_CUR, or SEEK_END, the offset is
relative to the start of the file, the current position indicator, or
end-of-file, respectively.  A successful call to the fseek() function
clears the end-of-file indicator for the stream and undoes any
effects of the ungetc(3) function on the same stream.</br>
> **return value:**</br>
successful completion,
fgetpos(), fseek(), fsetpos() return 0, and ftell() returns the
current offset.  Otherwise, -1 is returned and errno is set to
indicate the error.




</br></br>

- int fclose(FILE *stream);</br>
#include <stdio.h>
> **description:**</br>
The fclose() function flushes the stream pointed to by stream
(writing any buffered output data using fflush(3)) and closes the
underlying file descriptor.</br>
> **return value:**</br>
Upon successful completion, 0 is returned.  Otherwise, EOF is
returned and errno is set to indicate the error.  In either case, any
further access (including another call to fclose()) to the stream
results in undefined behavior.







</br></br></br></br></br></br>


> fgets/printf/sprintf(buffer)/snprintf(buffer)/fprintf(file)

> char *fgets(char *restrict s, int n, FILE *restrict stream);
> int sprintf(char *restrict s, const char *restrict format, ...);
> int snprintf(char *str, size_t size, const char *format, ...);
> int fprintf(FILE *stream, const char *format, ...);


</br></br>

- char *fgets(char *restrict s, int n, FILE *restrict stream);</br>
#include <stdio.h>
> **description:**</br>
The functionality described on this reference page is aligned with
the ISO C standard. Any conflict between the requirements described
here and the ISO C standard is unintentional. This volume of
POSIX.1‐2008 defers to the ISO C standard.
The fgets() function shall read bytes from stream into the array
pointed to by s, until n−1 bytes are read, or a <newline> is read and
transferred to s, or an end-of-file condition is encountered. The
string is then terminated with a null byte.
The fgets() function may mark the last data access timestamp of the
file associated with stream for update. The last data access
timestamp shall be marked for update by the first successful
execution of fgetc(), fgets(), fread(), fscanf(), getc(), getchar(),
getdelim(), getline(), gets(), or scanf() using stream that returns
data not supplied by a prior call to ungetc().</br>
> **return value:**</br>
Upon successful completion, fgets() shall return s.  If the stream is
at end-of-file, the end-of-file indicator for the stream shall be set
and fgets() shall return a null pointer.  If a read error occurs, the
error indicator for the stream shall be set, fgets() shall return a
null pointer, and shall set errno to indicate the error.



</br></br>

- int sprintf(char *restrict s, const char *restrict format, ...);</br>
#include <stdio.h>
> **description:**</br>
sprintf(), snprintf(), vsprintf() and  vsnprintf()  write  to  the character string str.</br>
> **return value:**</br>
Upon  successful  return, these functions return the number of characters printed
(excluding the null byte used to end output to strings).





</br></br>

- int snprintf(char *str, size_t size, const char *format, ...);
#include <stdio.h>
> **description:**</br>
The  functions snprintf() and vsnprintf() write at most size bytes (including the
terminating null byte ('\0')) to str.</br>
the  functions  printf(),  fprintf(), sprintf(), snprintf(), respectively, except
that they are called with a va_list instead of a variable  number  of  arguments.
These  functions  do  not  call the va_end macro.  Because they invoke the va_arg
macro, the value of ap is undefined after the call. </br>
> **return value:**</br>
The functions snprintf() and vsnprintf()  do  not  write  more  than  size  bytes
(including the terminating null byte ('\0')).  If the output was truncated due to
this limit then the return value is the number of characters (excluding the  ter‐
minating  null  byte) which would have been written to the final string if enough
space had been available.  Thus, a return value of size or more  means  that  the
output was truncated.  (See also below under NOTES.)




</br></br>

- int fprintf(FILE *stream, const char *format, ...);
#include <stdio.h>
> **description:**</br>
fprintf() and vfprintf() write output to the given
output stream;
the  functions  fprintf() respectively, except
that they are called with a va_list instead of a variable  number  of  arguments.
These  functions  do  not  call the va_end macro.  Because they invoke the va_arg
macro, the value of ap is undefined after the call.
> **return value:**</br>
Upon  successful  return, these functions return the number of characters printed
(excluding the null byte used to end output to strings).




<img src="https://img-blog.csdnimg.cn/20210129183339102.png" height=30>








### 系统调用接口

> open/creat/write/read/lseek/close
> 
> #include <fcntl.h> </br>

- int open(const char *pathname, int flags);
- int open(const char *pathname, int flags, mode_t mode);
- open不定参函数(C语言中没有函数重载)</br>
> **argument:**</br>
> flags:</br>
> 必选: </br>
O_RDONLY / O_WRONLY / O_RDWR</br>
可选:</br>
O_CREAT: 文件存在打开,不存在创建</br>
O_EXCL: 文件不存在则创建,存在就报错返回</br>
O_TRUNC:打开的同时清空内容</br>
O_APPEND:追加写入</br>
>
> mode:以8进制指定<a href="https://blog.csdn.net/qq_43808700/article/details/116026208?utm_source=app">文件权限</a>


> **description:**</br>
returns a file descriptor, a small, nonnegative integer for use in subsequent sys‐tem calls.The file descriptor returned by a successful call will be the lowest-numbered file descriptor not currently open for the process;false return -1
>
> **return value:**</br>
open()  and  creat() return the new file descriptor, or -1 if an error occurred
>
> 库函数封装系统调用时:</br>
r+: O_RDWR</br>
w+: O_RDWR | O_TRUNC | O_CREAT</br>
a+: O_RDWR | O_APPEND | O_CREAT</br>

</br></br>




- int creat(const char *pathname, mode_t mode);
> **argument:**</br>
mode：以8进制指定<a href="https://blog.csdn.net/qq_43808700/article/details/116026208?utm_source=app">文件权限</a>

> **description:**</br>
possibly create a file
creat() is equivalent to open() with flags equal to O_CREAT|O_WRONLY|O_TRUNC.

> **return value:**</br>
open()  and  creat() return the new file descriptor, or -1 if an error occurred

</br></br>





- ssize_t write(int fd, char* data, size_t count )
> fd:文件描述符(open函数返回的句柄)
data:写入的数据首地址
count:写入的数据长度
> 返回值:成功返回写入的字节数,失败-1

</br></br>




- ssize_t read(int fd, char* buf, size_t count)</br>
> 参数：</br>
fd: 文件描述符(open函数返回的句柄)
buf: 一块缓冲区的首地址,用于存储读取的数据
count:想要读取的数据长度
> 返回值:</br>
0 实际读取的数据长度, -1错误, 0读到了文件末尾
 
</br></br>



- off_t lseek(int fd,long offset,int whence)
> **argument:**</br>
whence:</br>
SEEK_SET:The offset is set to offset bytes.</br>
SEEK_CUR:The offset is set to its current location plus offset bytes.</br>
SEEK_END:The offset is set to the size of the file plus offset bytes.</br>
>
> **description:**</br>
lseek function repositions the offset of the open file associated with the file descriptor fd to the argument offset according to the directive whence as follows
>
> **return value:**</br>
fseek返回值是跳转后的位置相对于文件起始位置的偏移量

</br></br>


- close(int fd);


> 注意事项:
> 1、如果open使用O_CREAT，那么就一定要加上第三个权限参数</br>
> 2、权限参数是8进制，总共四位不要忘了前边这个0



