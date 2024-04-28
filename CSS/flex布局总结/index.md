# flex布局
## 一.基本概念
Flex布局又称弹性布局，它使用flexbox使得容器有了弹性，更加适应各种设备的不同宽度，而不必依赖于传统的块状布局和浮动定位。


- 弹性容器
- 弹性项
- 主轴
- 交叉轴
- 对齐方式

## 二.容器的属性
### 2.1 flex-diretion属性
flex-direction属性决定主轴的方向（即项目的排列方向）。

```css
.box {
  flex-direction: row | row-reverse | column | column-reverse;
}
```

flex-direction属性有4个值:
row（默认值）：主轴为水平方向，起点在左端（项目从左往右排列）。
row-reverse：主轴为水平方向，起点在右端（项目从右往左排列）。
column：主轴为垂直方向，起点在上沿（项目从上往下排列）。
column-reverse：主轴为垂直方向，起点在下沿（项目从下往上排列）。

### 2.2 flex-wrap属性
默认情况下，项目都排在一条线（又称”轴线”）上。flex-wrap属性定义，如果一条轴线排不下，如何换行。

```css
.box {
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```

flex-wrap属性有3个值
nowrap（默认）：不换行（列）。
wrap：主轴为横向时：从上到下换行。主轴为纵向时：从左到右换列。
wrap-reverse：主轴为横向时：从下到上换行。主轴为纵向时：从右到左换列。


### 2.3 flex-flow属性
flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。

```css
.box {
  flex-flow: <flex-direction> <flex-wrap>;
}
```

### 2.4 justify-content属性
justify-content属性定义了项目在主轴上的对齐方式。

```css
.box {
  justify-content: flex-start | flex-end | center | space-between | space-around;
}
```

justify-content属性有5个值

flex-start（默认）：与主轴的起点对齐。
flex-end：与主轴的终点对齐。
center：与主轴的中点对齐。
space-between：两端对齐主轴的起点与终点，项目之间的间隔都相等。
space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。


### 2.5 align-items属性
align-items属性定义项目在交叉轴上如何对齐。纵向交叉轴始终自上而下，横向交叉轴始终自左而右。

```css
.box {
  align-items: flex-start | flex-end | center | baseline | stretch;
}
```

align-items属性有5个值:
flex-start：交叉轴的起点对齐。
flex-end：交叉轴的终点对齐。
center：交叉轴的中点对齐。
baseline: 项目的第一行文字的基线对齐。
stretch（默认值）：如果项目未设置高度或设为auto，项目将占满整个容器的高度。


### 2.6 align-content属性
align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。

```css
.box {
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}
```

align-content属性有6个值:
flex-start：与交叉轴的起点对齐。
flex-end：与交叉轴的终点对齐。
center：与交叉轴的中点对齐。
space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
stretch（默认值）：主轴线占满整个交叉轴。

### 2.7 gap属性
gap 属性定义 flexbox、网格或多列布局中行与列之间的间隙大小。它是以下属性的简写属性：

```css
.box {
 gap: row-gap column-gap|initial|inherit;
}
```

row-gap 行间隙
column-gap 列间隙

## 三.项目的属性
### 3.1 order
order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。
```css
.item {
  order: <integer>;
}
```

### 3.2 flex-grow属性
flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。


### 3.3 flex-shrink属性
flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。负值对该属性无效。如果flex-shrink值为0，表示该项目不收缩。

> 当子元素宽度和大于父元素宽度时，flex-shrink 将会按照一定的比例进行收缩，即将子元素宽度之和与父元素宽度的差值按照子元素flex-shrink值来分配给各个子元素，
> 指定各个子元素收缩多少，每个子元素原本宽度减去按比例分配的值，其剩余值为收缩完的实际宽度。

### 3.4 flex-basis属性
flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。


### 3.5 flex属性
flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。
该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。
建议优先使用这个属性，而不是单独写三个分离的属性，因为浏览器会推算相关值。
```css
.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}
```

### 3.6 align-self属性
align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。

```css
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```

## 四.链接
https://blog.csdn.net/wwwjjjjj666/article/details/128033184