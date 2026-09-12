# Web自动化（selenium)

## 安装selenium包

==使用pip安装==

pip install selenium

==卸载==

pip uninstall selenium

==查看==

pip show selenium

==扩展==：

1. 安装指定版本 pip install selenium==版本号
2. 如果查看可安装版本，指定版本号为错误版本
3. pip是python中报管理工具（可以安装，卸载，查看python工具）
4. pip list；查看通过pip包管理工具安装的产假按或工具

提示：

1. 使用pip必须联网
2. 默认安装python3.5版本以上，自带pip管理工具，默认会自动安装并且添加path环境管理

###浏览器驱动

可以把驱动安装到项目中

![image-20260109165211426](E:\文档\笔记\图片\image-20260109165211426.png)

==创建浏览器，设置，打开==

```python
# 视频教程版
from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动


# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下
a1.get('https://www.baidu.com')



# 网页版
# import time
# 
# from selenium import webdriver
# 
# # 创建设置浏览器对象
# browser = webdriver.Edge()
# browser.get('http://www.baidu.com')
# time.sleep(10) #停留10秒
```

#### 打开网页，关闭网页，浏览器

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动


# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下
# 打开指定页面
a1.get('https://baidu.com')
time.sleep(3)
# 关闭当前标签页
# a1.close()
# 退出浏览器并释放驱动
a1.quit()
```

#### 浏览器最大化，最小化

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动


# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下

a1.get('https://baidu.com')
time.sleep(2)
# 浏览器最大化
a1.maximize_window()
time.sleep(2)
# 浏览器最小化
a1.minimize_window()
time.sleep(2)
# 浏览器最大化
a1.maximize_window()
```

#### 浏览器打开位置，尺寸

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动


# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下

a1.get('https://baidu.com')
# 浏览器打开位置
a1.set_window_position(200,200)
# 浏览器打开尺寸
a1.set_window_size(600,600)
```

#### 浏览器截图，网页刷新

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动


# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下

a1.get('https://baidu.com')
# 浏览器截图
a1.get_screenshot_as_file('1.png') # 参数是存放文件的路径和名字
time.sleep(3)
# 刷新当前网页
a1.refresh()

```

#### 元素定位

```python
from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下

a1.get('https://baidu.com')
# 定位一个元素(找到的化返回结果，找不到的话报错）
a2 = a1.find_element(By.ID,'kw')
# 定位多个元素（找到的话返回列表形式，找不到的话返回空列表）
a2 = a1.find_elements(By.ID,'kw1')
print(a2)
```

#### 元素交互操作

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下

a1.get('https://baidu.com')
# 定位一个元素(找到的化返回结果，找不到的话报错）
a2 = a1.find_element(By.ID,'chat-textarea')
time.sleep(2)
# 元素输入
a2.send_keys('小涛')
time.sleep(2)
# 元素清空
a2.clear()
time.sleep(2)
a2.send_keys('小涛')
time.sleep(2)
a2 = a1.find_element(By.ID,'chat-submit-button')
# 元素点击
a2.click()
```

#### 元素定位-ID

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下

a1.get('https://baidu.com')
# 定位一个元素(找到的化返回结果，找不到的话报错）
# 通过id定位元素，一般比较准确
# 并不是所有网页或则元素都有id值
a2 = a1.find_element(By.ID,'chat-textarea').send_keys('小涛')

```

#### 元素定义-NAME

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下

a1.get('https://baidu.com')
# 定位元素-name
# 通过name定位元素，一般比较准确
# 并不是所有网页或则元素都有name值
a1.find_element(By.NAME,'chat-textarea').send_keys('小涛')

```

#### 元素定位-CLASS_NAME

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下

a1.get('https://bilibili.com')
# 定位元素-class_name
# class值泵有空格，否则报错
# class值重复的有很多，需要切片
# class值有的网址是随机的
a1.find_elements(By.CLASS_NAME,'channel-link')[3].click()
```

#### 元素定义-TAG_NAME

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下

