# 基础类型声明

## 一 布尔值

最基本的数据类型就是简单的 true/false 值，在 JavaScript 和 TypeScript 里叫做 boolean（其它语言中也一样）。

```ts
let isDone: boolean = false;
```

## 二 数字

和 JavaScript 一样，TypeScript 里的所有数字都是浮点数。

```ts
let decLiteral: number = 6;
let hexLiteral: number = 0xf00d;
let binaryLiteral: number = 0b1010;
let octalLiteral: number = 0o744;
```

## 三 字符串

```ts
let name: string = "bob";
```

## 四 数组

定义数组有俩种方式:

**常规定义**

```ts
let list: number[] = [1, 2, 3];
```

**数组泛型**

```ts
let list: Array<number> = [1, 2, 3];
```

## 五 元组 Tuple

元组类型允许表示一个已知元素数量和类型的数组，各元素的类型不必相同。**用得少**

```ts
let x: [string, number];
```

# 链接

https://www.tslang.cn/docs/handbook/basic-types.html
