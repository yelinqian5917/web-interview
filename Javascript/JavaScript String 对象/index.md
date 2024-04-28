# String对象

## 一 属性

1. length
2. prototype
3. constructor

## 二 方法

### 1. 查找
charAt()	返回在指定位置的字符。
charCodeAt()	返回在指定的位置的字符的 Unicode 编码。

match()	查找找到一个或多个正则表达式的匹配。
search()	查找与正则表达式相匹配的值。

indexOf()	返回某个指定的字符串值在字符串中首次出现的位置。

### 2.替换

replace()	在字符串中查找匹配的子串， 并替换与正则表达式匹配的子串。

### 3.分割
split()	把字符串分割为字符串数组。

### 4.提取
slice()	提取字符串的片断，并在新的字符串中返回被提取的部分。
substr()	从起始索引号提取字符串中指定数目的字符。
substring()	提取字符串中两个指定的索引号之间的字符。


---
concat()	连接两个或更多字符串，并返回新的字符串。
fromCharCode()	将 Unicode 编码转为字符。

includes()	查找字符串中是否包含指定的子字符串。
lastIndexOf()	从后向前搜索字符串，并从起始位置（0）开始计算返回字符串最后出现的位置。

repeat()	复制字符串指定次数，并将它们连接在一起返回。



startsWith()	查看字符串是否以指定的子字符串开头。

toLowerCase()	把字符串转换为小写。
toUpperCase()	把字符串转换为大写。
trim()	去除字符串两边的空白
toLocaleLowerCase()	根据本地主机的语言环境把字符串转换为小写。
toLocaleUpperCase()	根据本地主机的语言环境把字符串转换为大写。
valueOf()	返回某个字符串对象的原始值。
toString()	返回一个字符串。