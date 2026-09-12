# Pytest测试框架

## 安装

```
pip install pytest # 安装
pip install pytest -u #升级到最新版
```

## pytest有三种启动方式

1. 命令：pytest

2. 代码

   ```
   import pytest
   pytest.main()
   ```

3. 鼠标【不推荐】

   1. 是由pycharm提供不是pytest
   2. 行为前两种方式，不一致，不适合复杂项目

**pytest在简单的基础上，对断言进行高级封装（AST），对pyton数据结构断言，非常友好**

1. pytest遵循了python简单的学习方式
2. pytest实现了很多高级特性
3. 鼓励积极使用断言

## 看懂结果

1. 执行环境：版本，根目录，用例数量
2. 执行过程：文件名字，用例结果，执行进度
3. 失败详情：用例内容，断言提示
4. 整体摘要：结果情况，结果数量，花费时间

用例结果缩写

| 缩写 | 单词    | 含义                       |
| ---- | ------- | -------------------------- |
| .    | passed  | 通过                       |
| F    | failed  | 失败（用例执行时报错）     |
| E    | error   | 出错（fixture执行报错）    |
| S    | skipped | 跳过                       |
| X    | xpassed | 预期外的通过（不符合预期） |
| x    | xfailed | 预期内的失败（符合预期）   |

## 用例规则

### 用例发现规则

测试框架在识别，加载用例的过程，称之为：**用例发现**

pytest的用例发现步骤：

1. 遍历所用的目录，例外：venv，.开头的目录
2. 打开python文件，`test_`开头或者`_test`结尾
3. 遍历所用的test开头类
4. 收集所有的test_开头的函数或者方法

### 用例内容规则

> pytest8.4增加了一个强制要求

pytest对用例的要求

1. 可调用的（函数，方法，类，对象）
2. 名字test_开头
3. 没有参数（参数有另外含义）
4. 没有放回值（默认为None）

## 配置框架

配置可以改变pytest默认的规则

1. 命令参数
2. ini配置文件

所有的配置方式，可以一键获取

```
pytest -h
```

- 有哪些配置
- 分别是什么方式
  - -开头：参数
  - 小写字母开头：ini配置
  - 大写字母开头：环境遍历
- 配置文件：pytest.ini

常用参数

- `-v`增加详细程度
- `-s`在用例中正常的使用输入输出
- `-x`快速退出，当遇到失败的用例停止执行
- `-m`用例筛选

## 标记mark

___

标记可以让用例与众不同，进而可以让用例被区别对待

### 1.用户自定义标记

用户自定义标记只能实现用例筛选

步骤：

1. 先注册
2. 再标记
3. 后筛选

```
pytest -m api
```



### 2.框架内标记

用户自定义标记为用例怎加特殊执行效果

和用户自定义标记区别

1. 不需注册，可以直接使用
2. 不仅可以筛选，还可以郑家特殊效果
3. 不同的标记，增加不同的特殊效果
   - skeip:无条件跳过
   - skipfi：有条件跳过
   - xfail：预期失败
   - parametrize：参数化
   - usefixtures：使用fixtures

## 数据驱动测试参数

数据文件，驱动用用例执行数量，内容

```
a,b,c
1,2,3
1,2,3
1,2,3
1,2,3
1,2,3
```

```python
@pytest.mark.parametrize("a,b,c",read_csv("data.csv"))
def test_ddt(self,a,b,c):
	res=add(int(a),int(b))
	assert res = int(c)
```

## 夹具fixture

夹具：在执行用例之前，执行之后，自动运行的代码

场景：

- 之前：加密参数/之后：解密结果
- 之前：启动浏览器/之后：关闭浏览器
- 之前：注册，登录账号/之后：删除账号

### 创建fixture

```python
@pytest.fixture
def f():
    # 前置操作
    yield
    # 后置操作
```

1. 创建函数
2. 添加装饰器
3. 添加yield关键字

### 使用fixture

1. 在用例的参数列表中，加入fixture名字
2. 给用例加上`pytest.mark.usefixtures("名字")`标记

```py
def test_l(f):
	pass
@pytest.mark.usefixtures("f")
def test_2():
	pass
```

### 高级用法

1. 自动使用
2. 依赖使用
   1. linux:使用linux进行编译
   2. git:使用git进行版本控制
   3. fixture：使用fixture进行前后置自动操作
3. 返回内容：接口自动化封住：接口关联
4. 范围共享
   - 默认范围：function
   - 全局范围：session
     - 使用conftest.py

命令空间->第三空间

## 插件管理

pytest插件生态是pytest特别的优势之处

插件分成两类

- 不需要安装：内置插件
- 需要安装：第三方插件

插件的启用管理

- 启用：-p abc
- 禁用：-p no:abc

插件使用方式：

1. 参数
2. 配置文件
3. fixture
4. mark

## 常用第三方插件

pytest插件：https://docs.pytest.org/en/stable/reference/plugin_list.html

### pytest-html

用途：生成html测试报告

安装：

```python
pip install pytest-html
```

使用：

```
--html=report.html --self-contained-html
```