a1.get('https://baidu.com')
# 定位元素-Tag_name
# 查找<开头标签名字>
# 重复标签名字特别多，需要切片
a1.find_elements(By.TAG_NAME,'a')[5].click()
```

#### 元素定位-LINK_TEXT

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下

a1.get('https://baidu.com')
# 定位元素-LINK_TEXT
"""
通过精准连接文本找到标签a的元素
有重复的文本需要切片
"""
a1.find_element(By.LINK_TEXT,'地图').click()


```

#### 元素定位-PARTIAL_LINK_TEXT

```PYTHON
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下

a1.get('https://baidu.com')
# 定位元素-LINK_TEXT
"""
通过模糊连接文本找到标签a的元素[模糊文本定位]
有重复的文本需要切片
"""
a1.find_elements(By.PARTIAL_LINK_TEXT,'地')[0].click()

```

#### 元素定位-CSS_SELECTOR

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下

a1.get('https://baidu.com')
# 元素定位-CSS_SELECTOR
"""
#id = 井号+id值通过id定位
.class = 点+class值通过class定位
不加修饰符 = 标签头 通过标签头定位
通过任意类型定位："[类型='精准值']"
通过任意类型定位："[类型*='模糊值']"
通过任意类型定位："[类型^='开头值']"
通过任意类型定位："[类型$='结尾值']"
以上这些方法都属于理论定位法

更简单的定位发给发：在浏览器控制台直接复制SELECTOR（个别元素定位值会比较长）
"""
a1.find_element(By.CSS_SELECTOR,'#s-top-left > a:nth-child(7)').click()

```

#### 元素定位-XPATH

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下

a1.get('https://baidu.com')
# 元素定位-XPATH
"""
复制浏览器Xpath(通过属性+路径定位,属性如果是随机的,可能定位不到)
复制浏览器Xpath完整路径(缺点是定位值比较长,优点是基本100%精确)
"""
a1.find_element(By.XPATH,'/html/body/div[1]/div[2]/div[1]/div[3]/a[5]').click()

```



#### 元素定位隐形等待

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下

a1.get('https://baidu.com')
# 元素定位隐形等待(多少秒内找到元素就立即执行,没找到元素就报错)
a1.implicitly_wait(10)
a1.find_element(By.XPATH,'//*[@id="s-top-left"]/a[4]').click()

```

### 元素操作

#### 警告框元素交互

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素
from selenium.webdriver.common.action_chains import ActionChains

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下
a1.implicitly_wait(10)

a1.get('https://sahitest.com/demo/alertTest.htm')
a1.find_element(By.XPATH,'/html/body/form/input[2]').click()
time.sleep(2)
# 获取弹窗内的文本内容
print(a1.switch_to.alert.text)
# 点击弹窗确定按钮
a1.switch_to.alert.accept()
a1.find_element(By.XPATH,'/html/body/form/input[3]').click()

```

#### 确认框元素交互

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素
from selenium.webdriver.common.action_chains import ActionChains

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下
a1.implicitly_wait(10)

a1.get('https://sahitest.com/demo/confirmTest.htm')
a1.find_element(By.XPATH,'/html/body/form/input[1]').click()
time.sleep(1)
# 点击弹窗确定按钮
# a1.switch_to.alert.accept()
# 点击弹窗取消按钮
a1.switch_to.alert.dismiss()
```

####  提示框元素交互

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素
from selenium.webdriver.common.action_chains import ActionChains

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下
a1.implicitly_wait(10)

a1.get('https://sahitest.com/demo/promptTest.htm')
a1.find_element(By.XPATH,'/html/body/form/input[1]').click()
# 弹窗输入内容
a1.switch_to.alert.send_keys('小涛')
# 弹窗点击确定
a1.switch_to.alert.accept()
```

#### iframe嵌套页面输入，退出

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素
from selenium.webdriver.common.action_chains import ActionChains

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下
a1.implicitly_wait(10)

a1.get('https://sahitest.com/demo/iframesTest.htm')
# 获取iframe元素
a2 = a1.find_element(By.XPATH,'/html/body/iframe')
# 进入iframe嵌套页面
a1.switch_to.frame(a2)
# 进入iframe页面操作元素点击
a1.find_element(By.XPATH,'/html/body/table/tbody/tr/td[1]/a[1]').click()
# 退出iframe嵌套页面
a1.switch_to.default_content()
a1.find_element(By.XPATH,'/html/body/input[2]').click()

