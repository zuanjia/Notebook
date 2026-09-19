## 第一个shell脚本

打开文本编辑器(可以使用 vi/vim 命令来创建文件)，新建一个文件 test.sh，扩展名为 sh（sh代表shell），扩展名并不影响脚本执行，见名知意就好，如果你用 php 写 shell 脚本，扩展名就用 php 好了
``` bash
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
```shell
your_name:"xiaotao"
```
注意：变量名和等号之间不能有空格
**只包含字符，数字和下划线**：变量名可以包含字母（大小写敏感），数字和下划线`_`,不能包含其他的特殊符号
**不能以数字开头**：变量名不能以数字开口，可以包含数字
**避免使用shell关键字**：不要使用shell关键字（if，then，else，fi，for，whlie等）作为变量名，以免引起混淆
**使用大写字母表示常量**：习惯上，常量的变量名通常使用大写字母，例如 `PI=3.14`
**避免使用特殊符号：** 尽量避免在变量名中使用特殊符号，因为它们可能与 Shell 的语法产生冲突
**避免使用空格：** 变量名中不应该包含空格，因为空格通常用于分隔命令和参数
```shell
RUNOOB="www.runoob.com"
LD_LIBRARY_PATH="/bin/"
_var="123"
var2="abc"
```
除了显式地直接赋值，还可以用语句给变量赋值，如：
```shell
for file in `ls /etc`
或
for file in $(ls /etc)
```
以上语句将 /etc 下目录的文件名循环出来

### 使用变量
使用一个定义过的变量，只要在变量名前面加美元符号即可，如：
```shell
your_name="qinjx"
echo $your_name
echo ${your_name}
```
变量名外面的花括号是可选的，加不加都行，加花括号是为了帮助解释器识别变量的边界，比如下面这种情况：
```shell
for skill in Ada Coffe Action Java; do
    echo "I am good at ${skill}Script"
done
```
如果不给skill变量加花括号，写成echo "I am good at $skillScript"，解释器就会把$skillScript当成一个变量（其值为空），代码执行结果就不是我们期望的样子了。
推荐给所有变量加上花括号，这是个好的编程习惯。
已定义的变量，可以被重新定义，如：
```shell
your_name="tom"
echo $your_name
your_name="alibaba"
echo $your_name
```
这样写是合法的，但注意，第二次赋值的时候不能写`$your_name="alibaba"`，使用变量的时候才加美元符($)

### 只读变量
使用 readonly 命令可以将变量定义为只读变量，只读变量的值不能被改变。
下面的例子尝试更改只读变量，结果报错：
```shell
#!/bin/bash

myUrl="https://www.google.com"
readonly myUrl
myUrl="https://www.runoob.com"
```
运行结果：
```shell
/bin/sh: NAME: This variable is read only.
```

### 删除变量
使用 `unset` 命令可以删除变量。语法：
```shell
unset variable_name
```
变量被删除后不能再次使用。unset 命令不能删除只读变量
```shell
#!/bin/sh

myUrl="https://www.runoob.com"
unset myUrl
echo $myUrl
```
以上实例执行将没有任何输出

### 变量类型
Shell 支持不同类型的变量，其中一些主要的类型包括：

#### 字符串变量
在 Shell中，变量通常被视为字符串。
你可以使用单引号 ' 或双引号 " 来定义字符串，例如：
```shell
my_string='Hello, World!'
或者
my_string="Hello, World!"
```

#### 整数变量
在一些Shell中，你可以使用 **declare** 或 **typeset** 命令来声明整数变量。
这样的变量只包含整数值，例如：
```shell
declare -i my_integer=42
```
这样的声明告诉 Shell 将 my_integer 视为整数，如果尝试将非整数值赋给它，Shell会尝试将其转换为整数

#### 数组变量
Shell 也支持数组，允许你在一个变量中存储多个值。
数组可以是整数索引数组或关联数组，以下是一个简单的整数索引数组的例子：
```shell
my_array=(1 2 3 4 5)
```
或者关联数组：
```shell
declare -A associative_array
associative_array["name"]="John"
associative_array["age"]=30
```

#### 环境变量
这些是由操作系统或用户设置的特殊变量，用于配置 Shell 的行为和影响其执行环境。
例如，PATH 变量包含了操作系统搜索可执行文件的路径：
```shell
echo $PATH
```
#### 特殊变量


## 注释
在字符串前面加一个`#`表示注释
## 运算符
lt(less than):小于
le(less than or equal to): 小于等于
gt(greater than): 大于
ge(greater than or equal to)：大于等于
eq(equal to): 大于
ne(not equal to): 不等于