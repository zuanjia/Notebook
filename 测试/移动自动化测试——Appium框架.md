# 移动自动化测试——Appium框架

## adb调试工具

### adb构成和工作原理

- adb构成
  - client端，在电脑上，负责发送adb命令
  - daemon守护进程，在手机上，负责接收和执行adb命令
  - server端，在电脑上，负责管理client和daemon之间的通信
- adb工作原理
  1. client端将命令发送给server端
  2. server端会将命令发送个daemon端
  3. daemon端进行执行
  4. 将执行结果，放回给server端
  5. server端将结果再返回给client端

### 获取包名和界面名【应用】

- 包名和界面名的概念

  - 包名，对应者应用程序
  - 界面名，对应着应用程序的某个界面，也叫做启动名

- 如果获取包名和界面名

  - mac

    ```
    adb shell dumpsys window windows | grep mFocusedApp
    ```

    

  - windows

    ```
    adb shell dumpsys window windows | findstr mFocusedApp
    ```

    

- 应用场景
  - 后期，我们在告诉计算机到底打开哪一个应用和哪一个界面，必须要使用的一个写代码的参数

### 文件传输【应用】

#### 发送文件到手机

- 从电脑发送文件到手机

  - 如何使用

    ```
    adb push 电脑的文件路径 手机的文件夹的路径
    ```

    

#### 从手机中拉取文件

- 如何使用

  ```
  adb pull 手机的文件路径 电脑的文件夹的路径
  ```

- 应用场景
  - 如果希望将电脑上的某个文件，发送到手机，使用adb push 的命令
  - 如果希望将手机上的某个文件，发送到电脑，使用adb pull 的命令

### 获取app启动时间【应用】

获取app启动时间

```
adb shell am start -w  包名/界面名
```

- 应用场景
  1. 当企业有需求的时候，使用这个adb命令进行测试
  2. 如果企业没有特定的事件规范，我们可以参考同类型产品，不要超过一倍即可

### 获取手机日志【应用】

- 获取手机的日志信息

  ```
  adb logcat
  ```

- 应用场景
  - 当发生崩溃的时候，可以将日志信息发给开发人员，便于其快速的定位bug
    - 用于崩溃的处理，需要找日志的“at”前的第一个字符式E的就是错误信息

### 其他命令

- 安装app到手机

  ```
  adb install apk路径

- 卸载手机上的app

  ```
  adb uninstall 包名

- 查看连接设备的数量及设备号

  ```
  adb devices

- 进入到android手机系统内部的命令行中

  ```
  adb shell

- 关闭adb服务

  ```
  adb kill-server

- 开启adb服务

  ```
  adb start-serve

- 查看adb帮助

  ```
  adb --help
  ```

## appium自动化测试框架

### 如何使用ppium打开任意一个应用程序

1. 打开要测试的应用
2. 使用adb命令获取包名和界面名
3. 修改desired_caps字典中的appPackage和appActivity的参数

### 如果测试的版本号发生变化

修改desired_caps字典中的platformVersion的参数

### 如果测试的设备平台发生了变化

修改desired_caps字典中的platformName的参数

```python
from appium import webdriver
import time

desired_caps = dict()
# 平台的名字，大小写无所谓，不能乱写
desired_caps['platformName'] = 'andRoId'
# 平台的版本，（5.4.3 可以写 5.4.3，5.4，5）
desired_caps['platformVersion'] = '5'
# 设备的名字，随便写，不能乱写
desired_caps['deviceName'] = '1'
# 要打开的应用程序
desired_caps['appPackage'] = 'com.cyanogenmod.filemanager'
# 要打开的界面
desired_caps['appActivity'] = '.activities.NavigationActivity'

driver = webdriver.Remote('http://localhost:4723/wd/hub', desired_caps)

time.sleep(5)

driver.quit()
```

### 如果通过代码跳转其他的app

- 通过driver对象调用start_activity的方法（已经弃用）
- 使用mobile：startActivity来启动应用

