# 事件循环
## 执行栈与事件队列

1. 执行栈：调用方法时，js会生成一个与这个方法对应的执行环境（执行上下文）
> 执行环境：
> - 存在着这个方法的私有作用域
> - 上层作用域的指向
> - 方法的参数
> - 这个作用域的this对象。
> - 这个作用域中定义的变量

2. 事件循环： 被放入事件队列不会立刻执行其回调，而是等待当前执行栈中的所有任务都执行完毕， 主线程处于闲置状态时，主线程会去查找事件队列是否有任务。如果有，那么主线程会从中取出排在第一位的事件，并把这个事件对应的回调放入执行栈中，然后执行其中的同步代码，如此反复，这样就形成了一个无限的循环。这就是这个过程被称为 事件循环（Event Loop）；

## 一 同步任务与异步任务
任务分为： 同步任务 异步任务
- 异步任务放入事件队列里面执行

## 二 宏任务与微任务
> 事件队列里面又分为宏任务队列，微任务队列。
> 宏队列里面放的是宏任务，微队列里面放的是微任务。
> - 微队列优先级是高于宏队列优先级。

- 宏任务主要包含：script( 整体代码)、setTimeout、setInterval、I/O、UI 交互事件、setImmediate(Node.js 环境)
- 微任务主要包含：Promise、MutaionObserver、process.nextTick(Node.js 环境)

```js
// 宏任务
console.log('1')

// setTimeout 的回调是 宏任务，进入回调队列排队
setTimeout(() => {

    // 宏任务
    console.log('4')
    
    // setTimeout 的回调是 宏任务2，进入回调队列排队
    setTimeout(() => {
        console.log('7')
    }, 0)
    
    // Promise 的回调是 微任务，本轮调用末尾直接执行
    Promise.resolve()
        .then(() => {
            console.log('6')
        })
    console.log('5')
}, 0)

// Promise 的回调是 微任务，本轮调用末尾直接执行
Promise.resolve()
    .then(() => {
        console.log('3')
    })
    
console.log('2')
```

## 补充总结 异步代码里面的异步代码执行顺序

```js
    setTimeout(() => {
      // 微任务
      console.log("1");
      setTimeout(() => {
        // 微任务
        console.log("2");
        setTimeout(() => {
          // 微任务
          console.log("3");
        });
      });
    });

    setTimeout(() => {
      // 微任务
      console.log("4");
      setTimeout(() => {
        // 微任务
        console.log("5");
      });
    });
```

<!-- 主线程  set1 set2
1 4 同步任务执行完
执行第一个的 异步 第二个的异步，他们成为同步代码
 -->



执行顺序 1 4 2 5 3

主线程执行完毕，然后从事件队列里面找异步任务，放入主线程执行

## 图

```mermaid
    
 graph *LR;*  
 A-->B  
 B-->C  
 C-->D  
 D-->A 
 ```

​

