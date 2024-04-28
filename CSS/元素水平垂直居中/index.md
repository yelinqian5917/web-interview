# 居中篇

## 实现方式

1. 利用定位+margin:auto
2. 利用定位+margin:负值
3. 利用定位+transform
4. table布局
5. flex布局
6. grid布局

## 1. 利用定位+margin:auto
子元素设置为 absolute ,加上margin:auto

## 2.利用定位+margin:负值

```css
.son {
  position: absolute;
  top: 50%;
  left: 50%;
  margin-left: -50px;
  margin-top: -50px;
  width: 100px;
  height: 100px;
  background: red;
}
```

- 此方式需要知道子元素宽高才能设置边距负自身的一半
- margin设置百分比的话是相对于父元素，不想对于自身偏移，所以只能设置像素。
- 需要知道子元素具体宽高

## 3.利用定位+transform

```css
.son {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate( -50%, -50%);
  width: 100px;
  height: 100px;
  background: red;
}
```

transform 能够实现自身偏移而且能够使用百分比，替代了具体值

## 4. table布局
设置父元素为display:table-cell，子元素设置 display: inline-block。利用vertical和text-align可以让所有的行内块级元素水平垂直居中

```html
<style>
    .father {
        display: table-cell;
        width: 200px;
        height: 200px;
        background: skyblue;
        vertical-align: middle;
        text-align: center;
    }
    .son {
        display: inline-block;
        width: 100px;
        height: 100px;
        background: red;
    }
</style>
<div class="father">
    <div class="son"></div>
</div>
```

限制也是有的只能让行内块元素居中

## 5. flex布局
```css
.father {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 200px;
        height: 200px;
        background: skyblue;
    }
    .son {
        width: 100px;
        height: 100px;
        background: red;
    }
```

flex 比较简单直接让主轴跟交叉轴居中对齐即可

## 6. grid布局

```html
<style>
    .father {
            display: grid;
            align-items:center;
            justify-content: center;
            /* place-content: center;  简写 */
            width: 200px;
            height: 200px;
            background: skyblue;

        }
        .son {
            width: 10px;
            height: 10px;
            border: 1px solid red
        }
</style>
<div class="father">
  <div class="son"></div>
</div>
```



## 链接

margin: auto;居中：
那么还有一个问题，既然居中是有margin：auto来计算实现。为什么还需要将元素设为绝对定位呢？
这是因为margin：auto 默认只会计算左右边距。而上下如果设置为auto时默认是取0.也就是说，margin：auto和margin：0 auto 在一般情况下没有区别，不能实现垂直居中。
但是有了绝对定位后，margin-top和margin-bottom 的值就不是0了，也是通过计算所得。所以能实现垂直居中。
https://blog.csdn.net/wu_xianqiang/article/details/105840799

## vertical-align 属性 line-height

设置文字布局的属性

https://zhuanlan.zhihu.com/p/352965852