```python
# 旧
# stsrt_activty("包名","界面")


# 新
# 导入所需的模块
from appium import webdriver

# 设置 Appium 服务器和测试设备的配置
desired_caps = {
    'platformName': 'Android',
    'platformVersion': 'your_android_version',
    'deviceName': 'your_device_name',
    'appPackage': 'your_app_package',
    'appActivity': 'your_app_activity'
}

# 连接 Appium 服务器
driver = webdriver.Remote('http://localhost:4723/wd/hub', desired_caps)

# 使用 mobile: startActivity 来启动应用
driver.execute_script('mobile: startActivity', {
    'appPackage': 'your_app_package',
    'appActivity': 'your_app_activity'
})

# 在这里执行其他测试步骤

# 关闭应用
driver.quit()
```

### 通过代码获取app的包名和界面名

- 通过driver对象调用current_package属性
  - 包名
- 通过driver对象调用current_activity属性
  - 界面名

```python
print(driver.current_package)
print(dirver.current_activity)
```

### 通过代码关闭app和驱动对象

- 通过drivr对象调用close_app方法（弃用）

  - 关闭当前程序，不会关闭驱动程序

    ```python
    # 旧版本用法（已弃用）
    driver.close_app()
    ```

- 通过driver对象调用terminate_app（appPackage)

  - 强制终终止指定的应用程序，只关闭指定应用，dirver session保持活跃，可以关闭任何已安装的应用（不仅仅当前应用），适用于需要在测试用切换或重启应用的场景

    ```python
    # 测试中重启应用
    driver.terminate_app('com.example.app')
    driver.activate_app('com.example.app')  # 重新启动
    
    # 清理后台应用
    driver.terminate_app('com.android.chrome')
    ```

    

- 通过driver对象调用quit方法

  - 关闭驱动对象，同时关闭驱动对象所关联的app

    ```python
    # 结束整个测试会话
    driver.quit()
    ```

    

### 安装和卸载应用以及判断应用是否安装

- 安装应用

  ```python
  install_app("apk路径")
  ```

  

- 卸载应用

  ```python
  remove_app("包名")
  ```

  

- 判断某个应用是否已经安装

  ```python
  is_app_installed("包名")
  ```



实例代码：

```python
# 判断安智市场是否已经安装
if driver.is_app_installed("cn.goapk.market"):
    # 如果安装，就要卸载
    driver.remove_app("cn.goapk.market")
else:
    # 如果没有安装，就要安装
    driver.install_app("/Users/Yoson/Desktop/anzhishichang.apk")
```

###  模拟按home键，将应用防止到后台中

- 通过driver对象调用background_app方法

  - 注意：这个方法会自动回到前台

  ```python
  dirver.backgrouond_app("放置到后台的事件，秒")
  ```

  实例代码

  ```python
  print("---- 准备进入后台 ----")
  
  # 进入后台5秒，再回到前台
  driver.background_app(5)
  
  print("---- 已经回到前台 ----")
  ```



## UIAutomatorVirwer的使用

### 使用uiautomatorviewer获取元素特征

1. 保证想要查看的元素在当前的屏幕上
2. 打开uiautomatorviewer工具
3. 点击左上角第二个按钮
4. 点击获取特征的元素
5. 查看工具右下角相关的特征信息

### 使用uiautomatorviewer注意点

1. 命令行窗口不要关闭
2. 如果uiautomatorviewer闪退
   - 跟换jdk为1.8
3. 点击第二个按钮的时候报错
   - 重启adb
     - `adb kill-server`
     - `adb start-server`

### 定位一个元素

- find_element_by_id
  - 传入的参数：resource-id的值
- find_element_by_class_name
  - 传入的参数：class的值
- find_element_by_xpath
  - 传入的参数：xpath表达式
- 注意点
  - 如果很多元素的"特征"相同，使用find_element_by_xxx的方法会找到第一个
  - 也就是说，尽可能去找元素特征有唯一的特征，来定位

### 定位一组元素

- find_elements_by_id
  - 传入的参数：resource-id的值
- find_elements_by_class_name
  - 传入的参数：class的值
