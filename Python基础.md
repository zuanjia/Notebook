#Python基础

依旧第一个python程序

```py
print('hello world')
```

## print 函数的简单使用

```py
print('hello world!')
```

- print() 是python中自带的函数，作用在控制台中输出，括号的内容

- print() 主要在学习阶段使用，便于确认结果的正确性在实际工作的代码中基本不会使用print，会使用其他的内容代替（日志模块）
- print() 函数中是什么内容就会显示什么内容，里边的文字信息，可以使用单引号也可以使用双引号

## 注释

- 单行注释
  - 使用`#`号空格进行注释（单独一个`#`也可以）
  - 快捷键ctrl+/
- 多行注释
  - 多行注释中的内容可以换行书写
  - 多行注释可以使用3对双引号或者3对单引号，被3对引号包括的内容就是注释的内容
  - 三对引号的注释，一般写在文件的最开始部分，或者文件注释处（函数）
  - 

```py
# 这个是单行注释
"""
这个是多行
注释
"""
'''
这个也是多行
注释
'''
```

## python代码中三种波浪线和PEP8

- 红色
  - 红色波浪线是代码的错误，必须处理才能执行
- 灰色
  - 灰色波浪线，不会影响代码的正常执行
  - PEP8：是python代码的书写规范，如果不按照这规范书写，会给灰色波浪线提示，建议代码的书写按照PEP8的规范书写
  - 可以在书写完成之后，使用快捷键ctrl + alt + L来按照PEP的规范自动格式化代码
- 绿色
  - 绿色波浪线，不影响的正常执行，在引号中，认为你书写的内容不是一个单词，就会给你绿色提示

## 变量

- 变量注意实现：变量必须先定义（保存数据）后使用（取出数据）

### 定义变量

- 变量名=数据值

```python
# 例子
name = '张三'
```



### 使用变量

- 变量定义之后，想要是使用变量中的数据，直接使用变量名即可

### 变量名的命名规范

1. 必须有字母数字和下划线组成，并且不能以数字开头
2. 不能使用python中的关键字命名
3. 区分大小写
4. 建议命名方式
   - 驼峰命名法
     - 小驼峰：第一个单词小写其余的单词首字母大写`myName`
     - 大驼峰：每个单词首字母大写`MyName`
   - 下划线连接法：每个单词之间使用下滑线连接`my_name`

### 变量的类型

- 数字类型
  - 整型（int）
  - 浮点型（float）
  - 布尔类型（bool）
    - 真true，1
    - 假false，0，非零即真
  - 复数类型（3+4i）
- 非数字类型
  - 字符串：（str）使用引号引起来的就是字符串
  - 列表（list），[1,2,3,4]
  - 元组（tuple）（1，2，3，4，4）
  - 字典（dict）{'name':'小涛','age':19}

#### type()函数

可以获取变量的数据类型

type(变量)

## 类型转换

语法：

```python
变量 = 要转换为的类型（原数据）
```

1. 数据原来是什么类型
2. 你要转换什么类型

- ==int()==将其他类型转换称int类型
  1. 可以将float类型转换成整数
  2. 可以将整数类型的字符串转换为整型
- ==float()== 将其他类型转换成浮点类型
  1. 可以将`int`类型转换为浮点型float（3） ---> 3.0
  2. 可以将数字类型的字符串（整数类型和小数类型）转换为浮点型
- ==str()==
  1. 任何类型都可以使用`str()`将其转换成字符串

示例

```python
age = input('enter your age: ')
print(type(age),age)
# 类型转换
age1 = int(age)
print(type(age1),age1)
```



## 输入 input

获取用户键盘录入的内容

语法

```python
变量 = input('提示的信息')
```

1. 代码从上到下执行，遇到input函数后，会暂停执行，等待用户输入
2. 输入结束用回车结束
3. 无论你输入什么都类型都是str

## 输出 print

输出使用的函数是print（）函数，作用，将程序中数据或者结果打印到控制台（屏幕）

### 格式化输出

- % 格式化输出占位符号
  - `%d`占位，填充 整型数据`digit`
  - `%f`占位，填充，浮点数据`float`
  - `%s`占位，填充，字符串数据`string`

```python
name = '小涛'
age = 18
height = 1.75
print('我的名字是%s,年龄是%d，身高是%.2fm'%(name,age,height))
# 小数默认显示6位，如果想要指定显示小数后几位，%.nf，n是需要换成具体的整数数字，既保留小数的位置


# 补充
stuNum = 1 #学号
# 我的学号是000001
print('我的学号是%d'%stuNum)
#%0nd n需要换成具体的整数数字，表示整数一共占几位
print('我的学号是%06d'%stuNum)

num = 90 # 考试的及格率
print('考试的及格率%d%%'%num)
```

### f-string （f字符串的格式化方法）

1. f-string 格式化的方法，想要使用，python的版本>=3.6
2. 占位符位{}
3. 把需要填充的变量写在{}中

```python
print(f'我的名字是{name}，年龄是{age}')
```



### 字符串.format()

- 可以在任意版本中使用
- 在需要使用，变量的地方使用{}占位
- ‘{}，{}...’.format(变量，变量，...)

```python
print('我的名字是{},年龄是{},升高{:.3f}m,学号是{:06d}'.format(name,age,height,stuNum))
```

##运算数符

| 运算符 | 描述             | 示例     |
| ------ | ---------------- | -------- |
| +      | 加               | x+y=n    |
| -      | 减               | x-y=n    |
| *      | 乘               | x*y=n    |
| /      | 除               | x/y=n    |
| //     | 求商             | x//y=n   |
| %      | 求余             | x%y=n    |
| **     | 幂运算，指数运算 | 2**3 = 8 |

- 被除数/除数 = 商 ...余数

### 比较运算符

`> < >= <= ==`

 ### 逻辑运算符

- and 逻辑与 和 ，并且 and 连接两个条件，都必须位true，整体结果才为true，即一假为假
- or 逻辑或 或者 or连接的两个条件，只要一个为true就为true，即以真为真
- not 逻辑非 取反 not后面的条件是true变为false，false为true

### 赋值运算符

- 赋值运算符 = ，作用就是将等号右边的值保存到左边变量中
- 复合赋值运算符（将算术运算符和赋值运算符进行结合）
- += -= *= /= //= %=

## 判断

### if 的基本结构

基本语法

```python
if 判断条件:
	书写条件为真的执行代码
```

- if是一个关键字，后续的判断条件之间需要一个空格
- 判断条件后边需要一个冒号，不要少了
- 冒号之后回车代码需要缩进，在pycharm中会自动进行缩进，一般是4个空格或者是一个tab键
- 所有的if代码下方的缩进中书写的代码属于if语句的代码块，判断条件为true的时候会执行

### if else 结构

- 基本语法

```python
if 判断条件:
    书写条件为真的代码
else:
    书写条件不成立为假的代码
```

- else 是关键字，后边需要冒号
- 冒号之后回车，同样需要缩进
- 处于else代码下方的代码为else的代码块中
- if 和 else的代码块，只会执行其中一个
- else需要结合if使用

### if elif else 结构

语法：

```python
if 判断条件1:
    判断1成立执行这个段代码
elif: 判断条件2:
    判断条件2执行这个代码
else:
    以上条件都不成立执行代码
```

## debug 调试代码

1. 打断点
2. 右键debug代码
3. 单步执行代码

## 循环

### while

语法：

```python
while 判断条件:
    需要重复执行的代码
    改变循环的初始条件（计数器）
```

### for循环

- break：终止循环
- continue：终止当次循环

语句：

```python
for <variable> in <sequence>:
    <statements>
else:
    <statements>
```

示例：

```python
sites = ["Baidu", "Google","Runoob","Taobao"]
for site in sites:
    print(site)
```

## 容器（数据序列）

### 字符串

字符串的定义

1. 单引号定义
2. 双引号定义
3. 三引号定义

```python
my_str = """hello"""
my_str1 = '''world'''
```

- 字符串前边加上r“”原生字符串，字符串中的\不会作为转义字符

