# DOM节点操作

## 1. 获取元素节点
document.getElementById(id)：返回具有指定ID属性的元素。
document.getElementsByTagName(tagname)：返回具有指定标签名称的元素的集合。例如，getElementsByTagName("div")将返回所有div元素。
document.getElementsByClassName(classname)：返回具有指定类名的所有元素的集合。
document.querySelector(selector)：返回与指定CSS选择器匹配的第一个元素。
document.querySelectorAll(selector)：返回与指定CSS选择器匹配的所有元素的集合

## 2. 创建元素节点
可以使用createElement(tagname)方法创建新元素节点。例如，要创建一个新的
元素，请使用document.createElement("div")。
document.createTextNode(textNode)方法：创建一个文本节点textNode
document.createDocumentFragment()方法：创建文档碎片节点

## 3.添加和删除元素
可以使用父节点元素的appendChild(child)方法将元素添加到文档中。例如，要添加一个新的元素，请使用document.body.appendChild(newDiv)。

insertBefore()方法：在开头插入新节点JavaScript insertBefore() 方法可向当前节点的子节点列表的开头添加新的子节点。用法如下：insertBefore(newChild,refChild) 其中参数 newchild 表示新插入的节点，refchild 表示插入新节点的节点，用于指定插入节点的后面相邻位置。插入成功后，该方法将返回新插入的子节点。
删除元素时，可以使用父节点元素的removeChild(child)方法。例如，要从文档中删除一个元素，请使用document.body.removeChild(divToRemove)。

## 4.修改元素属性
可以使用元素节点的setAttribute(attributeName, attributeValue)方法设置属性值。例如，要将一个元素的class属性设置为“myclass”，请使用element.setAttribute("class", "myclass")。
可以使用getAttribute(attributeName)方法获取元素属性的值。例如，要获取元素的class属性值，请使用element.getAttribute("class")。
可以使用removeAttribute(attributeName)方法删除元素属性。例如，要从元素中删除class属性，请使用element.removeAttribute("class")。

## 5. 修改元素内容
可以使用元素节点的innerHTML属性设置元素内容。innerHTML属性包含HTML标记和文本内容。例如，要将一个元素的内容设置为“Hello World”，请使用element.innerHTML = "Hello World"。
可以使用元素节点的innerText或textContent属性设置纯文本内容。例如，要将一个元素的内容设置为“Hello World”，请使用element.innerText = "Hello World" 或 element.textContent = "Hello World"。

## 6. 节点遍历
可以使用parentNode属性访问元素的父节点。例如，要获取一个元素的父节点，请使用element.parentNode。
可以使用childNodes属性访问元素的子节点。例如，要获取一个元素的子节点，请使用element.childNodes。
可以使用nextSibling和previousSibling属性访问兄弟节点。例如，要获取下一个兄弟节点，请使用element.nextSibling。

## 7. 事件处理
可以使用元素节点的addEventListener(event, function)方法将事件处理函数添加到元素。例如，要在单击元素时执行一个函数，请使用element.addEventListener("click", myFunction)。
可以使用removeEventListener(event, function)方法从元素中删除事件处理函数。例如，要从元素中删除单击事件处理函数，请使用element.removeEventListener("click", myFunction)。
