# React 的事件机制

## 一 介绍

React 基于浏览器的事件机制自身实现了一套事件机制，包括事件注册、事件的合成、事件冒泡、事件派发等
在 React 中这套事件机制被称之为合成事件

**_合成事件（SyntheticEvent）_**

合成事件是 React 模拟原生 DOM 事件所有能力的一个事件对象，即浏览器原生事件的跨浏览器包装器

```jsx
const button = <button onClick={handleClick}>按钮</button>;
```

如果想要获得原生 DOM 事件，可以通过 e.nativeEvent 属性获取

```jsx
const handleClick = (e) => console.log(e.nativeEvent);
const button = <button onClick={handleClick}>按钮</button>;
```

虽然 onclick 看似绑定到 DOM 元素上，**但实际并不会把事件代理函数直接绑定到真实的节点上**，而是把所有的事件绑定到结构的最外层，使用一个统一的事件去监听

## 二 执行顺序

```jsx
import React from "react";
class App extends React.Component {
  constructor(props) {
    super(props);
    this.parentRef = React.createRef();
    this.childRef = React.createRef();
  }
  componentDidMount() {
    console.log("React componentDidMount！");
    this.parentRef.current?.addEventListener("click", () => {
      console.log("原生事件：父元素 DOM 事件监听！");
    });
    this.childRef.current?.addEventListener("click", () => {
      console.log("原生事件：子元素 DOM 事件监听！");
    });
    document.addEventListener("click", (e) => {
      console.log("原生事件：document DOM 事件监听！");
    });
  }
  parentClickFun = () => {
    console.log("React 事件：父元素事件监听！");
  };
  childClickFun = () => {
    console.log("React 事件：子元素事件监听！");
  };
  render() {
    return (
      <div ref={this.parentRef} onClick={this.parentClickFun}>
        <div ref={this.childRef} onClick={this.childClickFun}>
          分析事件执行顺序
        </div>
      </div>
    );
  }
}
export default App;
```

输出顺序为：

原生事件：子元素 DOM 事件监听！
原生事件：父元素 DOM 事件监听！
React 事件：子元素事件监听！
React 事件：父元素事件监听！
原生事件：document DOM 事件监听！

**_总结：_**

- React 所有事件都挂载在 document 对象上
- 当真实 DOM 元素触发事件，会冒泡到 document 对象后，再处理 React 事件
- 所以会先执行原生事件，然后处理 React 事件
- 最后真正执行 document 上挂载的事件

**_阻止事件冒泡_**

- 阻止合成事件间的冒泡，用 e.stopPropagation()

- 阻止合成事件与最外层 document 上的事件间的冒泡，用 e.nativeEvent.stopImmediatePropagation()

- 阻止合成事件与除最外层 document 上的原生事件上的冒泡，通过判断 e.target 来避免

## 三 总结

- React 上注册的事件最终会绑定在 document 这个 DOM 上，而不是 React 组件对应的 DOM(减少内存开销就是因为所有的事件都绑定在 document 上，其他节点没有绑定事件)

- React 自身实现了一套事件冒泡机制，所以这也就是为什么我们 event.stopPropagation()无效的原因。

- React 通过队列的形式，从触发的组件向父组件回溯，然后调用他们 JSX 中定义的 callback

- React 有一套自己的合成事件 SyntheticEvent