#### 切片

语法：

```python
字符串[start:end:step]
```

start是开始位置的下标（开始位置是零可以不写），end是结束位置的下标（注意，不能取到这个位置的字符。取到最后一个字符可以不写）step步长，等差薯类的差值，所取的字符下标之间的差值（如果是1可以不写）

#### 字符串的查找方法

语法：

```python
字符串.find(sub_str,start,end)
作用：在字符串中查找是否存在sub_str这样的字符串
sub_str：要查找的小的字符串
start：开始位置，从那个下标位置开始查找，一般不写，默认是0
end：结束位置，查找到那个下标结束，一般不写，默认是len()返回(代码执行之后会得到什么，如果有返回，就可以使用变量保存)
如果在字符中找到了sub_str，返回sub_str第一次出现的正数下标(sub_str中第一个字符在大字符串中的下标)
如果没有找到返回-1
```

#### 字符串的替换方法 replace

语法：

```python
字符串.replace(old_str,new_str,count)
```

- 将字符串中old_str替换为new_str
- old_str:被替换的内容
- new_str:替换为的内容
- count：替换的次数，一般不写，默认是全部替换
- 返回：替换之后的完整的字符串，注意：原来的字符串没有发生改变

#### 字符串的拆分

语法：

```yacas
字符串。split(sep，max_split) # 将字符串按照sep进行分割（拆分）
```

- sep，字符串按照什么进行拆分，默认是空白字符（空格，换行\n，tap键\t）
- max_split分割次数一般不写，全部分割
- 返回：将一个字符串拆分为多个，存到列表中
- 注意：如果sep不写，想要指定分割次数则需要按照如下方式使用

```python
字符串，split(max_split=n) # n是次数
```

#### 字符串的连接 join

```yacas
字符串，join(列表) # 括号中的内容主要是列表，可以是其他容器
# 作用：将字符串插入到列表中每个相邻的两个数据之间组成一个新的字符串
列表中的数据使用，逗号隔开的
注意点，列表中的数据必须都是字符串，否则会报错
```

### 列表基础

#### 列表定义

方法一：用[]定义，数据之间使用英语逗号，分隔

```python
name_list = []
name_list = ['zhangsan','lisi','wangwu']
```

方法二：通过类实例化方法定义

```python
data_list = list()
```

#### 查找列表中数据下标的方法

在字符串中使用的find方法查找下标的，不存在返回的是-1

在列表中没有find方法，想要查找数据的下标，使用index() 方法

语法:

```python
列表.index(数据，start,end)使用和find方法一样，同时在字符串中也有index方法
区别：返回，index（）方法，找到返回第一次出现的下标，没找到直接报错
```

#### 查找-判断是否存在

判断容器中某个数据是否存在可以使用in关键字

数据in容器   如果存在返回True ，如果不存在，返回False

#### 查找-统计出现的次数

统计出现次数，使用的是count()方法

列表，count(数据)	返回数据出现的次数

```python
str_list = [1,2,3,4,32,3,2,4,2]
print(str_list.index(2))
# print(str_list.index(5))
if 5 in str_list:
    print(str_list.index(5))
else:
    print('不存在5')

if str_list.count(5):
    print(str_list.index(5))
else:
    print('不存在5')
```

#### 添加数据的方法

- ==尾部添加（最常用）==

```python
列表.append(数据)  # 将数据添加列表的尾部
返回：返回的none(关键字，空)一般就不再使用变量来保存返回的内容想要查看添加的列表，需要打印的是列表
```

- 指定下标位置添加
  - 语法
  - 列表.insert(下标，数据)    再指定的下标位置添加数据，如果指定下标位置本来有数据，原数据会后移
  - 返回：返回的None(关键字，空)一般就不再使用变量来保存返回的内容想要查看添加的列表，需要打印的是列表
- 列表合并
  - 列表1.extend(列表2)    将列表2中的所有数据逐个添加的列表1的尾部
  - 返回：返回的None(关键字，空)一般就不再使用变量来保存返回的内容想要查看添加的列表，需要打印的是列表

#### 修改操作

语法:

列表[下标] = 数据

#### 列表删除操作

- 根据下标删除

```python
列表.pop(下标) # 删除指定下标位置的数据
下标不写，默认删除最后一个数据（常用）
书写存在的下标，删除对应位置的数据
返回：返回删除的数据
```

- 根据数据值删除

```python
列表.remove(数据值) # 根据数据值删除
返回：None
注意：如果要删除的数据不存在，会报错
```

- 清空数据（一般不用）

```python
列表.clear()
```

#### 倒置列表，列表反转    reverse

语法： 列表.reverse()

示例：

```python
num_list = [1,2,3,4]
mun_list.reverse()
print(num_list) # [4,3,2,1]
```

1. 另外的方法列表[::-1]使用切片的方法，会得到一个列表，原列表不会发生改变
2. 列表.reverse()直接修改原数据，返回None

#### 列表的复制  copy()

1. 使用切片：变量 = 列表[:]
2. 使用copy方法:变量 = 列表.copy()

#### 排序 sort()

- 功能：将列表指定规则进行数据排序
- 语法：列表.sort(key=None,reverse=false)

```python
val_list = [8,100,30,10,40,2]
val_list.sort(reverse=True)
print(val_list) # [100,40,30,10,8,2]
```

- 列表.sort() 按照升序排序，从小到大
- 列表.sort(reverse=True) 降序排序，从大到小

#### 列表嵌套

```python
my_str = [['小涛',1,1.2],['小涛爸爸',1,1.2]]
```

### 元组

相同点：

1. 元组中可以存放任意数据
2. 元组中可以存放任意多个数据

区别

1. 元组中的数据内容不能改变，列表中的可以改变的
2. 元组使用（），列表使用[]

应用：在函数的传参或者返回值中使用，保证数据不会被修改

**定义**

1. 使用类实例的方法
2. 直接使用()方法

**常用方法**

由于元组中的数据不能修改，所以只有查看的方法

1. 在元组中也可以使用，下标和切片获取数据
2. 在元组中存放index方法
3. 在元组中存放count方法
4. 在元组中可以使用in操作
5. 以上方法的使用，和列表中一样的

### 字典

1. 字典dict，字典中的数据是由键(key)值(value)对组成的(键表示数据的名字，值就是具体的数据)
2. 在字典中一组键值对是一个数据，多个键值对之间使用逗号隔开变量= {key:value,key:value,...}
3. 一个字典中的键值是唯一的，不能重复的，值可以是任意数据
4. 字典中的键，一般都是字符串，可以是数字，不能是列表

#### 定义

- 使用类实例化的方法

```python
my_dict = dict()
print(type(my_dict),my_dict) # <class 'dict'>
```

- 直接使用{}定义

```python
my_dict={}
print(type(my_dict),my_dict) # <class 'dict'>
my_dict1 = {"name":"小涛","age":18,"height":1.71}
```

#### 增加和修改操作

语法：

字典[键] = 数据值

1. 如果键已经存在，就是修改数据值
2. 如果键不存在，就是添加数据值

#### 删除

- 删除指定键值对

```python
del 字典[键]
字典.pop(键) # 键必须书写
```

- 清空

```python
字典.clear()
```

#### 查询-根据键获取对应的值

- 使用字典[键]

```python
字典[键]
```

1. 如果键存在返回键对应的数据值
2. 如果不存在会报错

- 使用字典.get(键)

```python
字典.get(键，数据值)
```

1. 数据值一般不写，默认是None

**返回**

1. 如果键存在返回键对应的数据值
2. 如果键不存在，返回的是括号中书写的数据值（None）

一般建议使用get方法

#### 字典的遍历

**字典的键进行遍历**

```python
for 变量 in 字典:
    print(变量)  # 变量就是字典的key，键
for 变量 in 字典.keys():  #  字典.keys() 可以获取字典中所有的键
    print(变量)
```



**字典的值进行遍历**

```python
for 变量 in 字典.values():  # 字典.values()可以获取字典中所有的值
    print(变量)
```



