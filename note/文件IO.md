### 文件I/O

#### C标准函数与系统函数的区别

* C标准函数： fopen ,fread,printf ...工作在操作系统之上

* 系统函数：
    + window： writefile
    + linux :write(应用层API) 



Linux ：printf调用write，write调用sys_write(内核层API)，最后显示在频幕上。


Linux gcc编译器编译printf后调用write。
Window 的编译器则writefile

虽然C标准可以在不同系统运行，但有时候为了写出更多功能，需要调用系统函数。


#### I/O缓冲区
每一个FILE文件流都有一个缓冲区buffer，默认大小8192Byte。
