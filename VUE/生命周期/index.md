# vue的生命周期

## 一 vue生命周期
每个vue实例都有一个生命周期 一共分为八个阶段
创建前后： beforeCreate/created 渲染前后： beforeMount/mounted
更新前后： beforeUpdate/updated 销毁前后： beforeDestroy/destroyed

在created周期的时候 就可以访问到this了 也可以调用异步的方法去获取后台的数据
在mounted周期的时候 就能够访问到DOM结构 对dom结构进行一些增删改查的操作 因为在这个时候 dom结构已经渲染完成并挂载在vue实例上面了
当data变化时，会触发beforeUpdate和updated方法
在执行destroy方法后，对data的改变不会再触发周期函数，说明此时vue实例已经解除了事件监听以及和dom的绑定，**但是dom结构依然存在**。

## 二 父子组件的生命周期顺序
加载渲染过程：
父beforeCreate->父created->父beforeMount->子beforeCreate->子created->子beforeMount->子mounted->父mounted
子组件更新过程：父beforeUpdate->子beforeUpdate->子updated->父updated
父组件更新过程：父beforeUpdate->父updated
销毁过程：父beforeDestroy->子beforeDestroy->子destroyed->父destroyed

> before 除了create 其他周期父组件都在子组件前面执行 ， ed则相反 除了create其他之外 子组件都在父组件之前执行完

> 除了创建过程父节点是独立完成的，其余的载入 跟新 销毁，都是父节点先开始执行，子节点执行完父节点才执行完。