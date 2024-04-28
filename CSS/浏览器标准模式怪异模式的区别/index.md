# 标准模式 怪异模式
## 定义
在“标准模式”(Standards Mode) 页面按照 HTML 与 CSS 的定义渲染，而在“怪异模式”(Quirks Mode)就是浏览器为了兼容很早之前针对旧版本浏览器设计、并未严格遵循 W3C 标准的网页而产生的一种页面渲染模式。
## 如何实现标准模式怪异模式
浏览器基于页面中文件类型描述的存在以决定采用哪种渲染模式；如果存在一个完整的`DOCTYPE`则浏览器将会采用标准模式，而如果它缺失则浏览器将会采用怪异模式。
## 区别
### 1. 盒子模型
在怪异模式下，盒模型为IE盒模型而非标准模式下的W3C
#### 1.1标准盒子模型
标准盒模型又称W3C标准盒模型，标准盒模型的 width 或 height 决定 content 的宽或高。

计算盒子宽：width(content) + padding + border

计算盒子高：heigth(content) + padding + border

样式设置：box-sizing: content-box;

#### 1.2怪异盒子模型
怪异盒模型又称IE盒子模型，怪异盒子模型的 width 或 height 等于 content + padding + border 的宽或高。

计算盒子宽：width(content + padding + border)

计算盒子高：heigth(content + padding + border)

样式设置：box-sizing: border-box;
### 2. 图片元素的垂直对齐方式:
### 3. `<table>`元素中的字体:
### 4. 内联元素的尺寸:
### 5. 元素的百分比高度:
