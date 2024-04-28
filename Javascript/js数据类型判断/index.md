# 数据类型判断

## js数据类型
基本类型：String、Number、Boolean、Symbol、Undefined、Null
引用类型：Object、Function 、Array、RegExp、Date

基本类型：也称为 简单类型，由于其占据空间固定，是简单的数据段，为了便于提升变量查询速度，将其存储在栈中，即按值访问。

引用类型: 也称为 复杂类型，由于其值的大小会改变，所以不能将其存放在栈中，否则会降低变量查询速度，因此，其值存储在堆(heap)中，而存储在变量处的值，是一个指针，指向存储对象的内存处，即按址访问。

## typeof 判断
typeof 是一个操作符，其右侧跟一个一元表达式，并返回这个表达式的数据类型。
- 返回的是一个字符串，判断的话需要跟字符串判断

```js
console.log(typeof myFun);      //function
console.log(typeof 1);       //number
console.log(typeof 'abc');   //string
console.log(typeof true);    //boolean
console.log(typeof undefined);  //undefined
console.log(typeof Symbol('a')); // symbol

// 下面这此，typeof 只有测出为 object，不能进一步判断它们的类型
console.log(typeof obj);          // object
console.log(typeof null);            //object ，无法准确测出是 null
console.log(typeof (new Date) );   //object  ，无法准确测出是 日期类型
console.log(typeof [1,2,3]);        //object ，无法准确测出是 数组
console.log(typeof (new RegExp()));  //object ，无法准确测出是 RegExp类型
```

说明：
typeof 可以准确测试出 number、string、boolean、undefined、function， 共5种数据类型。
对象、null、数组、Date、Array数组等类型， typeof 只能测出为object，不能进一步判断它们的类型。

总结：
对于基本类型，除 null 以外，均可以返回正确的结果。
对于引用类型，除 function 以外，一律返回 object 类型。
对于 null ，返回 object 类型。
对于 function 返回 function 类型。

- typeof 返回的也是一个字符串

## instanceof 判断

> 只能用来判断 复杂数据类型 ，因为 instanceof 是用于检测构造函数（右边）的 prototype 属性是否出现在某个实例对象（左边）的原型链上。

```js
console.log([] instanceof Array); // true
console.log({} instanceof Object);// true
console.log(new Date() instanceof Date); // true

//下面这3个判断也为true， 大家可能会疑问
console.log([] instanceof Object); // true
console.log(new Date() instanceof Object);// true
console.log(new Person instanceof Object);// true

console.log({} instanceof Array) // false
```
- 数组也属于Object类下面

### 多框架，多全局环境
instanceof 操作符的问题在于，它假定只有一个全局执行环境。如果网页中包含多个框架，那实际上就存在两个以上不同的全局执行环境，从而存在两个以上不同版本的构造函数。如果你从一个框架向另一个框架传入一个数组，那么传入的数组与在第二个框架中原生创建的数组分别具有各自不同的构造函数。

```js
var iframe = document.createElement('iframe');
document.body.appendChild(iframe);
xArray = window.frames[0].Array;
var arr = new xArray(1,2,3); // [1,2,3]
console.log(arr instanceof Array); // false
```

针对数组的这个问题，ES5 提供了 Array.isArray() 方法 。该方法用以确认某个对象本身是否为 Array 类型，而不区分该对象在哪个环境中创建。
Array.isArray() 本质上检测的是对象的 [[Class]] 值，
[[Class]] 是对象的一个内部属性，里面包含了对象的类型信息，其格式为 [object Xxx] ，Xxx 就是对应的具体类型 。
对于数组而言，[[Class]] 的值就是 [object Array] 。

## 使用 Object.prototype.toString.call （最准确的判断类型）

toString() 是 Object 的原型方法，调用该方法，默认返回当前对象的 [[Class]] 。这是一个内部属性，其格式为 [object Xxx] ，其中 ， Xxx 就是对象的类型。
对于 Object 对象，直接调用 toString() 就能返回 [object Object] 。而对于其他对象，则需要通过 call / apply 来调用才能返回正确的类型信息。

> 从实例我们可以看出该方法能判断基本类型，也能判断 Array 和 Function。

> 实例可见，对于Object对象，可以直接使用 toString() 方法，对于其他内置对象，Object.prototype.toString.call() 方法都能准确的判断出其类型。

结论：
Object.prototype.toString.call() 方法是判断类型的最准确的方法！

## constructor判断

> 函数的 constructor 是不稳定的，这个主要体现在自定义对象上，当开发者重写 prototype 后，原有的 constructor 引用会丢失，constructor 会默认为 Object 。

# 链接
https://blog.csdn.net/xiaojin21cen/article/details/126852702

# 问题思考
=== 可以比较引用俩个引用类型的数据结构吗
null 的判断方式

# 2. 比较运算符探究

## 先说 ===，这个比较简单：
1、如果类型不同，就[不相等]
2、如果两个都是数值，并且是同一个值，那么[相等]。
3、如果两个都是字符串，每个位置的字符都一样，那么[相等]；否则[不相等]。
4、如果两个值都是true，或者都是false，那么[相等]。
5、如果两个值都引用同一个对象或函数，那么[相等]；否则[不相等]。
6、如果两个值都是null，或者都是undefined，那么[相等]。 

## 再说 ==，根据以下规则：
1、如果两个值类型相同，进行 === 比较。
2、如果两个值类型不同，他们可能相等。根据下面规则进行类型转换再比较：
3、如果一个是null、一个是undefined，那么[相等]。
4、如果一个是字符串，一个是数值，把字符串转换成数值再进行比较。
5、如果任一值是 true，把它转换成 1 再比较；如果任一值是 false，把它转换成 0 再比较。
6、任何其他组合，都[不相等]。
