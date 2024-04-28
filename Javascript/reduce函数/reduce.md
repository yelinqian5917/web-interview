# reduce()函数
---

## 定义
reduce() 方法接收一个函数作为累加器，数组中的每个值（从左到右）开始缩减，最终计算为一个值。
reduce() 可以作为一个高阶函数，用于函数的 compose。
注意: reduce() 对于空数组是不会执行回调函数的。

## 语法
```
array.reduce(function(total, currentValue, currentIndex, arr), initialValue)
通常情况下，第一个参数 使用  prev
arr.reduce(function(prev,cur,index,arr){
...
}, init);
```

> function(total, currentValue, currentIndex, arr) 
> - 必须用于执行每一个数组的函数
> - total 初始值 或者计算后的返回值   previous
> - currentValue  必选当前的元素  current
> - currentIndex 可选 当前元素的索引
> - arr  当前元素的数组

> initialValue
> - initialValue 可选传递给函数的初始值

## 重点

 - **当没有传入初始值时，prev是从数组中第一个元素开始的，cur 是数组第二个元素。**