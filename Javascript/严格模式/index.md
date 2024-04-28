# 严格模式
## 什么是严格模式
JavaScript 严格模式（strict mode）即在严格的条件下运行。
## 为什么要使用严格模式
- 消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为;
- 消除代码运行的一些不安全之处，保证代码运行的安全；
- 提高编译器效率，增加运行速度；
- 为未来新版本的Javascript做好铺垫。
- "严格模式"体现了Javascript更合理、更安全、更严谨的发展方向，包括IE 10在内的主流浏览器，都已经支持它，许多大项目已经开始全面拥抱它。
- 另一方面，同样的代码，在"严格模式"中，可能会有不一样的运行结果；一些在"正常模式"下可以运行的语句，在"严格模式"下将不能运行。掌握这些内容，有助于更细致深入地理解Javascript，让你变成一个更好的程序员。
## 如何使用严格模式
严格模式通过在脚本或函数的头部添加 use strict; 表达式来声明。
## 严格模式的限制
### 1.不允许使用未声明的变量
```js
"use strict";
x = 3.14;                // 报错 (x 未定义)
```
### 2.不允许删除变量或对象,函数。
```js
"use strict";
var x = 3.14;
delete x;                // 报错
"use strict";
function x(p1, p2) {};
delete x;                // 报错 
```
### 3.不允许变量重名:
```js
"use strict";
function x(p1, p1) {};   // 报错
```
### 4.不允许使用八进制，不允许使用转义字符:
```js
"use strict";
var x = 010;             // 报错
"use strict";
var x = \010;            // 报错
```
### 5.禁止this关键字指向全局对象。
```js
function f(){
    return !this;
} 
// 返回false，因为"this"指向全局对象，"!this"就是false

function f(){ 
    "use strict";
    return !this;
} 
// 返回true，因为严格模式下，this的值为undefined，所以"!this"为true。
// 因此，使用构造函数时，如果忘了加new，this不再指向全局对象，而是报错。
function f(){
    "use strict";
    this.a = 1;
};
f();// 报错，this未定义
```
### 6.变量名不能使用 "eval"  "arguments"字符串:
```js
"use strict";
var arguments = 3.14;    // 报错
"use strict";
var eval = 3.14;         // 报错
```




