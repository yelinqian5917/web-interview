## 本地对象，内置对象，宿主对象
### 本地对象 ( native object )
- 由 ECMAScript 实现提供并独立于宿主环境的任何对象。
- 本地对象可以理解为 ECMA-262 定义的类（引用类型）。
- 这些引用类型在运行过程中需要通过new来创建所需的实例对象。
- 包含：Object、String、Array、Date、Number、RegExp、Function、Boolean、Error等。

### 内置对象 ( built-in object )
- 由 ECMAScript 实现提供并独立于宿主环境的，在程序开始执行就出现的对象。
- 本身就是实例化对象，开发者无需再去实例化。
- 所有内置对象都是本地对象的子集。
- 包含：Global和Math。
- ECMAScript5中增添了JSON这个存在于全局的内置对象。

### 宿主对象 ( host object )
- 由 ECMAScript 实现的宿主环境（如某浏览器）提供的对象（如由浏览器提供的 Window 和 Document），包含两大类，一个是宿主提供，一个是自定义类对象。
- 所有非本地对象都属于宿主对象。
- 对于嵌入到网页中的JS来说，其宿主对象就是浏览器提供的对象，浏览器对象有很多，如Window和Document等。
- 包含：DOM 、BOM和自定义对象。

JavaScript 三大对象关系：

> 宿主对象（DOM、BOM、自定义）

> 内置对象:
  > 本地对象（Array、String、Date等需new出来的）
  > 标准内置对象（Global、Math、JSON）
