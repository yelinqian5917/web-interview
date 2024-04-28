# React Hooks的理解

## 一、是什么
Hook 是 React 16.8 的新增特性。它可以让你在不编写 class 的情况下使用 state 以及其他的 React 特性

至于为什么引入hook，官方给出的动机是解决长时间使用和维护react过程中常遇到的问题，例如：

- 难以重用和共享组件中的与状态相关的逻辑
- 逻辑复杂的组件难以开发与维护，当我们的组件需要处理多个互不相关的 local state 时，每个生命周期函数中可能会包含着各种互不相关的逻辑在里面
- 类组件中的this增加学习成本，类组件在基于现有工具的优化上存在些许问题
- 由于业务变动，函数组件不得不改为类组件等等
- 在以前，函数组件也被称为无状态的组件，只负责渲染的一些工作

因此，现在的函数组件也可以是有状态的组件，内部也可以维护自身的状态以及做一些逻辑方面的处理

## 二、有哪些

上面讲到，Hooks让我们的函数组件拥有了类组件的特性，例如组件内的状态、生命周期

最常见的hooks有如下：

- useState
- useEffect
- 其他


**useState**

首先给出一个例子，如下：

```jsx
import React, { useState } from 'react';

function Example() {
  // 声明一个叫 "count" 的 state 变量
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p >
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```


**useEffect**

useEffect可以让我们在函数组件中进行一些带有副作用的操作

同样给出一个计时器示例：

```jsx
import React, { useState, useEffect } from 'react';
function Example() {
  const [count, setCount] = useState(0);
 
  useEffect(() => {    document.title = `You clicked ${count} times`;  });
  return (
    <div>
      <p>You clicked {count} times</p >
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

**其它 hooks**

在组件通信过程中可以使用useContext，refs学习中我们也用到了useRef获取DOM结构......

还有很多额外的hooks，如：

- useReducer
- useCallback
- useMemo
- useRef

## 三、解决什么

通过对上面的初步认识，可以看到hooks能够更容易解决状态相关的重用的问题：

- 每调用useHook一次都会生成一份独立的状态

- 通过自定义hook能够更好的封装我们的功能

编写hooks为函数式编程，每个功能都包裹在函数中，整体风格更清爽，更优雅

hooks的出现，使函数组件的功能得到了扩充，拥有了类组件相似的功能，在我们日常使用中，使用hooks能够解决大多数问题，并且还拥有代码复用机制，因此优先考虑hooks