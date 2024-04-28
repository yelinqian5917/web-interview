# 数组去重
## 1. new Set()
## 2. filter() 去重
```js
var arr = ['apple','apps','pear','apple','orange','apps'];
 
console.log(arr)    
  var newArr = arr.filter(function(item,index){
     return arr.indexOf(item) === index;  // 因为indexOf 只能查找到第一个  
  });
 
console.log(newArr); 
```

## 3. 利用for 循环 搭配 indexOf 去重
```js
 var arr = [1,9,8,8,7,2,5,3,3,3,2,3,1,4,5,444,55,22];
 function noRepeat(arr) {
		//定义一个新的临时数组 
		var newArr=[]; 
		//遍历当前数组 
		for(var i=0;i<arr.length;i++) {
		  //如果当前数组的第i已经保存进了临时数组，那么跳过，
		  //否则把当前项push到临时数组里面 
		  if(newArr.indexOf(arr[i]) === -1) {  //indexOf() 判断数组中有没有字符串值，如果没有则返回 -1 
		     newArr.push(arr[i]);
		  }
    	}
    return newArr
  }
  var arr2 = noRepeat(arr);
  console.log(arr2);  

```

## 4. splice去重

## 5. includes去重 不重复则添加到新数组中去



