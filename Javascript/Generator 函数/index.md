# Generator 函数
ES6 新引入了 Generator 函数，可以通过 yield 关键字，把函数的执行流挂起，为改变执行流程提供了可能，从而为异步编程提供解决方案。

## Generator 函数组成

Generator 有两个区分于普通函数的部分：
一是在 function 后面，函数名之前有个 * ；
函数内部有 yield 表达式。
其中 * 用来表示函数为 Generator 函数，yield 用来定义函数内部的状态。

```js
function* func(){
 console.log("one");
 yield '1';
 console.log("two");
 yield '2'; 
 console.log("three");
 return '3';
}
```

## 执行机制
调用 Generator 函数和调用普通函数一样，在函数名后面加上()即可，但是 Generator 函数不会像普通函数一样立即执行，而是返回一个指向内部状态对象的指针，所以要调用遍历器对象Iterator 的 next 方法，指针就会从函数头部或者上一次停下来的地方开始执行。

next();返回函数内部状态对象。含有俩个属性value,done
done执行完为true

## 函数返回的遍历器对象的方法




## 链接
https://blog.csdn.net/java_vava2/article/details/117118271