**字典的键值对进行遍历**

```python
# 变量1 就是 键， 变量2 就是键对应的值
for 变量1，变量2 in 字典.items(): # 字典.items()获取键值对
    print(变量1,变量2)
```

#### 容器部分 总结

```python
# 1.字符串，列表，元组支持加法运算
str1 = 'hello'+'world'  #'hello world'
list1 = [1,2] + [3,4] # [1,2,3,4]
tuple1 = (1,2)+(3,4) # (1,2,3,4)

# 2.字符串 列表 元组 支持 乘一个数字
'hello'*3 # ===> 'hello hello hello'
[1,2]* 3 # ===> [1,2,1,2,1,2]
(1,2)* 3 # ===> (1,2,1,2,1,2)

# 3.len() 在容器中都可以使用
# 4.in关键咋容器中都可以使用，注意，在字典中判断的是字典的键是否存在
```

## 函数

语法:

```python
def 函数名():
    函数代码
```

1. def是关键字，用来定义函数的 define的缩写
2. 函数名需要遵守标识符的规则

#### 函数的调用

```python
函数名()
```

1. 函数调用的时候会执行函数体中代码
2. 函数调用的代码，要写在函数体外面

#### 文档注释

1. 书写位置，在函数名的下方使用三对双引号进行的注释
2. 作用：告诉别人这个函数如果使用的

#### 函数大的嵌套调用

1. 函数定义不会执行函数体中的代码
2. 函数调用会执行函数体中的代码
3. 函数体中代码执行结果会回到函数被调用的地方继续向上执行

#### 函数的基础

**函数的参数**

1. 定义一个函数，my_sum，对两个数字进行求和计算

```python
def my_sum(a,b):
    """计算两数之和"""
    print(a + b)
a1 = int(input('enter first number'))
b1 = int(input('enter second number'))
my_sum(a1,b1)
```

**函数的返回值**

在函数中想要将一个值最为返回值返回，需要使用return关键字（只能在函数中使用）作用：

1. 将数据值作为返回值返回
2. 函数代码执行遇到return，或结束函数的执行

```python
def my_sum(a,b):
    """计算两数之和"""
    return a+b
a1 = int(input('enter first number'))
b1 = int(input('enter second number'))
print(my_sum(a1, b1))
```

**补充**

```python
def 函数名(): # 返回值None
    pass # 代码中没有return
def 函数名():
    return # return后面没有数据，返回值None
def 函数名():
    return xx # 返回值是xx
```

##变量进阶

#### 变量的引用

1. 在定义变量的时候 变量=数据值，python解释器会在内存中开辟两块空间
2. 变量和数据都有自己的空间
3. 日常简答理解，将数据保存到变量的内存中，本质是将数据的地址保存到变量对应的内存中
4. 变量中存储数据地址的行为就是引用（变量引用了数据的地址，简单来说就是变量中存储数据），存储的地址称为引用地址
5. 可以使用id()来获取变量中的引用地址（即数据的地址），如果两个变量的id()获取的引用地址一样，即代表着两个变量引用了同一个数据，是同一个数据

#### 可变类型和不可变类型

数据类型：int，float，bool，str，list，typle，dict，set

可变不可变是指：数据说在的内存允许修改，允许修改就是可变类型，不允许就是不可变类型（不可变类型=，变量引用的数据中的内容是否变化，会变化是可可变的，不会变化是不可变化的）

可变类型：列表list，字典dict，集合set

​	列表.append()

​	字典.pop（键）

不可变类型：int，float，bool，str，tuple

### 组包和拆包

组包(pack)：将多个数据值使用逗号连接，组成元组

拆包(unpack)：将容器中的数据值使用多个变量分别保存的过程，注意：变量的个数和容器中数据的个数要保持一致

```python
a=10
b=20
a,b = b,a
print(a,b) # 20,10
```

## 局部变量和全局变量

### 局部变量

局部变量：在函数内步（函数的缩进中）定义的变量，称为是局部变量

特点：

1. 局部变量只能在当前函数内部使用，不能再其他函数和外部使用
2. 在不同函数中，可以定义名字名字相同的局部变量，两者之间没有影响
3. 生存周期（生命函数，作用函数）-- >在哪能用

在函数被调用的时候，局部变量被创建，函数调用结束，局部变量被销毁（删除），不能使用所以函数中的局部变量的值，如果想要在函数外部使用，需要使用return关键字，将这个值进行返回

### 全局变量

**定义位置**：在函数外部定义的变量，称为是全局变量

特点：

1. 可以在任何函数中读取（获取）全局变量的值
2. 如何在函数中存在和全局变量名字想的局部变量，在函数中使用的是局部变量的值（就近）
3. 在函数内部想要修改全局变量的引用，需要添加global关键字，对变量进行声明为全局变量
4. 生命周期

代码执行的时候被创建，代码执行结束，被销毁（删除）

### 返回值-函数返回多个数据值

函数中想返回一个数据值，使用return关键之

将多个数据值组成容器进行返回一般是元组（组包）

```python
def calc(a,b):
    num = a+b
    num1 = a-b
    return num,num1
#写法1
result = calc(3,4)
print(result,result[0],result[1])
#写法2
x,y = calc(3,4)
print(x,y)
```

### 函数参数

#### 函数传参的方式

- 位置传参
  - 在函数调用的时候，按照形参的顺序，进行实参值传递给形参
- 关键之传参
  - 在函数调用的时候，指定数据值给到那个形参
- 混合使用
  1. 关键字传参必须写在位置传参的后面
  2. 不要给一个形参传递多个数据值

```python
def func(a,b,c):
    print(f'a:{a},b:{b},c:{c}')
#位置传参
func(1,2,3)
#关键字传参
func(a=1,b=2,c=3)
#混合使用
func(1,3,c=5)
# func(c=3,1,2) 关键字传参不能在前面
```

### 默认参数（缺省参数）

列表.pop() # 不写参数，删除最后一个

列表.sort(reverse=True)

1. 定义方式

   在函数定义的时候，给形参一个默认的数据值，这个形参这个变为默认参数，注意，默认参数的书写要放在普通参数的后面

2. 特点（好处）

   默认参数，在函数调用的时候，可以传递实参值，也可以不传递实参值如果传参，使用的就是传递的实参值，如果不传参，使用的就是默认值

```python
def show_info(name,sex='保密'):
    print(name,sex)
show_info('小涛')
show_info('小涛','男')
```

### 多值参数[可变参数/不定参数]

```python
print(1)
print(1,2)
print(1,2,3)
print(1,2,3,4)
```

当我们在书写函数的时候，不确定参数的具体个数时，可以使用，不定长参数

- 不定长位置参数(不定长元组参数)

  1. 在普通参数的前边加上一个*，这个阐述就变为不定长位置参数

  2. 特点：这个参数可以接收任意多个位置传参的数据

  3. 数据类型，形参的类型时元组

  4. 注意：不定长位置参数要写在普通的后面

  5. 一般写法不定长位置参数的名字args，即（*args） #arguments

     

- 不定长关键字参数(不定长字典参数)

  1. 书写，在普通参数的前边加上两个*，这个参数就变为不定长关键字参数
  2. 特点，这个形参可以接收任意多个关键字传参的数据
  3. 数据类型，形参的类型是字典
  4. 注意，不定长关键字参数，要写在所有参数的最后边
  5. 一般写法，不定长关键字参数的名字为kwargs，即(**kwargs)，keyword arguments

- 完整的参数顺序

```python
def 函数名(普通函数，*args,默认参数,**kwargs):
    pass
# 一般在使用的时候，使用1-2种，按照这个顺序挑选书写即可
```

```python
def func (*args, ** kwargs):
    print(type(args),args)
    print(type(kwargs),kwargs)
func()
func(1, 2, 3)
func(a=1, b=2, c=3)
func(1,2,3,a=4,b=5,c=6)

# <class 'tuple'> ()
# <class 'dict'> {}
# <class 'tuple'> (1, 2, 3)
# <class 'dict'> {}
# <class 'tuple'> ()
# <class 'dict'> {'a': 1, 'b': 2, 'c': 3}
# <class 'tuple'> (1, 2, 3)
# <class 'dict'> {'a': 4, 'b': 5, 'c': 6}
```

