# Promise

## 一 概述

是异步编程的一种解决方案。
从语法上说，Promise 是一个对象，从它可以获取异步操作的消息。

> 所谓 Promise，简单说就是一个容器，里面保存着某个未来才会结束的事件（通常是一个异步操作）的结果。从语法上说，Promise 是一个对象，从它可以获取异步操作的消息。Promise 提供统一的 API，各种异步操作都可以用同样的方法进行处理。

## 二 Promise 状态

1. 初始态 pending
2. 成功态 resolved--也叫 fulfilled
3. 失败态 rejected

### 状态的缺点：

无法取消 Promise ，一旦新建它就会立即执行，无法中途取消。
如果不设置回调函数，Promise 内部抛出的错误，不会反应到外部。
当处于 pending 状态时，无法得知目前进展到哪一个阶段（刚刚开始还是即将完成）。

## 三 PromiseAPI

1. Promise.then
2. Promise.catch
3. Promise.all
   所有异步操作执行完后并且执行结果都是成功的时候才执行回调。
4. Promise.race
   谁先执行完成就先执行回调。先执行完的不管是进行了 race 的成功回调还是失败回调，其余的将不会再进入 race 的任何回调
5. Promise.resolve
   说明: 返回一个成功/失败的 promise 对象
6. Promise.reject
   说明: 返回一个失败的 promise 对象

> promise 源码实现要阅读
