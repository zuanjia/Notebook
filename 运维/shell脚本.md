## 第一个shell脚本

打开文本编辑器(可以使用 vi/vim 命令来创建文件)，新建一个文件 test.sh，扩展名为 sh（sh代表shell），扩展名并不影响脚本执行，见名知意就好，如果你用 php 写 shell 脚本，扩展名就用 php 好了
```
#!/bin/bash
echo "Hello World !"
```
`#!`是一个约定的标记，它告诉系统这个脚本用什么解释器来执行，即使用哪一种shell

shell第一次执行需要权限
```
chmod +X 文件名称 #使用脚本具有执行权限
./text.sh
```
注意：一定要写成`./test.sh`,而不是`test.sh`运行其他二进制的程序也一样，直接写成test.sh，linux系统或去PATH里寻找又没叫test.sh的，而只有/bin,/sbin/usr/bin,/luser/sbin等在PATH里，你的当前目录通常不在PATH里，所以写成test.sh是会找不到命令的，要用`./test.sh`告诉系统，就在当前目录找

## 变量
```
your_name:"xiaotao"
```

## 注释
在字符串前面加一个`#`表示注释
## 运算符
lt(less than):小于
le(less than or equal to): 小于等于
gt(greater than): 大于
ge(greater than or equal to)：大于等于
eq(equal to): 大于
ne(not equal to): 不等于