#### 补充

```python
def my_sum(*args,**kwargs):
    num=0
    for i in args:
        num+=i
    return num


my_list = [1,2,3,4]
my_dict = {'a':1,'b':2,'c':3,'d':4}
# 将字典和列表的数据使用my_sum函数进行求和，改如何传参问题
# my_sum(1,2,3,4)
# my_sum(a=1,b=2,c=3,d=4)
# 想要将列表（元组）中的数据分别作为位置参数，进行传参，需要对列表进行拆包操作
my_sum(*my_list) # my_list(1,2,3,4)
# 想要将字典中的数据，作为关键字传参，需要使用**对字典进行拆包
my_sum(**my_dict) # my_sum(a=1,b=2,c=3,d=4)
```



## print函数

- sep='',多个位置参数之间的间隔
- end='\n' 每一个print函数都会打印的内容结束符

```python
print(1,end=' ')
print(2,end=' ')
print(3)
print(1,2,3,4,5,6,sep='_')
print(1,2,3,4,5,6,sep='_*_')
# 1 2 3
# 1_2_3_4_5_6
# 1_*_2_*_3_*_4_*_5_*_6
```

### 匿名函数

匿名函数：就是使用lambda关键字定义的函数，一般称为使用def关键字定义的函数为，标准函数

匿名函数只能书写一行代码，匿名函数的返回不需要return，一行代码（表达式）的结果就是返回值

语法：

```python
lambda 参数：一行代码                             
```

- 匿名函数一般不需要我们主动的调用，一般作为函数的参数使用的      

- 我们在学习阶段为了查看匿名函数定义的式确定，可以调用

- 在定义的时候，将匿名函数的引用保存到一个变量中

  变量=lambda 参数：一行代码

- 使用变量进行调用

  变量()

```python
# 无参无返回值
def func1():
    print('hello world')
func1()
func11 = lambda:print('hello world')
func11()
# 无参有返回值
func22 = lambda:10
print(func22())
# 有参无返回值
my_sum = lambda a,b:print(a+b)
my_sum(1,2)
# 有参有返回值
my_sum1 = lambda a,b: a+b
print(my_sum1(1,2))
```

## 面向对象

### 类和对象

- 类
  - 抽象的概念，多个特征和行为相同或者相似事物的统称
  - 泛指的（指代多个，而不是具体的一个）
- 对象
  - 具体存在的一个事物，看得见摸得着的
  - 特指的（指代一个）

### 类的组成

1. 类名（给这多个事务起一个名字，在代码中满足大驼峰命名法（每个单词的首字母大写）
2. 属性（事物的特征，即有什么，一般文字中的名词）
3. 方法（事物的行为，即做什么事，一般是动词）

### 类的抽象（类的设计）（封装）

类的抽象其实就是找到类的类名属性和方法

需求：

- 小明今年18岁身高1.75每天早上跑完步会去吃东西
- 小美今年17岁身高1.65小美不跑步小美喜欢吃东西

类名：人类

属性：名字，年龄，身高

方法：跑步，吃

### 面向代码的步骤

1. 定义类，在定义类之前线设计类
2. 创建对象，使用第一步定义的类创建对象
3. 通过对象调用方法

### 面向对象基本代码的书写

1. 定义类

   先定义简单的类不包含属性，在python中定义类需要使用关键字class

   方法：方法的本质是在类中定义的函数，只不过第一个参数是self

   语法：

   ```python
   class 类名:
       def 方法名(self):
           pass
   ```

   

2. 创建对象

   创建对象是使用类名（）进行创建，即

   类名（） 创建一个对象，这个对象在后续不能使用

   创建的对象想要在后续的代码中据徐使用，需要使用一个变量，将这个对象保存起来

   变量 = 类名（） 这个变量中保存的是对象的地址，一般可以成为这个变量的对象

   一个类可以创建多个对象，只要出现类名（）就是创建一个对象每个对象的地址是不一样的

3. 调用方法

   对象.方法名（）

   列表.sort()

   列表.append()

###  self 的说明

```python
class Cat:
    def eat(self): # self会自动出现
        print('小猫吃鱼')
black_cat = Cat()
black_cat.eat()
```

1. 从函数的语法上讲，self是形参，就可以是任意的变量名，只不过我们习惯将这个形参写作self
2. self是普通的形参，但是在调用的时候么有传递实参值，原因是python解释器在执行代码大的时候自动的将调用这个方法的对象传递给了self，即self的本质是对象

### 对象的属性操作

#### 添加属性

对象.属性名= 属性值

- 内部添加

  ```python
  在内部方法中，self是对象，
  self.属性名= 属性值
  在类中添加属性一般写作__init__方法中
  ```

- 类外步添加

  对象.属性名=属性值 (一般不使用)

####获取属性

对象.属性名

- 类内部

  在内部方法中，self是对象

  self.属性名

- 类外部

  对象.属性名 （一般很少使用）

```python
# 外部获取属性
class Cat:
    def eat(self): # self会自动出现
        print(f'{self.name}吃鱼')
black_cat = Cat()
black_cat.name = '小蓝猫'
black_cat.eat()
```

### 魔法方法

python中有一类方法，以两个下滑线开头，两个下滑线结尾，并且在满足某个条件的情况下，会自动调用，这类方法称为魔法方法

学习：

1. 什么请款下自动调用
2. 有什么用，用在哪里
3. 书写的注意事项

#### `__init__`方法

1. 什么请款下自动调用

   创建对象之后自动调用

2. 有什么用，用在哪里

   给对象添加属性的（初始化方法，构造方法）

   某些代码，在每次创建对象之后，都要执行，就可以将这行代码写在`__init__`方法

3. 书写的注意事项

   不要写错了

```python
class Cat:
    def __init__(self):
        self.name = '蓝猫'
        self.age = 20
        print('我被调用了')
    def eat(self): # self会自动出现
        print(f'{self.name}吃鱼,年龄：{self.age}')
black_cat = Cat()
black_cat.eat()
blue_cat = Cat()
blue_cat.eat()


# 带参数的
class Cat:
    def __init__(self,name,age):
        self.name = name
        self.age = age
        print('我被调用了')
    def eat(self): # self会自动出现
        print(f'{self.name}吃鱼,年龄：{self.age}')
black_cat = Cat('黑猫',2)
black_cat.eat()
blue_cat = Cat('蓝猫',3)
blue_cat.e
```

#### `__str__方法`

1. 什么请款下自动调用

   使用print（对象）打印对象的时候或自动调用

2. 有什么用，用在哪里

   在这个方法中一般书写对象的属性信息，即打印对象的时候想要查看什么信息，在这个方法中进行定义的

   如果类中没有定义`__str__`方法，print(对象)，默认输出对象的引用地址

3. 书写的注意事项

   这个方法必须返回一个字符串

```python
class Cat:
    def __init__(self,name,age):
        self.name = name
        self.age = age
        print('我被调用了')
    def __str__(self):
        # 方法必须返回一个字符串，只要是字符串就行
        return f'小猫名字是：{self.name},年纪是{self.age}'
black_cat = Cat('黑猫',2)
print(black_cat)
blue_cat = Cat('蓝猫',3)
print(blue_cat)


# 我被调用了
#小猫名字是：黑猫,年纪是2
#我被调用了
#小猫名字是：蓝猫,年纪是3
```

#### `__del__`方法

`__init__`方法，创建对象之后，会自动调用（构造方法）

`__del__`方法，对象被删除销毁时，自动调用的（遗言，处理后事）（构造方法）

1. 调用场景，程序代码运行结束，所有对象都被销毁
2. 调用场景，直接使用del删除对象（如果对象有多个名字（多个对象引用一个对象），需要把所有的对象都删除才行）

