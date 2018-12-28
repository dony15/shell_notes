# 基础-bash库

[TOC]

### echo命令

用于字符串的输出,

字符串的引号修饰作用同变量

```shell
echo "字符串" #允许解析变量嵌入,允许转义
echo '字符串' #不允许解析变量嵌入,无法转义
echo 字符串   #字符串一次性输出,无法被引用(此处会被认为指令的一部分)
echo -e "字符串 \c" #开启转义,	\c 不换行
echo "巴拉巴拉信息" > myfile #将信息覆盖并写入到myfile文件中
echo "哔哩哔哩信息" >> myfile #将信息追加在文件myfile尾部,不会覆盖
```



### read命令

从标准输入中读取一行信息,存入指定变量中

```shell
read name #输入信息存入变量name中
read -p "请输入端口号" port  #-p 显示提示语句
read -t 30 username #-t 设置过期时间,30秒
```



### printf命令

与echo类似的输出命令

1. printf命令模仿c程序库(library)中的printf()程序
2. printf由POSIX标准定义,printf脚本移植性比echo好
3. printf使用引用文本或空格分割的参数,外面可以再printf中使用格式化字符串,定制宽度/左右对其等,需手动换行\n



##### 语法

`printf forma-string [args]`

##### 参数说明

1. format-string:字符串格式控制

2. args:参数列表



##### 演示列表

`%s %c %d %f`替代符

`%-10s`表示该字符串宽度为10个字符(-表示左对齐,没有则表示右对齐),不足空格补,超出全显示

`%-4.2f`中`-4`表示占据4个字符位置,左对齐,`.2`表示浮点数的小数部分位数为2 不足补0,超出隐藏



```shell
printf "Hello World \n" #普通输出,类似echo,但需要手动换位符
printf "%-10s %-8s %-4s \n" "姓名" "性别" "体重kg"  #此处引号内容为字符串格式化标准,对应右边数据
printf "%-10s %-8s %-4.2f \n" "大脚" "女"  48.236 #体重会被强制改为48.23输出

printf "%10s \n" a b c d e f #超出格式位数的参数会重用printf的格式控制.输出如下
         a 
         b 
         c 
         d 
         e 
         f 
printf "%10s %d" #如果没有参数,则字符串默认为null,数字默认0
```



### Shell输入输出命令

> 注意:
>
> 0是标准输入(STDIN)
>
> 1是标准输出(STDOUT)
>
> 2是标准错误输出(STDERR)

```shell
command > file #输出重定向到file,如echo "测试" > demo01.sh
command >> file	#将输出以追加的方式重定向到 file 如echo "测试" >> demo01.sh
command > /dev/null #将输出内容写入特殊的垃圾空间中丢弃
command > /dev/null 2>&1 #将输出内容写入特殊的垃圾空间中丢弃并屏蔽stdout和stderr
```

                                      Shell输入输出重定向指令笔记资料并不完整,以上只是常用操作