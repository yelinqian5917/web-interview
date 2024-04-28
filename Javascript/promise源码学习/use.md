# Promise 原理浅析

**对象状态（State）：** Promise 有三种状态：Pending（进行中）、Fulfilled（已成功）和 Rejected（已失败）。初始状态是 Pending，异步操作完成时，Promise 可以由 Pending 转为 Fulfilled，表示操作成功；或者由 Pending 转为 Rejected，表示操作失败。状态一旦转变，就不可再改变。

**then 方法：** Promise 对象上有一个 then 方法，用于指定异步操作成功或失败后要执行的回调函数。then 方法接收两个参数，第一个参数是处理成功情况的回调函数（onFulfilled），第二个参数是处理失败情况的回调函数（onRejected）。

**回调队列：** 当 Promise 处于 Pending 状态时，then 方法注册的回调函数不会立即执行。相反，它们会被添加到一个回调队列中，等待 Promise 的状态改变。

**状态转移和回调触发：** 当 Promise 状态由 Pending 转为 Fulfilled 或 Rejected 时，将会按照注册的回调函数的顺序执行对应的处理函数。如果是 Fulfilled，执行 onFulfilled 回调；如果是 Rejected，执行 onRejected 回调。这些回调函数可以访问到 Promise 返回的值或错误信息。

**错误处理：** 如果在回调函数执行过程中发生异常（异常被捕获），Promise 将转为 Rejected 状态，后续的错误处理回调（then 的第二个参数或后续 catch 方法）将会被触发。

**链式调用：** then 方法返回的仍然是一个 Promise 对象，因此可以进行链式调用。这样可以更方便地处理多个异步操作的依赖关系。
