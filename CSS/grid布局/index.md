# Grid布局

## 一 概览
Grid布局是将容器划分成“行”和“列”，产生单元格，然后指定“项目所在”的单元格，可以看作是二维布局

## 二 容器属性

### 1  grid
指定一个容器采用网格布局

### 2  inline-grid
将容器元素设置成行内元素

### 3 grid-template-columns 和 grid-template-rows
grid-template-columns
定义每一列的宽度
grid-template-rows
定义每一行的高度

####  repeat(重复的次数，所要重复的值)
> grid-template-columns: repeat(3, 20%);

####  auto-fill关键字
当单元格的大小是固定的，容器的大小不确定，实现每一行或每一列容纳尽可能多的单元格时，使用auto-fill实现自动填充
>grid-template-columns: repeat(auto-fill, 100px);

#### fr关键字
> grid-template-columns: 1fr 2fr 150px;
表示第二列的宽度是第一列的2倍，第三列宽度是150px

#### minmax(最小值，最大值) 将长度设置在一个范围内

> grid-template-colunms: 150px 20% (100px,1fr);
表示第三列的列宽不小于100px，不大于1fr

#### auto关键字
表示由浏览器自己决定长度

### 4 row-gap 和 column-gap 和 gap
row-gap设置行与行的间隔
column-gap设置列与列的间隔
gap 是row-gap和column-gap的缩写

### 5 grid-template-areas

### 6 grid-auto-flow

### 7 justify-items属性，align-items属性，place-items属性

#### 

## 链接
https://zhuanlan.zhihu.com/p/84844677?from_voters_page=true

