# 环境搭建

## 执行命令：

```cmd
npx create-react-app react-basic
npx Node.js 工具命令，查找并执行后续的包命令
create-react-app 核心包（固定写法），用于创建React项目
react-basic React项目的名称（可以自定义）
```

## 初始文件内容

![image-20260715220959366](E:\文档\笔记\图片\image-20260715220959366.png)

1.将不太需要的文件清除

![image-20260715221137945](E:\文档\笔记\图片\image-20260715221137945.png)

2.文件内容也可以适当的清除一些不必要的代码

app.js

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)

function App() {
  return <div className="App">this is my app</div>;
}

export default App;
```

index.js

```js
// 项目的入口 从这里开始

// React必要的两个核心包
import React from "react";
import ReactDOM from "react-dom/client";

//导入项目的根组件
import App from "./App";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);

```

### 官方文档

```
https://zh-hans.react.dev/learn/creating-a-react-app
```

# JSX基础

#### 概念

JSX是JavaScript和XML（html）的缩写，表示在js代码中编写html模板结构，他是React中编写UI模板的方式

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)
const message = "this is my app";

function App() {
  return (
    <div className="App">
      <h1>this is my react</h1>
      [message]
    </div>
  );
}

export default App;

```

优势

1.HTML的声明式模板写法

2.JS的可编程能力

#### JSX中使用JS表达式

在JSX中可以通过大括号识别JavaScript中的表达式，比如常见的变量，函数调用，方法调用等等

1. 使用引号传递字符串
2. 使用JavaScript变量
3. 函数调用和方法调用
4. 使用JavaScript对象

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)
const count = "this is my app";
function getName() {
  return "我是小涛";
}

function App() {
  return (
    <div className="App">
      {/* {使用引号传递字符串 } */}
      {"my is message"}
      {/* {识别js变量} */}
      {count}
      {/* {函数调用} */}
      {getName()}
      {/* {方法调用} */}
      {new Date().getDate()}
      {/* {使用js对象} */}
      <div style={{ color: "red" }}>我是红色的</div>
    </div>
  );
}

export default App;
```

==注意：if语句，switch语句，变量声明属于语句，不是表达式，不能出现在{}中==

#### JSX中实现列表渲染

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)
const list = [
  { id: 1001, name: "vue" },
  { id: 1002, name: "roect" },
  { id: 1003, name: "js" },
];

function App() {
  return (
    <div className="App">
      this is App
      {/* {渲染列表} */}
      {/* {map 循环那个结构return结构} */}
      {/* {注意：加上一个独一无二的key 字符串或者number id} */}
      {/* {key的作用：React框架内部使用 用于提升性能的} */}
      <ul>
        {list.map((item) => (
          <li key={item.id}>{item.name}</li>
        ))}
      </ul>
    </div>
  );
}

export default App;

```

#### JSX中实现条件渲染

语法：在React中，可以通过逻辑与原酸符&&，三元表达式（?:）实现基础的条件渲染

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)
const isLogin = true;

function App() {
  return (
    <div className="App">
      {/* {逻辑与&&} */}
      {isLogin && <span>this is my app</span>}
      {/* {三元运算符} */}
      {isLogin ? <span>jack</span> : <span>looding...</span>}
    </div>
  );
}

export default App;

```

#### JSX中实现复杂条件渲染

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)
const articleType = 2; // 0,1,2分别代表着对应的模式

function getArticleTem() {
  if (articleType === 0) {
    return <span>我是无图模式</span>;
  } else if (articleType === 1) {
    return <span>我是单图模式</span>;
  } else if (articleType === 2) {
    return <span>我是多图模式</span>;
  }
}

function App() {
  return <div className="App">{getArticleTem()}</div>;
}

export default App;

```

#### React基础事件绑定

语法：on+事件名称={事件处理程序}，整体上遵循驼峰命名法

基础使用：

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)

function App() {
  const handleClick = () => {
    console.log("button被点击了");
  };
  return (
    <div className="App">
      <button onClick={handleClick}>click me</button>
    </div>
  );
}

export default App;

```

输出触发的方式：

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)

function App() {
  const handleClick = (e) => {
    console.log("button被点击了", e);
  };
  return (
    <div className="App">
      <button onClick={(e) => handleClick(e)}>click me</button>
    </div>
  );
}

export default App;

```

绑定事件传参：

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)

