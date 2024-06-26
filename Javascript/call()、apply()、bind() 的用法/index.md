# call apply bind
  > 都是动态的修改当前函数内部环境对象this的指向。
  > **不会修改箭头函数的this指向**
## 1.call
```js
func.call(Obj,'','')
 // Obj将代替func函数里面的this指向，传参使用逗号分隔
```

## 2.apply

```js
fn.apply(obj, [3, 4]); //obj
// Obj将代替func函数里面的this指向，传参使用数组传递，所以是平常常见的传参方式
```
## 3.bind
```js
let newfn = fn.bind(obj); //obj
newfn(5, 6);
//会修改方法 的this指向并且返回新的函数，需要调用才会执行
```
## 4.三者区别的总结
- 执行方式不同
>  call和apply是改变后页面加载之后就立即执行，是同步代码。
>  bind是异步代码，改变后不会立即执行；而是返回一个新的函数。

- 传参方法不同
> call和bind传参是一个一个逐一传入，不能使用剩余参数的方式传参。
> apply可以使用数组的方式传入的，只要是数组方式就可以使用剩余参数的方式传入。

- 修改this的性质不同
> call、apply只是临时的修改一次，也就是call和apply方法的那一次；当再次调用原函数的时候，它的指向还是原来的指向。
> bind是永久修改函数this指向，但是它修改的不是原来的函数；而是返回一个修改过后新的函数，此函数的this永远被改变了，绑定了就修改不了。

## 手写实现三函数？