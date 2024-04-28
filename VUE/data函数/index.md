# data函数

## 概念

```js
var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: true
  }
})
```

***基本渲染语法***

```js
export default{
  data(){
    return {}
  }
}
```

## 为什么data是函数不是对象？

```js
var Component = function () {};
Component.prototype.data = {
            message: '10'
}
var component1 = new Component(), component2 = new Component(); 
component1.data.message = '20'; 
console.log(component2.data.message);
```