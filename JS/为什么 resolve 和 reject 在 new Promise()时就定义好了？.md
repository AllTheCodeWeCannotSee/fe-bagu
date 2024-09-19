在 `Promise` 的实现中，`resolve` 和 `reject` 是在构造函数（`constructor`）里定义并作为参数传递给 `executor` 函数的，这样做是因为 `Promise` 是 **立即执行** 的，而不是等到调用 `then()` 才执行。

### 理解 `executor` 和 `resolve`、`reject` 的关系

在 JavaScript 的 `Promise` 实现中，`executor` 是传递给 `Promise` 构造函数的函数。这个 `executor` 函数会在 `new Promise()` 时立刻执行，并且 `Promise` 构造函数会将它自己生成的 `resolve` 和 `reject` 函数作为参数传递给这个 `executor`。`executor` 函数的任务就是根据异步操作的结果来调用 `resolve` 或 `reject`，从而改变 `Promise` 的状态。

让我们一步步来理解这个过程：

1. **当你创建一个 Promise 实例时：**
   ```javascript
   const promise = new Promise((resolve, reject) => {
     if (res) {
       resolve("Success");
     } else {
       reject("Failed");
     }
   });
   ```
   在这段代码中，当 `new Promise()` 被执行时，`Promise` 构造函数立即调用了你传入的 `executor` 函数。这个 `executor` 函数会立刻执行，而不是等到你调用 `.then()` 方法。

2. **`resolve` 和 `reject` 的传递：**
   - `Promise` 构造函数在创建 `Promise` 实例时，生成了两个函数：`resolve` 和 `reject`。
   - 它们分别用于将 `Promise` 从 `'pending'` 状态转变为 `'fulfilled'`（成功）或 `'rejected'`（失败）。
   - `Promise` 构造函数把这两个函数传递给你定义的 `executor` 函数作为参数。

3. **`executor` 的执行：**
   ```javascript
   const promise = new Promise((resolve, reject) => {
     if (res) {
       resolve("Success");  // 调用 resolve，Promise 状态变为 fulfilled
     } else {
       reject("Failed");    // 调用 reject，Promise 状态变为 rejected
     }
   });
   ```
   当 `executor` 被调用时，它有能力调用 `resolve` 或 `reject` 函数来改变 `Promise` 的状态。

4. **`then` 和 `catch` 的作用：**
   - `then()` 和 `catch()` 并不是触发 `resolve` 或 `reject` 的地方，它们只是定义了在 `Promise` 被解决（`resolve`）或被拒绝（`reject`）后，应该执行的回调函数。
   - 也就是说，`then` 和 `catch` 方法只是在 `Promise` 的状态已经确定后执行相应的回调。

### 为什么 `resolve` 和 `reject` 在 `new Promise()` 时就定义好了？
因为 `Promise` 的设计模式是为了处理 **异步操作** 的结果。你通常希望在异步操作完成（或者失败）时改变 `Promise` 的状态，所以在 `executor` 函数中，`resolve` 和 `reject` 函数在 `new Promise()` 时被立即定义并传入 `executor`，以便你可以在异步操作完成时调用它们。

在异步操作完成之前，`then()` 和 `catch()` 方法只是注册了要执行的回调函数。等到 `Promise` 的状态从 `'pending'` 变为 `'fulfilled'` 或 `'rejected'` 后，这些回调函数才会被执行。

### 举个简单的异步例子
```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Success after 2 seconds");
  }, 2000); // 2 秒后调用 resolve
});

promise
  .then((message) => {
    console.log(message); // 2 秒后输出 "Success after 2 seconds"
  })
  .catch((error) => {
    console.log(error);
  });
```

在这个例子中，`setTimeout` 是一个异步操作，它会在 2 秒后调用 `resolve`，这时 `Promise` 的状态才会变为 `'fulfilled'`，然后 `then` 方法的回调函数才会被执行。

### 总结：
- **`resolve` 和 `reject` 在 `new Promise()` 时定义并传入 `executor`，是为了能够在异步操作完成时及时改变 `Promise` 的状态**。
- **`then()` 和 `catch()` 注册的是在状态变更后的回调函数**，它们不会直接影响 `resolve` 和 `reject` 的调用顺序。