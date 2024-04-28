## 1.vue的双向绑定原理
Vue.js是采用数据劫持结合发布者-订阅者模式的方式，通过Object.defineProperty()来劫持各个属性的setter，getter，在数据变动时发布消息给订阅者，触发相应的监听回调。
### 1.1数据劫持
Object.defineProperty()：主要作用就是直接在一个对象上面定义一个新属性，或者修改一个已经存在的属性。
```js
Object.defineProperty(obj,prop,desc)
```
> **obj**:需要定义属性的当前对象
> **prop**需要定义的属性名
> **desc**属性描述符

- 通过描述符的设置可以更加精准的控制对象属性
#### 1.1.1属性描述符
属性描述符有俩种形式，并且不可以混合使用，数据描述符，存取描述符。
1. 数据描述符

|    属性名    |  默认值   |                     功能                      |
| :----------: | :-------: | :-------------------------------------------: |
|    value     | undefined |                    具体值                     |
|     get      | undefined |                                               |
|     set      | undefined |                                               |
|   writable   |   false   |                 是否可以改变                  |
|  enumerable  |   false   | 是否会出现在for in 或者 Object.keys()的遍历中 |
| configurable |   false   |        描述属性是否配置，以及可否删除         |

2. 存取描述符
存取描述 符是一堆getter setter函数组成的
```js
var person = {
    a:1
}
Object.defineProperty(person,'a',{
    get(){
        return 3 //当访问这个属性的时候返回3
    },
    set(val){
        console.log(val)//当设置这个属性的时候执行,val是设置的值
    }
})

person.a// 3,我们明明写的是a:1,怎么返回的3呢?这就是get()的威力了
person.a = 5// 5,相应的设置的时候执行了set()函数
```

### 1.2 发布订阅模式
发布-订阅模式其实是一种对象间一对多的依赖关系，当一个对象的状态发送改变时，所有依赖于它的对象都将得到状态改变的通知。
多个订阅者同时监听某一个发布者，发布者发生变化通知所有订阅者

observe类进行初始化发布者
Dep收集所有的订阅者watcher
observe发布通知所有的dep里面的订阅者实现改变

# 设计模式

Vue设计模式主要包括以下几种：

单例模式: 确保整个程序中只有一个实例，如Vuex和Vue-Router插件的注册方法。

工厂模式: 通过传入参数来创建实例，如虚拟DOM的创建。

发布-订阅模式: 订阅者向调度中心注册感兴趣的事件，当事件触发时，调度中心会通知所有订阅者。

观察者模式: watcher和依赖对象的关系，用于响应式数据。