```

#### 获取元素文本内容，是否可见

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素
from selenium.webdriver.common.action_chains import ActionChains

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下
a1.implicitly_wait(10)

a1.get('https://baijiahao.baidu.com/s?id=1853165002199798774')
# 获取元素文本内容 text
a2 = a1.find_element(By.XPATH,'//*[@id="ssr-content"]/div[2]/div[1]/div[2]/div[3]/div[1]/div[26]/span').text
print(a2)
# 元素是否可见 is_selected()
a3 = a1.find_element(By.XPATH,'//*[@id="__SVG_SPRITE_NODE__"]').is_selected()
print(a3)
a3 = a1.find_element(By.XPATH,'//*[@id="ssr-content"]/div[2]/div[1]/div[2]/div[3]/div[1]/div[1]/span').is_selected()
print(a3)
```

#### 网页前进后退

```python
import time

from selenium import webdriver # 用于操作浏览器
from selenium.webdriver.edge.options import Options # 用于设置浏览器
from selenium.webdriver.edge.service import Service # 用于管理驱动
from selenium.webdriver.common.by import By # 用于定义元素
from selenium.webdriver.common.action_chains import ActionChains

# 浏览器查找多个元素：document.getElementById('元素值')

# 创建设置浏览器对象
browser = Options()
# 禁用沙盒模式(增加兼容性）
browser.add_argument('--no-sandbox')
# 保持浏览器打开状态（默认是代码执行完毕自动关闭）
browser.add_experimental_option('detach',True)

# 创建并启动浏览器
a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下
a1.implicitly_wait(10)

a1.get('https://www.baidu.com/')
a1.find_element(By.XPATH,'//*[@id="chat-textarea"]').send_keys('小涛')
time.sleep(1)
a1.find_element(By.XPATH,'//*[@id="chat-submit-button"]').click()
time.sleep(5)
# 网页后退
a1.back()
time.sleep(5)
# 网页前进
a1.forward()

 
```

#### 页面刷新

dirver.refresh()

#### 获取页面title

dirver.title

#### 获取当前页面URL

dirver.current_url

#### 返回元素大小

dirver.size返回参数是字典

#### 获取属性值

dirver.get_attribute("xxx")

传递的参数为元素的属性名

#### 判断元素是否可见

dirver.is_displayed()

#### 判断元素是否可用

dirver.is_enabled()

#### 判断元素是否选中

dirver.is_selected()

用来检查复选框或者单选框是否被选中

 #### 鼠标的操作

实例化对象：

action = ActionChains(dirver)

- 方法：
  - context_click(element)     右击===>模拟鼠标右击效果
  - double_click(elemnt)    双击===>模拟鼠标双击效果
  - drag_and_drop(source,target)    拖动===>模拟鼠标拖动效果
    - source源元素，target目标元素
    - 拓展target可以使用坐标（xoffset,yoffset)代替
  - move_to_element(element)    悬停===>模拟鼠标悬停效果
  - perform()    执行===>此方法用来执行以上所有鼠标操作
  
- 代码演示：

  ```python
  import time
  
  from selenium import webdriver # 用于操作浏览器
  from selenium.webdriver import ActionChains
  from selenium.webdriver.edge.options import Options # 用于设置浏览器
  from selenium.webdriver.edge.service import Service # 用于管理驱动
  from selenium.webdriver.common.by import By # 用于定义元素
  
  # 浏览器查找多个元素：document.getElementById('元素值')
  
  # 创建设置浏览器对象
  browser = Options()
  # 禁用沙盒模式(增加兼容性）
  browser.add_argument('--no-sandbox')
  # 保持浏览器打开状态（默认是代码执行完毕自动关闭）
  browser.add_experimental_option('detach',True)
  
  # 创建并启动浏览器
  a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下
  
  # a1.get('https://baidu.com')
  # action = ActionChains(a1)
  # print('开始执行')
  # 鼠标右键
  # action.context_click(a1.find_element(By.XPATH,'//*[@id="chat-textarea"]')).perform()
  # a1.find_element(By.XPATH,'//*[@id="chat-textarea"]').send_keys('我的世界')
  # 鼠标双击
  # action.double_click(a1.find_element(By.XPATH,'//*[@id="chat-textarea"]')).perform()
  a1.get('https://seleniumbase.io/demo_page')
  action = ActionChains(a1)
  print('开始执行')
  # 鼠标悬停
  action.move_to_element(a1.find_element(By.XPATH,'//*[@id="myDropdown"]')).perform()
  
  ```

  