function App() {
  const handleClick = (name) => {
    console.log("button被点击了", name);
  };
  return (
    <div className="App">
      <button onClick={() => handleClick("jack")}>click me</button>
    </div>
  );
}

export default App;

```

结合：

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)

function App() {
  const handleClick = (name, e) => {
    console.log("button被点击了", name, e);
  };
  return (
    <div className="App">
      <button onClick={(e) => handleClick("jack", e)}>click me</button>
    </div>
  );
}

export default App;

```

##组件

概念：一个组件就是用户界面的一部分，他可以用自己的逻辑和外观，组件之间可以相互嵌套，也可以多次复用

### React组件

在React中，一个组件就是首字母大写的函数，内部存放了组件和逻辑和视图UI，渲染组件只需要把组件当成标签来写即可

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)

function Button() {
  //业务逻辑组件逻辑
  return <button>clikc me</button>;
}
function App() {
  return (
    <div className="App">
      {/* {自闭合} */}
      <Button />
      {/* {成对标签} */}
      <Button></Button>
    </div>
  );
}

export default App;

```

箭头函数也是可以正常使用的

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)

const Button = () => {
  //业务逻辑组件逻辑
  return <button>clikc me</button>;
};
function App() {
  return (
    <div className="App">
      {/* {自闭合} */}
      <Button />
      {/* {成对标签} */}
      <Button></Button>
    </div>
  );
}

export default App;

```

### 组件基础样式方案

#### 行内样式（不推荐）

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)

function App() {
  return (
    <div className="App">
      {/* {行内样式} */}
      <span style={{ color: "red",}}>this is my app</span>
    </div>
  );
}

export default App;
//或者
// 项目的根目录
// app -> index.js -> public/index.html(root)

const style = {
  color: "red",
  fontSize: "50px",
};

function App() {
  return (
    <div className="App">
      {/* {行内样式} */}
      <span style={style}>this is my app</span>
    </div>
  );
}

export default App;

```



#### class类名控制

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)
import "./index.css";

function App() {
  return (
    <div className="App">
      {/* {通过class类名控制} */}
      <span className="foo">this is my app</span>
    </div>
  );
}

export default App;
// css
.foo {
  color: blue;
  font-size: 50px;
}

```



## useState基础使用

useState是一个ReactHook(函数),他允许我们向组件添加一个状态变量，从而孔子影响组件的渲染结果

基础使用：

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)
import { useState } from "react"; //导入

function App() {
  // 1.调用useStata添加一个状态变量
  //count状态变量
  //setCount修改状态变量的方法
  const [count, setCount] = useState(0);
  //2.点击事件的回调
  const handleClick = () => {
    //作用：1，用传入的新值修改count
    //2，重新使用的新的count渲染UI
    setCount(count + 1);
  };
  return (
    <div className="App">
      <button onClick={handleClick}>{count}</button>
    </div>
  );
}

export default App;

```

### userState修改状态的规则

#### 状态不可变

在React中，状态被认为式只读的，我们因该始终替换他不是修改他，直接修改状态不能引发视图更新

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)
import { useState } from "react"; //导入

function App() {
  // 1.调用useStata添加一个状态变量
  //count状态变量
  //setCount修改状态变量的方法
  const [count, setCount] = useState(0);
  //2.点击事件的回调
  const handleClick = () => {
    //作用：1，用传入的新值修改count
    //2，重新使用的新的count渲染UI
    setCount(count + 1);
    // count ++ // 错误写法
  };
  return (
    <div className="App">
      <button onClick={handleClick}>{count}</button>
    </div>
  );
}

export default App;

```



#### 修改对象状态

规则：对于对象类型的状态变量，应该始终传给set方法一个全新的对象雷进行修改

```js
// 项目的根目录
// app -> index.js -> public/index.html(root)
import { useState } from "react"; //导入

function App() {
  // 1.调用useStata添加一个状态变量
  //count状态变量
  //setCount修改状态变量的方法
  const [count, setCount] = useState(0);
  const [form, setForm] = useState({ name: "小涛" });
  //2.点击事件的回调
  const handleClick = () => {
    //作用：1，用传入的新值修改count
    //2，重新使用的新的count渲染UI
    setCount(count + 1);
    // count ++ // 错误写法
  };
  const changeForm = () => {
    //错误写法：
    // form.name = '周光明'
    //正确写法
    setForm({
      ...form,
      name: "周光明",
    });
  };
  return (
    <div className="App">
      <button onClick={handleClick}>{count}</button>
      <button onClick={changeForm}>修改form{form.name}</button>
    </div>
  );
}

export default App;

```