### pytest-xdist

用途：分布式执行（多线程）

安装：

```
pip install pytest-xdist
```

使用：

```
-n 想启动的线程数
```

> 只有在任务本身耗时较长，超出调用成本横夺的时候，才有意义

> 分布式执行，有并发问题：资源竞争，乱序

### pytest-rerunfailures

用途：用例失败之后，重新执行

安装：

```
pip install pytest-rerunfailures
```

使用：

```
--reruns 5 --reruns-delay 1
```

### pytest-result-log

用途：把用例执行的结果记录到日志文件中

安装：

```
pip install pytest-result-log
```

使用：执行的测试自动执行

配置：放在pytest.ini

```ini
log_file=./logs/pytest.log
log_file_level = info 
log_file_format = %(levelname)-8s %(asctime)s [%(name)s:%(lineno)s] :(message)s
log_file_date_format = %Y-%m-%d %H:%M:%S

; 记录用例执行结果
result_log_enable = 1
; 记录用分割线
result_log_separator = 1
; 分割线等级
result_log_level_separator = warning
; 异常信息等级
result_log_level_verbose = info
```

## 企业级测试报告

allure是一个测试报告框架

安装：

```
pip install allure-pytest
```

配置：

```
addopts = --alluredir=temps --clean-alluredir
```

生成报告

```
allure generate -o report -c temps
```

allure支持对用例进行分组何关联（敏捷开发）

```
@allure.epic 史诗 项目
@allure.feature 主题 模块
@allure.story 故事 功能
@allure.title 标题 用例
```

## web自动化测试实战

pytest仅进行用例管理，不会控制浏览器，需要借助新的工具：selenium

1. 只了解selenium
2. 搜索关于selenium的pytest插件

## 测试框架要封装什么

封装：

- 隐藏细节
- 增加功能
- 优化功能

接口自动化封装

- 使用yaml作为用例，降低自动化门槛
- 自动请求接口，断言接口
- 自动在日志记录http报文
- 自动生成allure测试报告

## YAML文件格式

**一句话：YAML完全兼容json格式，并且支持Python相识写法**

重点：

1. YAML完全兼容JSON
2. 是数据格式，不是变成语言
3. 像python一样容易编辑何阅读

### 安装yaml模块

```
pip install pyyaml
```

### 编写yaml文件

1. `#`作为注释符号
2. 缩进：使用两个空格
3. 成员表示
   - `-`表示列表成员
   - `:`表示字典成员
4. **兜底：完全兼容JSON**

```
# 这是我的一个yaml文件
数字:
  - 1
  - -1
  - 1.1
  
字符串:
  - '1231234124124'
  - "213fjdie"
  - jfeiwjf
 
空值:null # json写法

列表:[1,2,3] 

字典:{"a":1,"b":2}
```

### 加载yaml文件

```
import yaml
def load_yaml(path):
	f=open(path,encoding="utf-8")
	s=f.read()
	data = yaml.safe_load(s)
	return data
```

## 接口测试用例

### 设计用例内容

1. 名字
2. 标记【可选】
3. 步骤
   1. 请求接口：GET HTTPS://WWW.baidu.com
   2. 响应断言: status_code == 200
   3. 提取变量: json()['code']

## 封装接口自动化框架

###请求接口

外部工具：requests

从HTTP协议抓包角度，请求有三部分组成：

- 行：方法+地址（必填）
- 头：请求头（键值对）
- 体：参数内容

```
method = 'post'
url = 'http://198.168.12.12/shop/api.php'
requests.request(
	method, url,
	json={
	"a":1,
	"b":[1,2,3]
	"c":{}
	})
```



###断言响应

1. 断言里面有什么
2. 断言如何断言

从http协议抓包角度，响应有三部分组成：

- 行：状态码
- 头：响应头（键值对）
- 体：响应内容

```python
# resp 就是响应
# 获取响应中的内容
print(resp.status_code)# 状态码
print(resp.headers)# 响应头
print(resp.text)# 响应正文
print(resp.json())# 响应正文转成json
# 断言单个内容是否正确
from responses_validator import validator # 这个是第三方插件需要下载
validator(
resp,
status_code=200,
text='*美酒*',
json={
    "data":{
        "banner_list":[{"name":"美酒"}]
    }
}
)
```

### 变量提取

基本原则：

- json:jsonpath
- html:xpath
- 字符串：re

```python
import jsonpath
def extract(resp,attr_name,exp):
    try:
        resp.json=resp.json()
    except Exception:
        resp.json ={}
    attr = getattr(resp,attr_name)
    res = jsonpath.jsonpath(attr,exp)
    return res[0]
```

## 框架落地封装

![360c0dc5029a201f7e6c4858ce793b9b](E:\文档\笔记\图片\360c0dc5029a201f7e6c4858ce793b9b.png)

进一步完善：

1. YAML用例测试文件上传
2. YAML用例进行数据去掉测试？
3. YAML用例进行自定义的断言
4. YAML用例进行数据库查询

main.py

```python
import os
import pytest
pytest.main()
os.system(f"allure generate -c -o report temps")
```

