# React 生命周期

## 1. 生命周期

跟 Vue 一样，React 整个组件生命周期包括从创建、初始化数据、编译模板、挂载 Dom→ 渲染、更新 → 渲染、卸载等一系列过程

## 2. 流程

> 这里主要讲述 react16.4 之后的生命周期，可以分成三个阶段：

- 创建阶段
- 更新阶段
- 卸载阶段

### 2.1 创建阶段

创建阶段主要分成了以下几个生命周期方法：

- constructor
- getDerivedStateFromProps
- render
- componentDidMount

> 注意： 不要在 render 里面 setState, 否则会触发死循环导致内存崩溃
> 为什么？

### 2.2 更新阶段

该阶段的函数主要为如下方法：

- getDerivedStateFromProps
- shouldComponentUpdate
- render
- getSnapshotBeforeUpdate
- componentDidUpdate

### 2.3 卸载阶段

- componentWillUnmount

## 3. 总结

新版生命周期，与旧版生命周期比较。

React 的生命周期方法包括 componentDidMount, componentDidUpdate, componentWillUnmount, 等等。在 React 16.8 之后的版本中，通过引入 Hooks（如 useEffect），React 可以在函数组件中实现相同的功能。
