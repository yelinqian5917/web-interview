# var,let,const异同
## 1.变量提升
 如果我们在使用var声明一个变量之前进行了调用，输出的内容会是undefined，虽然值是undefined，但是是可以访问得到的。
## 2.块级作用域
## 3.重复声明变量
  在同一个作用域中，使用var定义变量，允许重复声明；
  let、const不允许重复声明变量
  > const 声明的同时必须赋值，并且基础类型不能改变
  在let、const定义的标识符真正执行到声明的代码前是不能被访问的，从块作用域的顶部一直到变量声明完成之前，这个变量处在 __暂时性死区__

## 4.重新赋值
  var let  都可以进行重新赋值，但是const不行
  
## 5.let/const不会在window对象添加属性