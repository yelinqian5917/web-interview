# MVVM和MVC的区别？
 
## 一 MVVM即Model-View-ViewModel的简写。
 
即模型-视图-视图模型。
模型（Model）指的是后端传递的数据。
视图(View)指的是所看到的页面。
视图模型(ViewModel)是mvvm模式的核心，它是连接view和model的桥梁。
它有两个方向：
一是将模型（Model）转化成视图(View)，即将后端传递的数据转化成所看到的页面。实现的方式是：数据绑定。
二是将视图(View)转化成模型(Model)，即将所看到的页面转化成后端的数据。实现的方式是：DOM 事件监听。
这两个方向都实现的，我们称之为数据的双向绑定。

## 二 MVC是Model-View- Controller的简写。即模型-视图-控制器。

MVC是单向通信。也就是View跟Model，必须通过Controller来承上启下。

# MVVM框架与MVC框架的区别

mvc 和 mvvm 其实区别并不大。都是一种设计思想，主要区别如下：
1.mvc 中 Controller演变成 mvvm 中的 viewModel
2.mvvm 通过数据来驱动视图层的显示而不是节点操作。
3.mvc中Model和View是可以直接打交道的，造成Model层和View层之间的耦合度高。而mvvm中Model和View不直接交互，而是通过中间桥梁ViewModel来同步
4.mvvm主要解决了:mvc中大量的DOM 操作使页面渲染性能降低，加载速度变慢，影响用户体验