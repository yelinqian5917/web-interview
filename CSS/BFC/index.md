# BFC块级格式上下文

## 一.什么是BFC
直译为 块级格式化上下文 ，把BFC理解成一块独立的渲染区域,容器内的元素不会影响容器外的元素.

## 二.BFC能够解决哪些问题

### 1.避免外边距重叠（防止margin塌陷）
俩个盒子上下叠加，会出现外边距重叠的情况，
通过给其中一个div包裹一个父div，设置BFC属性，来解决margin塌陷的问题

### 2.用于清除浮动
子元素设置为浮动了之后，父元素会出现高度为零的情况
通过给父元素设置BFC属性，来实现清除浮动

### 3.阻止元素被浮动元素覆盖
当前一个兄弟元素设置了浮动属性时，后一个兄弟元素会跑到前一个兄弟元素的位置去，从而后一个兄弟元素被覆盖
通过给被影响的兄弟元素设置BFC属性，来解决被覆盖的情况。


## 三.如何创建BFC
1. 浮动元素 ，float除了none外
2. 定位元素 position的值不是static或者relative
3. display 为inline-block,table-cell,table,line-table,flex,grid
4. overflow 除了 visible 以外的值（hidden，auto，scroll）
- 根元素html 就是一个 BFC


看下display的一些属性？
display:table
元素会作为块级表格来显示，类似 table，表格前后带有换行符;配合table-cell使用可实现水平垂直居中，具体可见：水平垂直居中