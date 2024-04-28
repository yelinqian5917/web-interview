# Redux 的理解

## 一 概念

React 是用于构建用户界面的，帮助我们解决渲染 DOM 的过程

而在整个应用中会存在很多个组件，每个组件的 state 是由自身进行管理，包括组件定义自身的 state、组件之间的通信通过 props 传递、使用 Context 实现数据共享

如果让每个组件都存储自身相关的状态，理论上来讲不会影响应用的运行，但在开发及后续维护阶段，我们将花费大量精力去查询状态的变化过程

这种情况下，如果将所有的状态进行集中管理，当需要更新状态的时候，仅需要对这个管理集中处理，而不用去关心状态是如何分发到每一个组件内部的

redux 就是一个实现上述集中管理的容器，遵循三大基本原则：

- 单一数据源
- state 是只读的
- 使用纯函数来执行修改

> 注意的是，redux 并不是只应用在 react 中，还与其他界面库一起使用，如 Vue

## 二 工作原理

redux 要求我们把数据都放在 store 公共存储空间

一个组件改变了 store 里的数据内容，其他组件就能感知到 store 的变化，再来取数据，从而间接的实现了这些数据传递的功能

## 三、如何使用

```js
const redux = require("redux");

const initialState = {
  counter: 0,
};

// 创建reducer
const reducer = (state = initialState, action) => {
  switch (action.type) {
    case "INCREMENT":
      return { ...state, counter: state.counter + 1 };
    case "DECREMENT":
      return { ...state, counter: state.counter - 1 };
    case "ADD_NUMBER":
      return { ...state, counter: state.counter + action.number };
    default:
      return state;
  }
};

// 根据reducer创建store
const store = redux.createStore(reducer);

store.subscribe(() => {
  console.log(store.getState());
});

// 修改store中的state
store.dispatch({
  type: "INCREMENT",
});
// console.log(store.getState());

store.dispatch({
  type: "DECREMENT",
});
// console.log(store.getState());

store.dispatch({
  type: "ADD_NUMBER",
  number: 5,
});
// console.log(store.getState());
```

## 四 小结

- createStore 可以帮助创建 store
- store.dispatch 帮助派发 action , action 会传递给 store
- store.getState 这个方法可以帮助获取 store 里边所有的数据内容
- store.subscrible 方法订阅 store 的改变，只要 store 发生改变， store.subscrible 这个函数接收的这个回调函数就会被执行