## classnames优化类名控制

classnames是一个简单的js库，可以非常方便的通过条件动态控制class类名的显示

## 受控表单绑定

==概念==：使用React组件的状态（useState）控制表单的状态

```js
import { useState } from "react";

//1.声明一个react状态 -useState
//2.核心绑定流程
//1.通过value属性绑定react状态
//2.绑定onchange事件 通过事件参数e拿到输入框的值 反向修改到react状态
function App() {
  const [inputValue, setInputValue] = useState("");
  return (
    <div className="App">
      <input
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
      ></input>
    </div>
  );
}

export default App;

```

## React中获取DOM

在React组件中获取/操作DOM，需要使用useRef钩子函数，分为两步：

1.使用useRef创建ref对象，并与jsx绑定

```js
const inputRef = useRef(null)
<input type = "text" ref = {inputRef}>
```

2.在DOM可用时，通过inputRef.current拿到DOM对象

```js
console.log(inputRef.current)
```

```js
import { useRef } from "react";
// 1.useRef生成ref对象 绑定到dom标签身上
// 2.dom可用时，refcurrent获取dom
// 渲染完毕之后dom生效之后才可用
function App() {
  const inputRef = useRef(null);
  const showDom = () => {
    console.dir(inputRef.current);
  };
  return (
    <div className="App">
      <input ref={inputRef} type="text" />
      <button onClick={showDom}>点击我获取DOM</button>
    </div>
  );
}

export default App;

```

## 组件通信

### 父传字

#### 基础实现

```js
// 父传子
//1.父组件传递数据 子组件标签上绑定属性
//2.子组件接收数据 props的参数
function Son(props) {
    // props：对象里面包含了父组件传递过来的所有的数据
    //{name:父组件中的数据}
  return <div>this is my son:{props.name}</div>;
}

function App() {
  return (
    <div className="App">
      <Son name="john" />
    </div>
  );
}

export default App;

```

#### props说明

1. props可传递任意的数据

   数字，字符串，布尔值，数组，对象，函数，JSX

2. props是只读对象

   子组件只能读取props中的数据，不能直接进行修改，父组件的数据只能由父组件修改 

   ```js
   function Son(props) {
     return (
       <div>
         this is my son:{props.name},JSX:{props.child}
       </div>
     );
   }
   
   function App() {
     return (
       <div className="App">
         <Son
           name="john"
           age={18}
           isStudent={true}
           list={["vue", "react", "angular"]}
           obj={{ name: "小猫", age: 18 }}
           cb={() => console.log("this is a callback function")}
           child={<div>this is a child element</div>}
         />
       </div>
     );
   }
   
   export default App;
   
   ```

   #### 特殊的prop children

   当我们把内容嵌套在子组件标签中，父组件会自动在名为children的prop属性中接收该内容

   ```js
   function Son(props) {
     return <div>this is my son,JSX props: {props.children}</div>;
   }
   
   function App() {
     return (
       <div className="App">
         <Son>this is my father</Son>
       </div>
     );
   }
   
   export default App;
   
   ```

   

### 子传父

```js
// 核心：在子组件中调用父组件中的函数并传递实参
import { useState } from "react";

function Son({ onGetSonMsg }) {
  const sonMsg = "this is my son";
  return (
    <div>
      this is my son
      <button onClick={() => onGetSonMsg(sonMsg)}>sendMsg</button>
    </div>
  );
}

function App() {
  const [msg, setMsg] = useState("");
  const getMsg = (msg) => {
    console.log(msg);
    setMsg(msg);
  };
  return (
    <div className="App">
      this is my father, {msg}
      <Son onGetSonMsg={getMsg} />
    </div>
  );
}

export default App;

```

### 兄弟组件通信

使用状态提升实现兄弟通信

实现思路：借助“状态提升”机制，通过父组件进行兄弟之间的数据传递

```js
import { useState } from "react";

function A({ onGetName }) {
  const name = "this is A name";
  return (
    <div>
      this is A component
      <button onClick={() => onGetName(name)}>click me</button>
    </div>
  );
}

function B({ name }) {
  return <div>this is B component, {name}</div>;
}

function App() {
  const [name, setName] = useState("");
  const getName = (name) => {
    console.log(name);
    setName(name);
  };
  return (
    <div className="App">
      this is my father component
      <A onGetName={getName} />
      <B name={name} />
    </div>
  );
}

export default App;

```

