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



语法:

`printf forma-string [args]`

参数说明:

format-string:字符串格式控制

args:参数列表