# typeScript

## 什么是 TypeScript，为什么要用它？

TypeScript 是一种静态类型的面向对象的编程语言，它是 JavaScript 框架 之一

## TypeScript 的主要特点是什么？

1. 跨平台：Typescript 编译器可以安装在任何操作系统上

- 静态类型
- 接口
- 类和继承
- 模块
- 命名空间
- 装饰器
- 泛型
- 异步/等待

## TypeScript 与 JavaScript 有何不同？

TypeScript 是 JavaScript 的超集，这意味着所有有效的 JavaScript 代码也是有效的 TypeScript 代码。然而，TypeScript 增加了 JavaScript 所没有的特性，例如静态类型和基于类的面向对象编程。
TypeScript 还具有更严格的类型系统，允许在编译时而不是运行时检测到错误。

## TypeScript 如何与其他工具和库集成？

TypeScript 可以与 Angular 和 React 等流行的前端框架以及用于服务器端开发的 Node.js 等各种工具和库一起使用。
TypeScript 代码可以编译成纯 JavaScript，使其与任何支持 JavaScript 的环境兼容。

## TypeScript 是如何进行类型检查的？

Typescript 使用类型系统在编译时执行类型检查。这可以通过允许在代码运行之前检测到错误来提高代码的可靠性和可维护性。
TypeScript 的类型系统是可选的，因此，开发人员可以随心所欲地使用它。

## 什么是 TypeScript 接口？

TypeScript 接口定义了指定对象外观的契约。它用于在对象上强制执行某些构造或保证对象实现某些属性或方法。
接口可用于使代码可重用和紧凑，或者通过使代码的意图更清晰来使代码更具可读性。

> 接口（interface）: 可以使用接口来描述对象、命名和参数化对象的类型，以及将现有的命名对象类型组成新的对象类型。

```ts
interface Employee {
  firstName: string;
  lastName: string;
  fullName(): string;
}
```

## 什么是 TypeScript 类？它们与 JavaScript 类有何不同？

TypeScript 类提供了一种创建具有特定属性和方法的对象的方法。它们类似于其他面向对象编程语言中的类，提供了一种编写可重用和模块化代码的方法。
TypeScript 中的类是 JavaScript 原型的语法糖，并被翻译成 JavaScript 的构造函数。

## 如何在 TypeScript 中定义类？

TypeScript 中的类可以使用 class 关键字定义，后跟类名。可以使用构造函数方法和公共或私有关键字将属性和方法添加到类中。

## 什么是 TypeScript 命名空间？它与模块有何不同？

TypeScript 命名空间提供了一种以类似于模块的方式组织代码的方式，但语法略有不同。
命名空间允许将代码分组在通用名称下，从而避免名称冲突。但是，在 TypeScript 中，命名空间不像模块那样常用。
因为模块提供的功能更多，适合大型项目。

```ts
namespace MyApp {
  export function doSomething() {
    console.log("Doing something");
  }
}

MyApp.doSomething(); // Doing something
```

## 什么是 TypeScript 装饰器？

TypeScript 装饰器是一种向类、方法或属性添加额外行为的方法。
装饰器作为函数实现，可以使用@符号来应用。
装饰器可用于向类或方法添加元数据或添加功能等。

```ts
function Logger(target: any, propertyKey: string) {
  console.log(`Calling ${propertyKey}`);
}

class MyClass {
  @Logger
  greet() {
    console.log("Hello");
  }
}

const instance = new MyClass();
instance.greet(); // Calling greet \n Hello
```

## 什么是 TypeScript 中的泛型，它们是如何使用的？

TypeScript 中的泛型提供了一种通过编写可处理不同类型的函数、类和接口来编写可重用且灵活的代码的方法。

泛型可以用来实现类型安全，提高代码的可读性和可维护性。

```ts
function identity<T>(arg: T): T {
  return arg;
}

const result = identity<string>("Hello");
console.log(result); // Hello
```

> 泛型： 可以支持不特定的数据类型。 要求： 传入的参数和返回的参数一致

## 什么时候使用 TypeScript any type？

TypeScript any type 用于指示变量、函数或参数可以保存任何类型的值。
在处理外部库或不是用 TypeScript 编写的代码时，或者在需要禁用特定变量的类型检查时，任何类型都是有用的。
但是，尽可能使用更具体的类型通常是个好主意。这是因为使用 any 可能会削弱使用 TypeScript 类型系统的好处。

## type 和 interface 的区别异同？

Type 又叫类型别名（type alias）,作用是给一个类型起一个新名字，不仅支持 interface 定义的对象结构，还支持基本类型、联合类型、交叉类型、元组等任何你需要手写的类型。

```ts
type num = number; // 基本类型
type stringOrNum = string | number; // 联合类型
type person = { name: string }; // 对象类型
type user = person & { age: number }; // 交叉类型
type data = [string, number]; // 元组
type fun = () => void; // 函数类型
```

相同点： 1.都可以用来描述一个对象或者函数 2.都可以进行拓展

不同点： 1.类型别名可以用于其它类型 （联合类型、元组类型、基本类型（原始值）），interface 不支持
2.interface 可以多次定义来合并声明，type 不支持
3.type 能使用 in 关键字生成映射类型，但 interface 不行 4.默认导出方式不同 5.在 type 中可以使用泛型
6.type 可以使用 typeof 获取实例类型

## TypeScript 的未知类型是什么，什么时候用？

TypeScript 的未知类型用于指示变量、函数或参数可以包含任何类型的值，但在使用前需要进行类型检查。
unknown 类型的限制比任何类型都多，当需要在使用前可靠地检查值时才有效。
unknown 声明之后不可以修改

TypeScript 中的未知类型是一种特殊的类型，它用于表示我们不知道变量的类型是什么。与 any 类型不同，未知类型不允许我们直接对其进行操作或调用其方法，除非我们先进行类型检查。这是为了提高代码的类型安全性。

我们可以使用类型断言、类型保护或条件语句等方式来处理未知类型。

## TypeScript 的 void 类型是什么，什么时候使用？

TypeScript 的 void 类型用于指示函数不返回值。void 类型对于定义执行某些操作但不返回值的函数很有用。

## TypeScript 的 never type 是什么，什么时候用？

TypeScript 的 never 类型用于指示永远不会到达某个值或函数。never 类型可用于指示函数抛出错误或变量没有值。
never 类型可以用于声明函数的返回值类型，表示该函数不会有任何返回值。
TypeScript 中的 never 类型表示的是值永远不会出现的一种类型。

## 链接

https://blog.csdn.net/LuckyWinty/article/details/129457555