1. 注意：
   1. selenium框架虽然提示了，右键鼠标的方法，但是没有提供右击菜单方法

#### 键盘操作

##### Keys类

- 常用的键盘操作

  1. send_keys(Keys.BACK_SPACE)	删除键（BackSpace）
  2. send_keys(Keys.SPACE)                    空格键（Sacpe）
  3. send_keys(Keys.TAB)                   制表键（Tab）
  4. send_keys(Keys.ESCAPE)                   回退键（Esc）
  5. send_keys(Keys.ENTER)                   回车键（Enter）
  6. send_keys(Keys.CONTROL,'a')                   全选（Ctrl+A）
  7. send_keys(Keys.CONTROL,'c')                   全选（Ctrl+C）

  ```python
  import time
  
  from selenium import webdriver # 用于操作浏览器
  from selenium.webdriver import ActionChains, Keys
  from selenium.webdriver.edge.options import Options # 用于设置浏览器
  from selenium.webdriver.edge.service import Service # 用于管理驱动
  from selenium.webdriver.common.by import By # 用于定义元素
  
  # 浏览器查找多个元素：document.getElementById('元素值')
  
  # 创建设置浏览器对象
  browser = Options()
  # 禁用沙盒模式(增加兼容性）
  browser.add_argument('--no-sandbox')
  # 保持浏览器打开状态（默认是代码执行完毕自动关闭）
  browser.add_experimental_option('detach',True)
  
  # 创建并启动浏览器
  a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下
  
  a1.get('https://baidu.com')
  action = ActionChains(a1)
  print('开始执行')
  # 鼠标右键
  # action.context_click(a1.find_element(By.XPATH,'//*[@id="chat-textarea"]')).perform()
  a1.find_element(By.XPATH,'//*[@id="chat-textarea"]').send_keys('我的世界')
  # 键盘输入
  action.send_keys(Keys.ENTER).perform()
  # 鼠标双击
  # action.double_click(a1.find_element(By.XPATH,'//*[@id="chat-textarea"]')).perform()
  # a1.get('https://seleniumbase.io/demo_page')
  # action = ActionChains(a1)
  # print('开始执行')
  # # 鼠标悬停
  # action.move_to_element(a1.find_element(By.XPATH,'//*[@id="myDropdown"]')).perform()
  
  ```

  

### 隐式等待

- 方法：

  - diver.implicitly_wait(参数：秒)

  ```python
  from selenium import webdriver
  from selenium.webdriver.edge.options import Options
  from selenium.webdriver.edge.service import Service
  from selenium.webdriver.common.by import By
  
  # 创建设置浏览器对象
  b = Options()
  # 禁用沙盒模式
  b.add_argument('--no-sandbox')
  # 保持浏览器打开状态
  b.add_experimental_option('detach',True)
  
  # 创建并启动浏览器
  l = webdriver.Edge(service=Service('msedgedriver.exe'),options=b)
  l.implicitly_wait(10) # 隐式等待
  
  l.get('https://seleniumbase.io/demo_page')
  # 如何选中"CheckBox 1"？
  l.find_element(By.XPATH,'//*[@id="checkBox1"]').click()
  # 如何检查"CheckBox 2"是否已被选中？
  a = l.find_element(By.XPATH,'//*[@id="checkBox2"]').is_selected()
  if a:
      print('被选中了')
  else:
      print('未被选中')
  ```

  - 特色：
    1. 针对所有元素生效
    2. 一般情况下为前置必写的代码（1、获取浏览器对象；2、最大化浏览器；3、设置隐式等待）

### 显示等待

- 导包

  ```python
  from selenium.webdriver.support import expected_conditions as EC
  ```