```python
class demo:
    def __init__(self,name):
        print('__init__')
        self.name = name
    def __del__(self):
        print(f'{self.name} 没了')

a = demo('a')
b= demo('b')
del a
print('程序结束')

# __init__
# __init__
# a 没了
# 程序结束
# b 没了
```

```python
class person:
    def __init__(self,name,weight):
        self.name = name
        self.weight = weight
    def __str__(self):
        return f'{self.name} 体重 {self.weight}'
    def run(self):
        print(f'{self.name}跑了5公里')
        self.weight -= 0.5
    def eat(self):
        print(f'吃一炖好的')
        self.weight += 1
xt = person('小涛',500)
xt.run()
print(xt)
xt.eat()
print(xt)
```

### 私有和公有

1. 访问控制权限分为两种，共有权限，私有权限

   1. 共有权限：

      直接书写的方法和属性，都是共有的

      共有的方法和属性，可以在任意地方访问和使用

   2. 私有权限

      在类内部，属性名或者方法名前边加上两个下滑线，这个属性或者方法就变为私有的

      私有的方法和属性，只能在当前类的内部使用

2. 什么使用定义私有

   1. 某个属性或者方法，不想再外部类被访问和使用，就将其定义为私有即可

```python
class Person:
    def __init__(self,name,age):
        self.name = name
        # 私有的本质，是python解释器执行代码，发现属性名或方法名前有两个__，会将这个重命名
        # 会键这这个名字前边驾驶_类名前缀，即self.__age ==> self._Person__age
        self.__age = age
    def __str__(self):
        return f'名字{self.name} | 年龄{self.__age}'

xiaotao = Person('小涛',22)
print(xiaotao.__dict__)
xiaotao.age = 30 # 这个不是修改私有属性，是添加了一个共有属性__age
print(xiaotao.__dict__)
print(xiaotao)
print(xiaotao._Person__age)


# {'name': '小涛', '_Person__age': 22}
# {'name': '小涛', '_Person__age': 22, 'age': 30}
# 名字小涛 | 年龄22
# 22
```



### 继承

==语法==：

```python
class A:
    pass
class B(A): # 类B，继承了类A
    pass

```

术语：

1. A类，称为父类（基类）
2. B类，称为是子类（派生类）

**单继承**：一个类只继承一个父类，称为单继承

继承之后的特点：

​	子类（B）继承父类（A）之后，子类的对象可以直接使用父类中定义的共有属性和方法

```python
class Animal:
    def eat(self):
        print('正在吃东西...')
class Dog(Animal):
    def brak(self):
        print('正在叫...')
class BlueDog(Dog):
    pass

dog1 = Dog()
dog1.eat()
dog1.brak()
dog2 = BlueDog()
dog2.eat()
dog2.brak()

# 正在吃东西...
# 正在叫...
# 正在吃东西...
# 正在叫...
```

- 结论:

  python中对象.方法（）调用

  1. 现在自己的类中的去找有没有这个方法，如果有，就直接调用
  2. 如果没有主父类中查找，如果有就直接调用
  3. 如果没有就去父类的父类中查找如果有就直接调用
  4. ...
  5. 如果没有object类中有直接调用，如果没有代码报错

### 重写

1. 覆盖（父类中功能完全被抛弃，不要，重写书写）
2. 扩展（父类中功能还调用，只是添加一些新的功能）（使用较多）

```python
class Animal:
    def eat(self):
        print('正在吃东西...')
class Dog(Animal):
    def brak(self):
        print('正在叫...')
class BlueDog(Dog):
    def brak(self):
        print('嗷嗷叫...')
    pass

dog1 = Dog()
dog1.eat()
dog1.brak()
dog2 = BlueDog()
dog2.eat()
dog2.brak()

# 正在吃东西...
# 正在叫...
# 正在吃东西...
# 嗷嗷叫...
```



#### 覆盖

1. 直接再子类中定义和父类中名字相同的方法
2. 直接在方法中写新的代码

#### 扩展

1. 直接在子类中，定义和父类中名字相同的方法
2. 在合适的地方调用，父类中方法 super().方法()
3. 书写添加的新功能

```python
class Animal:
    def eat(self):
        print('正在吃东西...')
class Dog(Animal):
    def brak(self):
        print('正在叫...')
class BlueDog(Dog):
    def brak(self):
        print('嗷嗷叫...')
        # 调用父类中的代码
        super().brak()
        print('嗷嗷叫...')
    pass

dog1 = Dog()
dog1.eat()
dog1.brak()
dog2 = BlueDog()
dog2.eat()
dog2.brak()

# 正在吃东西...
# 正在叫...
# 正在吃东西...
# 嗷嗷叫...
# 正在叫...
# 嗷嗷叫...
```



### 多态

1. 是一种写代码，调用的一种技巧
2. 同一个方法，传入不同的对象，执行得到不同得结果，这种现象称为是多态
3. 多态可以增加代码得灵活度

那个对象调用方法，就去自己得类中查找这个方法，找不到去父类中找

### 属性和方法

python中一切皆对象

即使用class定义得类也是一个对象

### 对象的划分

#### 实例对象（实例）

1. 通过类名（）创建的对象，我们称为实例对象，简称实例
2. 创建对象的过程称为是类的实例化
3. 我们平时所说的对象就是指实例对象（实例）
4. 每个实例对象，都有自己的内存空间，在自己的内容空间中保存自己的属性（实例属性）

#### 类对象（类）

1. 类对象就是类，或者可以认为是类名，
2. 类对象是Python解释器在执行代码的过程中创建的
3. 类对象的作用：1.使用类对象创建实例类名（），2.类对象也有自己的内存空间，可以保存一些属性值信息（类属性）
4. 在一个代码中，一个类只有一份内存空间

### 属性的划分

实例属性

- 概念：是==实例对象==具有的属性

- 定义和使用

  在init方法中，使用self.属性名 = 属性值 定义

  在方法中是使用self.属性名来获取（调用）

- 内存

  实例属性，在每个实例中多存在一份

- 使用时机

  1. 基本上99%就是实例属性，即通过self去定义
  2. 在多个对象，来判断这个值是不是都是一样的，如果都是一样的，同时变化，则一般定义为类属性，否则定义为，实例属性

类属性

- 概念：是==类对象==具有的属性

- 定义和使用

  在类内部，方法外部，直接定义的变量，就是类属性

  使用：类对象.属性名=属性值or类名.属性名 = 属性值

  类对象.属性名 or 类名.属性名

- 内存

  只有类对象中存在一份

#### 方法的划分

方法，使用def关键字定义在类中的函数就是方法

**实例方法（最常用）**

- 定义

  ```python
  # 在类中直接定义的方法就是实例方法
  class Demo:
      def func(self):
          pass
  ```

- 定义时机（什么时候用）

  如果在方法中需要使用实例属性（即需要使用self），则这个方法必须定义为实例方法

- 调用

  对象.方法名 # 不需要给self传参

**类方法（会用）**

- 定义

  ```python
  # 在方法名字的上方法书写@classmethod 装饰器（使用@classmethod 装饰的方法）
  class Demo:
      @classmethod
      def func(cls): # 参数一般写作cls，表示的是类对象（即类名）class
          pass
  ```

- 定义时机（什么时候用）

  1. 前提，方法中不需要使用实例属性（即self）
  2. 用到了类属性，可以将这个方法定义为类方法（也可以定义为实例方法）

- 调用

  调用类对象调用

  类名.方法名（） # 也不需要给cls传参，python解释器自动传递

  通过实例对象调用

  实例.方法名()  # 也不需要给cls传参，python解释器自动传递

**静态方法（基本不用）**

- 定义

  ```python
  # 在方法名字的商法书写@staticmethod装饰器（使用@staticmethod装饰的方法）
  class Demo:
      @staticmethod
      def func(): # 一般没有参数
          pass
  ```

- 定义时机（什么时候用）

  1. 提前，方法中不需要使用实例属性（即self）
  2. 也不使用类属性，可以将这个方法定义为静态方法

