# 组件间过渡动画

## 什么是过渡动画

在日常开发中，页面切换时的转场动画是比较基础的一个场景

当一个组件在显示与消失过程中存在过渡动画，可以很好的增加用户的体验

在 react 中实现过渡动画效果会有很多种选择，如 react-transition-group，react-motion，Animated，以及原生的 CSS 都能完成切换动画

## 如何实现

在 react 中，react-transition-group 是一种很好的解决方案，其为元素添加 enter，enter-active，exit，exit-active 这一系列勾子

可以帮助我们方便的实现组件的入场和离场动画

其主要提供了三个主要的组件：

- CSSTransition：在前端开发中，结合 CSS 来完成过渡动画效果
- SwitchTransition：两个组件显示和隐藏切换时，使用该组件
- TransitionGroup：将多个动画组件包裹在其中，一般用于列表中元素的动画
