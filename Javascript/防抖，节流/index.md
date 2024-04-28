# 防抖 节流
## 1.防抖

### 1.1 为什么有防抖
有的操作是高频触发的，但是其实触发一次就好了，比如我们短时间内多次缩放页面，那么我们不应该每次缩放都去执行操作，应该只做一次就好。再比如说监听输入框的输入，不应该每次都去触发监听，应该是用户完成一段输入后在进行触发。

- **防抖就是防止抖动，避免事件的重复触发**

### 1.2 如何实现防抖

**设计思路：** 事件触发后开启一个定时器，如果事件在这个定时器限定的时间内再次触发，则清除定时器，在写一个定时器，定时时间到则触发。

- 频繁点击 只执行最后一次操作

```js
function debounce(fn, delay){
	let timer = null;
	return function(){
		clearTimeout(timer);
		timer = setTimeout(()=> {
			fn.apply(this, arguments);
		}, delay)
	}
}
```

## 2.节流
### 2.1 为什么有节流
请求点击不应该一直点击，应该是第一次请求，等到请求回来才能够再请求第二次。

**设计思路：** 初始timer开始执行的时候，启动定时器，给到timer再次点击定时器没有执行完，则直接不执行。实现一段时间内只执行一次

- 频繁点击，一段时间内只执行第一次操作

```js
function throttle(fn, delay) {
    let timer = null
    return () => {
      if (timer) { return }
      timer = setTimeout(() => {
        fn.apply(this, arguments)
        timer = null
      }, delay);
    }
  }
```
## 防抖节流区别
防抖执行最后一次操作，节流执行第一次操作