1. 调用
2. 调用类对象调用
3. 类名.方法名（） # 也不需要给cls传参，python解释器自动传递
4. 通过实例对象调用
5. 实例.方法名()  # 也不需要给cls传参，python解释器自动传递

## 文件操作

### 普通文件的操作

- 文本文件
  - 能够使用记事本软件打开（能够使用记事本转换为文字）
  - `txt,md,py,html,css,js,json`
- 二进制文件
  - 不能使用记事本软件打开
  - `exe,mp3,mp4,jpg,png`

### 文件操作步骤

1. 打开文件
2. 读或写文件
3. 关闭文件

#### 打开文件

打开文件：将文件从磁盘（硬盘）中读取到内存总

语法：

open(file,mode='r',encoding=None,errors=None,newline=None,closefd=True): # known special case of open

常用的：

open(file,mode='r',encoding=None)

参数：

file:是要打开的文件，类型时字符串，文件的路径可以时相对路径，也可以时绝对路径（从根目录开始书写的路径）建议使用相对路径（相对于当前代码文件所在的路径,./../）

mode:默认参数，表示是打开文件的方式

- r；read只读打开
- w:write只写打开
- a:append追加打开，在文件的末尾写入内容

encoding:编码方式（文字和二进制如何进行转换的）

- gbk：将一个汉字转换为2个二进制
- utf-8:常用，将一个汉字转换为3个字节的二进制

返回值：返回的是文件对象，后续对文件的操作，都需要这个对象

#### 读或者写文件

**写文件**：向文件中写入指定的内容

提前：文件的开发方式是w或者a

文件对象.write('写入文件的内容')

返回值：写入文件的字符数，一般不关注

