# this指向
## 概念
1. 在js中，this的意思为“这个;当前”，是一个指针型变量，它动态指向当前**函数**的运行环境。
2. 在不同的场景中调用同一个函数，this的指向也可能会发生变化，但是它永远指向其所在函数的真实调用者；如果没有调用者，就指向全局对象window。
3. this是一个只针对函数的概念，与对象无关。

> 普通函数：关于this，谁调用就指向谁，没有调用者，就指向全局对象window。
> 箭头函数：箭头函数的this指向于函数作用域所用的对象。

## 全局环境下的this指向
在全局作用域下，this始终指向全局对象window，无论是否是严格模式！
```js
console.log(this)
window.console.log(this)
```

## 函数内的this
普通函数内的this分为两种情况，严格模式下和非严格模式下。

1. 严格模式
```js
function test(){
  'use strict'
  console.log(this)
}
test(); // undefinded
window.test(); // window
```
直接test()调用函数,this指向undefined，window.test()调用函数this指向window。因此，在严格模式下， 我们对代码的的调用必须严格的写出被调用的函数的对象，不可以有省略或者说简写。

2. 非严格模式下

```js
function test(){
  console.log(this)
}
test(); // window
window.test(); // window
```

非严格模式下，通过test()和window.test()调用函数对象，this都指向window。

## 对象中的this
> 对象内部方法的this指向调用这些方法的对象，也就是谁调用就指向谁。

```js
const obj = {
  name:'姓名',
  func:function (){
    const name = '姓名1'
    console.log(this)
  },
  obj2:function (){
    const name = '姓名2';
    func2:function (){
      const name = '姓名2'
       console.log(this)
    }
  }
}
obj.func();
obj.obj2.func2();
```

函数的定义位置不影响其this指向，this指向只和调用函数的对象有关。
多层嵌套的对象，内部方法的this指向离被调用函数最近的对象。

## 箭头函数中的this
> 箭头函数：this指向于函数作用域所用的对象。

- 箭头函数的重要特征：箭头函数中没有this和arguments，是真的没有！

- 箭头函数没有自己的this指向，它会捕获自己定义所处的外层执行环境，并且继承这个this值,指向当前定义时所在的对象。箭头函数的this指向在被定义的时候就确定了，之后永远都不会改变。即使使用call()、apply()、bind()等方法改变this指向也不可以。

```js
const obj = {
  name:'',
  func:()=>{
    console.log(this)
  }
}
// 这里的this 指向window 箭头函数初始化捕获执行上下文的this，不随使用者改变，
// 对象没有this，所以继续向上面捕获 拿到window
```

## 构造函数中的this
> 构造函数中的this是指向实例。构造函数中的this指向构造函数下创建的实例。


## 原型链中的this
> this这个值在一个继承机制中，仍然是指向它原本属于的对象，而不是从原型链上找到它时，它所属于的对象。

## 改变this指向的方法 call apply bind