- find_elements_by_xpath
  - 传入的参数：xpath表达式
- 概念：
  - 如果通过一组的方式进行定位，获取的返回值不再式一个元素。而是一个列表，列表中装着所有符合这个特征的元素

### 定位元素的注意点

如果find_element_by_xxx方法，传入了一个没有的条件，会报错，NoSuchElementException

如果find_elements_by_xx方法，传入了一个没有的条件不会报错，返回一个空列表

### 元素等待

概念：找元素的时候，通过一个时间的设置，进行等待元素，等待元素出来之后，再来定位，放置报错

应用场景：

​	如果某个元素没有及时出来，那么我们就应该使用元素等待

分类：

​	隐式等待

​	显示等待

#### 隐式等待

- 关键方法：
  - 通过driver对象嗲用implicity_wait方法
  - 设置超时时间
- 作用：
  - 在设置了超时时间之后，后续所有的定位元素的方法都会在这个事件内等待元素出现
  - 如果出现了，直接进行后续操作
  - 如果没有出现，报错，NoSuchElementException

```python

# ------- 隐式等待
# driver.implicitly_wait(10)
#
# print("---准备找返回进行点击")
# driver.find_element_by_xpath("//*[@content-desc='收起']").click()
# print("---点完了")
```



#### 显示等待

- 关键方法
  - 关键类：WebDriverWait
  - 关键方法：WebDirverWait对象中的until的方法
- 作用：
  - 在设置了像是等待之后，可以等待一个超时时间，在这个超时时间之内进行查找，默认每0.5秒找一次
  - 0.5秒的频率式可以设置的
  - 一但找到这个元素，直接进行后续操作
  - 如果没有找到，报错，NoSuchElementException

```python
# ------- 显式等待

print("---准备找返回进行点击")
# wait = WebDriverWait(driver, 25, 5)
# back_button = wait.until(lambda x: x.find_element_by_xpath("//*[@content-desc='收起']"))
# back_button.click()

# back_button = WebDriverWait(driver, 5, 1).until(lambda x: x.find_element_by_xpath("//*[@content-desc='收起']"))
# back_button.click()

# WebDriverWait(driver, 5, 1).until(lambda x: x.find_element_by_xpath("//*[@content-desc='收起']")).click()

# 使用显示等待，在20秒的时间内，每3秒钟找一次，id为xxx的元素
WebDriverWait(driver, 20, 3).until(lambda x: x.find_element_by_id("xxx"))


print("---点完了")

```

#### 隐式等待和显示等待的选着

- 从使用的角度上：
  - 隐式等待更简单
  - 显示等待相对负责
- 从灵活性的角度上：
  - 显示等待更加灵活，因为可以针对每一个元素进行单独的设置
  - 隐式等待式针对全局的定位元素
- 关于sleep的问题
  - sleep不是泵做元素等待，而是不推荐，因为会造成时间上的浪费
- 从选择的角度：
  - 考虑使用的是单个还是全局
  - 考虑灵活性的问题

### 元素操作

#### 点击元素

- 关键方法
  - click()

#### 对输入框进行文字输入

- 关键方法：

  - send_keys("输入文字")

- 注意点：

  - 默认输入中文是有问题的，需要在来连接手机参数中多加两行代码

    ```python
    desired_caps['unicodeKeyboard'] = True
    desired_caps['resetKeyboard'] = True
    ```

#### 对输入框的文字的清空

- 关键方法
  - clear()

#### 获取元素的文本内容，位置，大小

##### 获取文本内容

- 关键属性
  - text

##### 获取元素的位置

- 关键属性
  - location
  - 是一个字典，字典中有x和y两个key
  - 取到的数据类型是int的

##### 获取元素大小

- 关键属性
  - size
  - 是一个字典，字典中有width和height两个key
  - 取到的数据类型是int的

#### 根据元素的属性名获取属性值

- 关键的方法
  - get_attribute('属性名')
- 注意点
  - 想获取resource-id使用resourceId属性名 API>=18
  - 想要获取class使用className属性名API>=18
  - 想要获取content-desc使用name属性名
  - 其他的，都可以参考uiautomatorviewer中的属性名