- 注意 (w 打开文件）：
  - 文件不存在，会直接创建文件
  - 文件存在，会覆盖原文件（将原文件内容清空）

**读文件**：将文件的内容读取出来

前提：问及啊的打开方式需要时r

文件对象.read(n)

参数n表示读取多少个字符，一般不写，表示读取全部内容

返回值：读取到的文件内容，类型字符串

#### 关闭文件

关闭文件：将文件占用的资源进行清理，同时会保存文件，文件关闭之后，这个文件对象就不能使用了

文件对象，close()

#### 使用with open打开文件

好处： with open（）打开文件不需要直接书写关闭文件的代码，会自动进行关闭

示例

```python
with open (file, mode ,encoding='utf-8') as 变量:
    # 在缩进中去读取或者写入文件
# 缩进中的代码执行结束，出缩进之后，文件会自动关闭
```

```python
with open('a.txt','a',encoding='utf-8') as f:
    f.write('I am name XiaoTao')
```

#### 按行读取文件内容

语法：

文件对象.readline()

```python
# with open('a.txt',encoding='utf-8') as f:
#     a=f.readline()
#     print(a)
#     print(f.readline())

# with open('a.txt','r',encoding='utf-8') as f:
#     for i in f:
#         print(i,end='')


# # read()和readline()读到文件末尾，返回一个空字符串
# with open('a.txt','r',encoding='utf-8') as f:
#     while True:
#         buf = f.readline()
#         if len(buf) == 0:
#             break
#         else:
#             print(buf,end='')

# 在容器中，容器为空，即容器中的数据的个数为0，表示false，其余情况都是True
with open('a.txt','r',encoding='utf-8') as f:
    while True:
        buf = f.readline()
        if buf:
            print(buf, end='')
        else:
            break
```



### json文件的操作（重点）

#### json文件的处理

- json基于文本呢，独立于语言的轻量级的数据交换格式
  - 基于文本是一个文本文件
  - 轻量级，相同的数据和其他格式相比占用的大小比较小
  - 独立语言，不是某个语言特有的，每种编程语言都可以使用
  - 数据交换格式，后端程序员给前端的数据（json,html,xml）

**json文件的语法**

1. json文件的后缀是.json
2. json中主要的数据为对象({}类似python中字典)和数组（[]，类似python中的列表），对象和数组可以相互嵌套
3. 一个json文件是一个对象或者数组（即json我文件的最外层要么时一个{}，要么是一个数组[]）
4. json中的对象是有键值对组成的，每个数据之间使用逗号隔开，但是最后一个数据后边不能写逗号
5. json中的字符串，必须使用双引号
6. json中的其他数据类型
   - 数据类型---> int float
   - string字符串===>str
   - 波尔类型true，false===>True，false
   - null==>None

#### json文件的书写

我叫小涛，今年18岁吗，性别男，爱好：听歌，游戏，吃饭，睡觉，打豆豆，居住地为中国，城市湖南

```json
{
  "name": "小涛",
  "age": 18,
  "sex": true,
  "like": ["听歌","游戏","购物","睡觉","吃饭","打豆豆"],
  "address": {
    "country": "中国",
    "city": "湖南"
  }
}
```

#### 读取json文件

1. 导包 import json

2. 读打开文件

3. 读文件

   json.load(文件对象)

   返回的是字典（文件中是对象）或者列表（文件中是数组）

```python
# 导入json
# 读打开文件
import json

with open('info.json',encoding='utf-8') as f:
    info = json.load(f)
    print(info)
    print(info.get('name'))
    print(info.get('age'))
    print(info.get('like')[1])
    print(info.get('address').get('city'))
    
# {'name': '小涛', 'age': 18, 'sex': True, 'like': ['听歌', '游戏', '购物', '睡觉', '吃饭', '打豆豆'], 'address': {'country': '中国', 'city': '湖南'}}
# 小涛
# 18
# 游戏
# 湖南
```

多个数据：

```json
[
  {
    "name": "小涛",
    "age": 18,
    "sex": true,
    "like": [
      "听歌",
      "游戏",
      "购物",
      "睡觉",
      "吃饭",
      "打豆豆"
    ],
    "address": {
      "country": "中国",
      "city": "湖南"
    }
  },
  {
    "name": "小涛他爸爸",
    "age": 18,
    "sex": true,
    "like": [
      "购物",
      "打豆豆"
    ],
    "address": {
      "country": "中国",
      "city": "湖南"
    }
  }
]
```

代码部分:

```python
with open('info2.json', encoding='utf-8') as f:
    info_list = json.load(f)
    for infos in info_list:
        print(infos.get('name'), infos.get('age'), infos.get('address').get('city'), infos.get('like')[1])

# 小涛 18 湖南 游戏
# 小涛他爸爸 18 湖南 打豆豆
```

将数据变成列表元组

数据:

```json
[
  {
    "desc": "正确的用户名密码",
    "username": "admin",
    "password": "123456",
    "expect": "登录成功"
  },
  {
    "desc": "错误的用户名",
    "username": "root",
    "password": "123456",
    "expect": "登录失败"
  },
  {
    "desc": "错误的密码",
    "username": "admin",
    "password": "1212121",
    "expect": "登录失败"
  }
]
```

代码：

```python
import json

with open('info3.json',encoding='utf-8') as f:
    data = json.load(f)
    # print(data)
    new_data = []
    for item in data:
        # print((item.get('username'), item.get('password'), item.get('expect')))
        new_data.append((item.get('username'), item.get('password'), item.get('expect')))
    print(new_data)
```

#### json的写入

步骤：

1. 导包

2. 写入（w）方法打开文件

3. 写入

   json.dump(python 中的数据类型，文件对象)

   ```python
   import json
   
   my_list= [('admin', '123456', '登录成功'), ('root', '123456', '登录失败'), ('admin', '1212121', '登录失败')]
   with open('info4.json','w',encoding='utf-8') as f:
       # json.dump(my_list,f) # 基础写入
       # 中文不要显示ASCII
       # json.dump(my_list,f,ensure_ascii=False,indent=4)
       # 显示缩进
       json.dump(my_list,f,ensure_ascii=False,indent=4)
       
       
   # [
   #     [
   #         "admin",
   #         "123456",
   #         "登录成功"
   #     ],
   #     [
   #         "root",
   #         "123456",
   #         "登录失败"
   #     ],
   #     [
   #         "admin",
   #         "1212121",
   #         "登录失败"
   #     ]
   # ]
   ```

   

## 异常处理（程序代码运行时的错误）

程序停止执行并且提示错误显示，抛出异常（raise关键字）

### 捕获异常

基本语法：

```python
try:
    书写可能发生异常的代码
except: # 任何类型的异常都能捕获
        发生了异常执行的代码
        
try:
    书写可能发生异常的代码
except 异常类型: # 只能捕获指定异常，如果不是这个异常还是会报错
        发生了异常执行的代码
```

```python
# num = input('enter number:')
# try:
#     num = int(num)
#     print(num)
# except:
#     print('请 enter number:')


# 指定捕获的异常
num = input('enter number')
try:
    num = int(num)
    print(num)
    a = 10 / num
    print(a)
except ValueError :
    print('请输入数字')
```

#### 捕获多个指定类型的异常

可以针对不同的异常错误，进行单独的代码处理

```python
try:
    书写可能发生异常的代码
except 异常类型: # 只能捕获指定异常，如果不是这个异常还是会报错
        发生了异常执行的代码
except 异常类型2: # 只能捕获指定异常，如果不是这个异常还是会报错
        发生了异常执行的代码
...
```

```python
# 指定捕获的异常
num = input('enter number')
try:
    num = int(num)
    print(num)
    a = 10 / num
    print(a)
except ValueError as e:
    print(f'请输入数字{e}')
except ZeroDivisionError:
    print('除数不能为零')
```

#### 异常捕获的完整版本

```python
try:
    可能发生异常的代码
except 异常类型1: 
    发生异常类型1执行的代码
    # Exception是常见异常类的父类，这里书写Exception，可以捕获常见的异常，as变量这个变量是一个异常类的对象print（变量）可以打赢异常信息
except Exception as 变量:
    发生其他错误类型的异常，指定的代码
else: 
    没有发生异常会执行的代码
finally:
    不管发没发生异常都活执行的代码
```

```python
num = input('enter number')
try:
    num = int(num)
    print(num)
    a = 10 / num
    print(a)
except ValueError as e:
    print(f'请输入数字{e}')
except ZeroDivisionError:
    print('除数不能为零')
else:
    print('没发生异常我会执行')
finally:
    print('不管发没发生我都执行')
    
    
# enter number1
# 1
# 10.0
# 没发生异常我会执行
# 不管发没发生我都执行
```

### 异常传递

在函数嵌套中调用的过程中，被调用的函数，发生了异常，如果没有捕获，会将这个异常想外层传递....如果传递到最外层还没捕获，才报错

### 抛出异常

## 模块和包

1. python源代码文件就是一个模块
2. 模块中定义的变量，函数，类都可以让别人使用，同样，可以使用别人定义的（好处：别人定义好的不需要我们再次书写，直接使用即可）
3. 想要使用别人的模块中内容工具（变量，类，函数），必须先导入模块才可以
4. 我们自己写的代码，想要作为模块使用，代码的名字需要满足表示符的规则（有数字，字母下划线组成不能有数字开头）

### 导入模块的语法

**方法一**

```python
import 模块名
# 使用模块中的内容
模块名.工具名
# 举例
import random 
import json
random.randint(a,b)
json.load()
json.dump()
```

**方法二**

```python
from 模块名 import 工具名
# 使用
工具名 # 如果是函数和类需要加括号
# 举例
from random import randint
from json import load, dump
randint(a,b)
load()
dump()
```

**方式三** 

```python
from 模块名 import * # 将模块中所有的内容都导入
from random import *
from json import *
randint(a,b)
dump()
load()
```

代码：

```python
# 方法一
# import random
# for i in range(20):
#     print(random.randint(1,10))

# 方法二
# from random import randint
# 
# for i in range(20):
#     print(randint(1,10))
    
## 方法三
from random import *

for i in range(20):
    print(randint(1,10))
```

对于导入的模块和工具可以使用as关键字给其起别名

注意：如果起别名，原来的名字就不能用了，只能使用别名

### 模块的查找顺序

在导入模块的时候会先在当前目录中找模块，如果找到，就直接使用如果没有找到汇聚系统的目录进行查找，找到，直接使用没有找到，报错

注意点：

定义代码文件的时候，你的代码名字不能和你要导入的模块名字相同，

### `__name__`的作用

1. 每个代码文件都是一个模块
2. 在导入模块的时候，会执行模块中的代码
3. `__name__`变量
   1. 是python解释器自动维护的变量
   2. 如果代码是直接运行，值是`__name__`
   3. 如果代码是导入执行，值是模块名（即代码文件名）

```python
def add(a,b):
    return a+b

if __name__ == '__main__':
    print(add(1,2))
    print('tools',__name__)
    
# 代码2
import tools

print(tools.add(1,2))
```

### 包（package）

在python中，包是一个目录，只不过在这个目录存在一个文件

`__init__.py`

将功能香精或者像是的代码放在一起的

----------

在python中使用的时候，不需要可以是区分包还是模块，使用方法是一样的

random 模块（单个文件代码）

json 包(目录)

## unittest 框架

### unitTest框架的基本使用方法

### 介绍

- 框架

  说明：

  1. 框架英语单词framework
  2. 为解决一类事情的功能集合
  3. 需要按照框架的规定（套路）去书写代码

- 什么是unitTest框架

  unitTest是python自带的一个单元测试框架，用它来左单元测试框架

  ----

  自带的框架：不需要单外安装。只要安装了python就可以使用

  第三方框架：想要使用需要先安装后使用（pytest）

  ----

  单元测试框架：主要用来做单元测试，一般单元测试是开发做的

  对于测试来说，unittest框架的作用是自动化脚本（用例代码）执行框架（使用unittest框架来管理运行多个测试用例）

  - 为什么使用unitTest框架
    1. 能勾组织多个用例去执行
    2. 提供丰富的断言方法
    3. 能够生成测试报告

#### unitTest核心要素（unitest组成）

1. TestCase（测试用例）（最核心的内容）
   1. 注意：这个测试用例是unittest框架的组成部分，不是手工和自动化中我们所说的用例（Test Case）
   2. 主要作用：每个TestCase（测试用例）都是一个代码文件，在这个代码文件中，来书写真正的用例代码
2. TestSuite（测试套件）
   1. 用来管理组装（打包）多个TestCase（测试用例）的
3. TestRunner（测试执行，测试运行）
   1. 用来执行Test Suite（测试套件）的
4. TestLoader（测试加载）
   1. 功能是对Testsuite（测试套件）功能的补充，管理组装（打包）多个TestCase（测试用例）的
5. Fixture（测试夹具）
   1. 书写在TestCase（测试用例）代码中，是一个代码结构，可以在每个方法执行前后都会执行的内容
   2. 举例：
      1. 登录的测试用例，每个用例中重复的代码可以写在fixture代码结构中，只写一遍，但每次用例方法的执行都绘制执行Fixture中的代码
      2. 打开浏览器
      3. 输入网址



#### TestCase（测试用例）

1. 是一个代码文件，在代码文件中来书写真正的用例代码
2. 代码文件的名字必须按照表示的规则来书写（可以浙江代码的作用写在文件的开头用注释说明）

**步骤**

1. 导包（unittest)
2. 自定义测试类
3. 在测试类中书写测试方法
4. 执行用例

**代码**

```python
import unittest

# 自定义测试类,需要继承unittest模块中TestCase类即可
class TestDome(unittest.TestCase):
    # 书写测试方法，即测试代码，目前没有真正的用例代码，使用print代替
    # 书写要求，测试方法必须以test_开头（本质是以test开头）
    def test_method1(self):
        print('测试方法1')
    def test_method2(self):
        print('测试方法2')

# 执行用例（方法）
# 将光标放在，类名的后面运行，会执行类中的所有的测试方法
# 将光标放在方法名后面运行只会执行当前方法
```

### TestSuite&TestRunner

Test Suite（测试套件）：管理打包组装TestCalse（测试用例）文件的

TestRunner（测试执行）：执行Test Suite（套件）

