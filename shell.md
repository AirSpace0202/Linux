shell是我们通过命令行与操作系统沟通的语言，Linux系统中一般默认使用bash。

新建一个bash文件命名为test.bash

```bash
#! /bin/bash

echo -e			#表示开启转义
$#				#表示传递参数个数
$?				#表示exit code
```

**运行方式：**

（1）使脚本具有可执行权限：chmod + x test.sh

（2）执行（当前路径）：./test.sh

**输出变量和删除变量**：

```bash
#输出变量
name=zjx
echo ${name}

#删除变量
name=zjx
unset name
echo ${name}     #输出空行
```

**变量类型：自定义变量（子进程不能访问）和环境变量（子进程可以访问）**

```bash
name=zjx
declare -x name  		#自定义变量改为环境变量
declare +x name			#环境变量改为自定义变量
```

**字符串（用双引号，单引号为原样输出）**

```bash
name=zjx
echo 'hello, ${name}' 			#输出hello, ${name}
echp "hello, ${name}"			#输出hello, zjx

echo ${#name}					#输出字符串长度3

echo ${name:0:3}				#输出从0开始的3个字符
```

**传参数**

```
#! /bin/bash

echo "文件名："$0
echo "第一个参数："$1
echo "第二个参数："$2
```

执行脚本（1）chmod +x test.sh    （2）./test.sh 1 2

输出：文件名：test.sh      第一个参数：1   第二个参数：2

**数组**

```bash
#! /bin/bash

array=(1 abc "def")			#用空格隔开

echo ${array[0]}			#输出1，读取数组元素

echo ${array[*]}			#读取整个数组

echo ${#array[*]}			#输出数组长度
```

**expr命令**

```bash
str="hello world!"

echo `expr length "$str"`			#输出字符串长度12
echo `expr index "$str" awd`		#输出7，下标从1开始，输出awd中随便一个字母在字符串中第一次出现的位置
echo `expr substr "$str" 2 3`		#输出ell，表示下标从1开始，下标为2开始的3个字符
```



在expr``中，* , ( , ) , > , < , <=, >= 要反斜杠 \ 转义



```bash
read -p "inout your name: " -t 10 name 		#读入name的值，等待10秒，-p后接提示，-t后接时间
```



**test命令**

```bash
test 2 -lt 3				#测试2小于3，返回值用exit code
echo $?						#输出0，0为真1为假

test -e filename			#测试文件是否存在
test -f filename			#测试是否为文件	
test -d filename			#测试是否为目录
test -r filename			#测试文件是否可读
test -w filename			#测试文件是否可写
test -x filename			#测试文件是否可执行
test -s filename			#测试文件是否为非空，1表示空，0表示非空
-eq 是否等于 				-ne 是否不等于
-lt 是否小于				-gt 是否大于
-le 是否小于等于				-ge 是否大于等于
```



**判断语句**

```bash
if [ condition ]
then
	语句1
	语句2
fi


if [ condition ]
then 
	语句1
elif
	语句2
fi




case $变量名称 in
	值1)
		语句1
		;;
	值2)
		语句2
		;;
	...
esac
```

**循环语句**

```bash
for i in val1 val2
do
	语句1
done

for ((i = 0; i < 10; i ++ ))
do
	echo ${i}
done

while [ condition ]
do
	语句1
done 
```

**函数**

```bash
func() {
    name=yxc
    echo "Hello $name"

    return 123
}

output=$(func)
ret=$?

echo "output = $output"
echo "return = $ret"

#output = Hello yxc
#return = 123

#local定义局部变量，只在函数中有用
```

**文件重定向**

```bash
#! /bin/bash

read a
read b
echo $(expr "$a" + "$b")

#创建input.txt 里面内容为3 4

#./test.sh < input.txt > output.txt  # 从input.txt中读取内容，将输出写入output.txt中，output.txt内容为7
```

**引入外部脚本**

```bash
创建test1.sh，内容为：
#! /bin/bash

name=yxc  # 定义变量name

然后创建test2.sh，内容为：
#! /bin/bash

source test1.sh # 或 . test1.sh

echo My name is: $name  # 可以使用test1.sh中的变量
```