### 滑动和拖拽事件

#### swipe滑动方法

- 方法：
  - driver.swipe(起始y坐标，起始x坐标，结束y坐标，结束x坐标，持续时间)
- 特点：
  - 参数的坐标idan
  - 持续时间短，惯性大
  - 持续时间长，惯性小

#### scroll滑动事件

- 方法：
  - driver.scroll(起始元素，结束元素)
- 特点：
  - 参数是元素
  - 没有持续时间，有惯性（新版好像可以设置持续时间）

#### drag_and_drop滑动方式

- 方法：
  - driver.drag_and_drop(起始元素，结束元素)
- 特点：
  - 参数是元素
  - 没有持续时间，无惯性（新版好像可以设置持续时间和也有惯性了）

#### 滑动和拖拽事件的选择

- 三种方式的选择
  - 有惯性，传入参数坐标
    - swipe,设置较短的持续时间
  - 有惯性，传入参数元素
    - scroll
  - 无惯性，传入参数坐标
    - swipe，设置较长的持续时间
  - 无惯性，传入参数元素
    - drag_and_drop

### 高级手势

#### TouchAction

- 概念和作用：
  - 高级手势，可以将小的动作组合成一系列复杂的动作
- 步骤
  1. 创建TouchAction对象
  2. 通过对象调用要执行的动作
  3. 通过perform进行执行

#### 轻敲

- 关键方法：
  - tap
- 参数：
  - 可以传入元素
    - 使用element参数
  - 可以传入坐标
    - 使用x和y参数
  - 多次点击
    - 使用count参数

#### 按下和抬起

##### 按下

- 关键方法
  - press
- 参数：
  - 可以传入元素
    - 使用element参数
  - 可以传入坐标
    - 使用x和y参数

##### 抬起

- 关键方法：
  - release

#### 等待

- 关键方法：
  - wait
- 参数：
  - 等待的时间（毫秒）
    - 使用ms参数

#### 长按

- 关键方法：
  - long_press
- 参数：
  - 可以传入元素
    - 使用element参数
  - 可以传入坐标
    - 使用x和y参数
  - 设置持续时间
    - 使用duration参数（毫秒）
  - 额外补充
    - 长按<==>按下，等待，抬手

#### 移动

- 关键方法：
  - move_to
- 参数
  - 可以传入元素
    - 使用element参数
  - 可以传入坐标
    - 使用x和y参数

### 手机操作API

#### 分辨率和截图

- 关键方法：
  - dirver.get_window_size()
- 返回值
  - 字典
  - 里面有两个key，分别是width和height
  - 宽和高的值是int类型的

###### 截图

- 关键方法：
  - driver.get_screenshot_as_file
- 参数
  - 文件的路径
  - 如果直接写了文件名，则会默认保存在项目目录下

#### 获取手机网路

- 获取网络状态
  - 属性
    - network_connection

#### 设置手机网路

- 方法：
  - set_network_connection
- 参数
  - 网络类型

注意点：

网络类型，建议使用系统提供的类型

```python
from appium.webdriver.connectiontype import ConnectionType
```

```python
# # 获取当前网络
# print(driver.network_connection)
#
# # 设置当前网络
# driver.set_network_connection(1)
#
# # 不推荐
# if driver.network_connection == 4:  # 4=data only
#     print(1)
# else:
#     print(0)
#
# # 推荐的
# if driver.network_connection == ConnectionType.DATA_ONLY:
#     print(1)
# else:
#     print(0)
```

#### 发送键到设备

- 关键方法：
  - driver。press_keycode
- 参数
  - 按键对应的编码

- 参考的keycode
  - https://blog.csdn.net/feizhixuan46789/article/details/16801429

#### 操作通知栏

- 关键方法
  - driver.open_notifications()

官方没有提供关闭方法，现实中怎么关闭就怎么关闭

- 关闭：
  - 可以使用滑动
  - 使用返回键
    - press_keycode(4)