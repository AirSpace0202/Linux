***thrift（rpc服务框架）***

远程函数调用，调用服务器内的函数，进行传输，进行服务器之间的交互



***thrift生成cpp文件***

```
thrift -r --gen cpp (thrift文件路径)
```



c++编译

1、编译

```
g++ -c <filename>.cpp
```

2、链接

```
g++ *.o -o main (-lthrift) (-pthread)
```

3、运行

```
./main
```



python3编译

```\
python3 <filename>.py
```





互斥锁mutex：保证共享数据操作的完整性，保证在任一时刻只能有一个线程访问对象。锁有两个操作。一个P操作(上锁)，一个V操作(解锁)，在项目中使用#include <mutex>进行实现

条件变量(condition_varialle)：和互斥锁搭配使用，用于多线程事件



***求字符串的md5值***：先获取服务器的用户名和密码，在终端输入md5sum，然后输入服务器密码，按ctrl + d得到一串字符，取前八位
