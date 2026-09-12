# Cocos脚本生命周期

说明：简单来说每个函数的执行顺序和触发方式

 ==onLoad== 加载函数：在脚本第一个执行的函数，一般用于开启监听事件

==onDestroy== 销毁函数：当组件或者节点被销毁时，执行这个函数，一般用于关闭监听事件

==start(默认)== 开始函数：脚本启动执行该函数

==update(默认)== 每帧（1秒=60帧）都会执行的循环函数

==lateUpdate== 延迟函数：update函数执行后，执行这个函数

==onDisable== 节点被禁止/隐藏时自动执行函数

==onEnable== 节点被启用/显示时自动执行函数

官方文档：[生命周期回调 | Cocos Creator](https://docs.cocos.com/creator/3.8/manual/zh/scripting/life-cycle-callbacks.html#生命周期回调)

# cocos的监听事件类型

## 鼠标事件 

==鼠标按下== ：Input.EventType.MOUSE_DOWN

==鼠标移动== ：Input.EventType.MOUSE_MOVE

==鼠标抬起== ：Input.EventType.MOUSE_UP

==鼠标持续按下== ：Input.EventType.MOUSE_WHEEL

## 触摸事件

==按下== ：Input.EventType.Touch_START

==移动== ：Input.EventType.Touch_MOVE

==抬起== ：Input.EventType.Touch_END

==持续按下==：Input.EventType.Touch_CANCEL

## 键盘事件

==键盘按下==：Input.EventType.KEY_DOWN

==键盘持续按下==：Input.EventType.KEY_PRESSING

==键盘释放==：Input.EventType.KEY_UP

## 碰撞事件

### 监听碰撞触发：组件.on（'触发类型'，执行函数，this）

监听碰撞触发类型：onTriggerEnter	开始触发

监听碰撞触发类型：onTriggerStay	持续触发

监听碰撞触发类型：onTriggerExit	结束触发

## 监听写法

input.on(监听类型，触发后执行的函数，this)

==监听开启和关闭要成对写上（防止内存泄漏）