- 创建实例：

  ```python
  wait = WebDriverWait(a1,10)
  ```

  - 代码：

    ```python
    import time
    
    from selenium import webdriver # 用于操作浏览器
    from selenium.webdriver.edge.options import Options # 用于设置浏览器
    from selenium.webdriver.edge.service import Service # 用于管理驱动
    from selenium.webdriver.common.by import By # 用于定义元素
    from selenium.webdriver.common.action_chains import ActionChains
    from selenium.webdriver.support import expected_conditions as EC
    from selenium.webdriver.support.wait import WebDriverWait
    
    # 浏览器查找多个元素：document.getElementById('元素值')
    
    # 创建设置浏览器对象
    browser = Options()
    # 禁用沙盒模式(增加兼容性）
    browser.add_argument('--no-sandbox')
    # 保持浏览器打开状态（默认是代码执行完毕自动关闭）
    browser.add_experimental_option('detach',True)
    
    # 创建并启动浏览器
    a1 = webdriver.Edge(service=Service('msedgedriver.exe'),options=browser) # 如果不填servic就是当前目录下
    a1.implicitly_wait(10)
    
    wait = WebDriverWait(a1,10)
    
    a1.get('https://www.baidu.com/')
    
    # 等待元素出现
    wait.until(
        EC.presence_of_element_located((By.XPATH,'//*[@id="chat-textarea"]'))
    ).send_keys('小涛')
    
    ```

    cookie操作

    方法：

    1. get_cookie(name)	-->获取指定cookie;name:为cookie的名称

    2. get_cookies()	--> 获取本网站有本地cookies

    3. add_cookie(cookie_dict)	--> 添加cookie

       cookie_dict:一个字典对象，必须的键包含：“name"and"value"

#### 等待元素

**visibility_of_element_located**

```python
EC.visibility_of_element_located((By.ID,'username'))
```



元素是否存在，元素可见，元素有高度宽度（不是display:none)

**presence_of_element_located**

```python
EC.presence_of_element_located((By.ID,'username'))
```



- 只要元素在DOM里，不保证可见
- 适合判断页面是否加载完成
- 不适合直接点击

**visbility_of_element_located**

```python
EC.visbility_of_element_located((By.ID,'username'))
```

- 在DOM，可见，有尺寸
- 适合点击/输入前使用

**visiblity_of**

```python
element = driver.find_element(...)
EC.visiblity_of(element)
```

- 和上面一样
- 但参数是已经找到的element

**invisibility_of_element_located**

```python
EC.invisibility_of_element_located((By.ID,'loading'))
```

- 元素消失，或者变成不可见
- 常用于等待loading消失

**element_to_be_clickable(做常用)**

```python
EC.element_to_be_clickable((By.ID,'submit'))
```

- 可见，enabled，可以点击
- 企业里点击按钮几乎都用这个

**text_to_be_present_in_element**

```python
EC.text_to_be_present_in_element((By.ID,'flash'),'Success')
```

- 等待文本出现

**url_contains**

```python
EC.url_contains('/url_containsurl_contaisecure')
```

- 等待URL包含某个内容

### 参数化

- 步骤：
  1. 导包from parameterized import parametertized
  2. 修饰测试函数@parmeterized。expand（列表类型数据）
  3. 在测试函数中使用变量接收，传递过来的值
- 语法：
  1. 单个参数：值为列表
  2. 多个参数：值为列表嵌套元组如：[(1,2,3),(2,3,4)]

### 测试失败重试

使用pytest插件：pytest-rerunfailures

安装:

```
pip install pytest-rerunfailures
```

#### 方法1:命令控制

```
pytest --reruns 3
# 意思：失败的用例最多再跑3次
#也可以延迟
pytest --reruns 3 --reruns-delay 2
# 意思失败等待2秒后再执行
```

#### 方法2：只给某个测试加重试

```python
import pytest
@pytest.mark.flaky(reruns=3)
def test....():
    ...
```

#### 方法3：全局配置

- 在pytest.ini里面写：

```ini
[pytest]
addopts = --reruns 2 --reruns-delay 1
```

以后每次跑pytest都自带重试
