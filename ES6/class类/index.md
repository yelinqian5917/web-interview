# class 类

## 构造函数的属性

**静态属性**

静态属性是对象的私有属性，只能通过 （类名.属性） 的方式访问，而实例是无法访问的

**原型属性**

原型属性是构造函数和实例都可以访问的

**实例属性**

实例属性是属于实例自己的

## 一 概述

在 ES6 中，class (类)作为对象的模板被引入，可以通过 class 关键字定义类。

class 的本质是 function。

它可以看作一个语法糖，让对象原型的写法更加清晰、更像面向对象编程的语法。

## 二 定义

```js
// 匿名类
let Example = class {
  constructor(a) {
    this.a = a;
  }
};

// 命名类
let Example = class Example {
  constructor(a) {
    this.a = a;
  }
};

// 声明类
class Example {
  constructor(a) {
    this.a = a;
  }
}
```

注意要点：

- 不可重复声明。
- 类定义不会被提升，这意味着，必须在访问前对类进行定义，否则就会报错。

## 三 类的主体

### 1 属性

#### 静态属性

```js
class Example {
  // 新提案
  static a = 2;
}
```

#### 公共属性

```js
class Example {}
Example.prototype.a = 2;
```

#### 实例属性

```js
class Example {
  a = 2;
  constructor() {
    console.log(this.a);
  }
}
```

### 2 方法

constructor 方法是类的默认方法，创建类的实例化对象时被调用。

## 四 类的实例化

new

class 的实例化必须通过 new 关键字。

```js
class Example {}

let exam1 = Example();
// Class constructor Example cannot be invoked without 'new'
```