步骤：

1. 自定义测试类,需要继承unittest模块中TestCase类即可
2. 书写要求，测试方法必须以test_开头（本质是以test开头）
3. 书写测试方法，即测试代码，目前没有真正的用例代码，使用print代替
4. 执行用例（方法）
5. 将光标放在，类名的后面运行，会执行类中的所有的测试方法
6. 将光标放在方法名后面运行只会执行当前方法

代码：

```python
TestSuite（测试套件）：是用来管理多个TestCase（测试用例）的，先创建多个TestCase（测试用例）文件
```

```python
# 1. 导包（unittest）
import unittest

from ceshi1 import TestDome1
from ceshi2 import TestDome2

# 2. 实例化（创建对象）套件对象
suite = unittest.TestSuite()
# 3. 使用套件对象添加用例方法
suite.addTest(TestDome1('test_method1'))
suite.addTest(TestDome1('test_method2'))
suite.addTest(TestDome2('test_method1'))
suite.addTest(TestDome2('test_method2'))
# 4. 实例化运行对象
runner = unittest.TextTestRunner()
# 5. 使用运行对象去执行套件对象
runner.run(suite)
```

```python
# 方法二
import unittest

from ceshi1 import TestDome1
from ceshi2 import TestDome2

suite = unittest.TestSuite()
loader = unittest.TestLoader()
suite.addTest(loader.loadTestsFromTestCase(TestDome1))
suite.addTest(loader.loadTestsFromTestCase(TestDome2))
runner = unittest.TextTestRunner()
runner.run(suite)
```

### TestLoader（测试加载）

1. 导包
2. 实例化测试加载对象并添加用例 --->得到的是suite对象
3. 实例化运行对象
4. 运行对象执行套件对象

代码:

```python
import unittest

suite = unittest.TestLoader().discover('./cases','ce*.py')
unittest.TextTestRunner().run(suite)
```

### Fixture(测试夹具)

在某个特定的情况下会自动执行

#### 方法级别

在每个测试方法执行前后都会自动调用的结构

```python
def setUp(self):
    每个测试方法执行之前都会执行
    pass
def tearDown(self):
    每个测试方法执行之后都会执行
    pass
```

#### 类级别

在每个测试类中多有方法执行前后都会自动调用的结构（在整个类中执行之前之后个一次）

```python
# 类级别的Fixture方法，是一个类方法
# 类中所有方法之前
@classmethod
def setUpClass(cls):
    pass
# 类中所有方法之后
@classmethod
def tearDownClass(cls):
    pass
```

#### 模块级别

模块：代码文件

在每个代码文件执行前后执行的代码结构

```python
# 模块级别的需要写在类的外边直接定义函数即可
# 代码文件之前
def setUpModule():
    pass
# 代码文件之后
def tearDownModule():
    pass
```

方法级别和类级别的前后的方法不需要同时出现，根据用例代码的需要自行的选择使用

案例

1. 打开浏览器（整个测试过程中就关闭一次浏览器）类级别 
2. 输入网址（每个测试方法都需一次）方法级别
3. 输入用户名密码验证吗点击登录（不同的测试数据）
4. 关闭当前页面（每个测试方法都需一次）方法级别
5. 关闭浏览器（整个测试过程中就关闭一次浏览器）类级别

```python
import unittest


class TestLogin(unittest.TestCase):
    def setUp(self):
        """每个方法都会调用"""
        print('输入网址')
    def tearDown(self):
        """每个方法结束都会调用"""
        print('关闭网页')

    @classmethod
    def setUpClass(cls):
        print('打开浏览器')

    @classmethod
    def tearDownClass(cls):
        print('关闭浏览器')
    def test_1(self):
        print('测试方法1')
    def test_2(self):
        print('测试方法2')
```



#### 常见错误

**问题一**

1. 代码文件的名字数字开头

2. 代码文件名字中有空格

3. 代码文件名字有中文

4. 其他的特殊符号

   （数字，字母，下划线组成，不能以数值开头

**问题二**

- 右键运行没有unittests for 的提示，出现的问题
- 解决方案：
  1. 从新新建一个代码文件，将写好的代码复制进去
  2. 删除已有的运行方式

**问题三** 

- 没有找到用例
- 测试方法中不是以test_开头，或者单词写错了

### 断言的使用方法

在unittest中使用断言，都需要通过self.断言方法来实验

#### assertEqual

预期结果，实际结果 # 判断预期结果和实际结果是否相等

1. 如果相等，用例通过
2. 如果不相等，用例不通过，抛出异常

#### assertIn

1. 包含，用例通过
2. 不包含，用例不通过，抛出异常

#### python自带断言

1. assert str1 == str2     判断str1 是否与 str2相等
2. assert str1 in str2     判断str2是否包含str1
3. assert True/1    判断是否为True

### 如何实现参数化

1. 测试数据一般放在json文件中
2. 使用代码读取json文件，提取我们想要的数据

#### 安装插件

unittest框架本身不支持参数化，想要使用参数化，需要插件来完成

**联网安装**

pip install parameterized

---

pip是python中包（插件）的管理工具，使用这个工具下载安装插件

**验证**

pip list # 查看到parameterized

新建一个python代码文件，导包验证

form pa... import pa...

#### 参数化代码

1. 导包unittest/pa
2. 定义测试类
3. 书写测试类方法（用到的测试数据使用变量代替）
4. 组织测试数据并传参

### 跳过

使用方法：

```python
# 直接将测试函数标记成跳过
@unittest.skip('跳过原因')
# 根据条件判断测试函数是否跳过，判断条件成立，跳过
@unittest.skipIf(判断条件,'跳过原因')
```

代码书写在TestCase文件

### 测试报告的生成

#### 自带的测试报告

只有单独运行Testcase的代码才会生成测试报告

#### 生成第三方的测试报告

1. 获取第三方的测试运行类模块，将其放在代码的目录中
2. 导包unittest
3. 使用套件对象，加载对象，去添加用例方法
4. 实例化第三方的运行对象并运行套件对象

### 日志

#### 特点

1. 调试程序
2. 定位跟踪bug
3. 根据日志，查看系统运行是否出错
4. 分析用户行为，与数据统计

#### 级别

1. debug # 调试级别
2. info #调试级别
3. warning #警告
4. error #错误级别
5. critical #严重

提示：

1. 开发常用以上debug,info,warning,error
2. 测试常用级别:info,erro

#### Logging基本使用

步骤：

1. 导包 如：import logging
2. 调用相应的级别方法，记录日志信息logging.debug('debug...')

设置级别：

​	logging.basicConfig(level=logging.DEBUG)

提示：

1. 默认级别为：logging.WARNING
2. 设置级别时调用的时logging文件夹下的常量，而不是调用的小写方法
3. 切记：设置级别以后，日志信息只会记录大于等于此级别的信息：

设置格式

fm = "%(asctime)s %(levelname)s [%(name)s] [%(filename)s (%(funcName)s:%(lineno)d] - %(message)s"
logging.basicConfig(level=logging.DEBUG, format=fm)

设置输入到文件

logging.basicConfig(level=logging.DEBUG, format=fm, filename="../log/log01.log")

logging高级用法

1. 为什么要使用高阶用法
   1. 中文乱码
   2. 无法同时输入到文件和控制台
2. logging组成
   1. logger日志器
   2. handler处理器
   3. formatter格式器
   4. filter过滤器
3. 模块关系
   1. 日志器：提供了，记录日志的入口，如：log.info("")
   2. 处理器：真正将日志器内容发送控制台还是文件或网路，都是处理器干的；每个日志器都可以添加多个不同的处理器
   3. 格式器：处理器可以设置不同的格式，不需要使用格式器
   4. 过滤器：处理器需要过滤日志信息，就选哟设置过滤器；

##### 日志器

操作：

1. 导包 import logging
2. 调用方法获取logger对象 # 如： logging.getlogger()
3. 设置级别：logger.setlevel=logging.INFO
4. 调用添加处理器方法 logger.addHandler(处理器)
