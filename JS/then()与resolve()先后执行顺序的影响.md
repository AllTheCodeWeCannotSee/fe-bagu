
我们可以通过多个顺序图来展示 `Commitment` 类的不同执行场景，包括 `then()` 在 `resolve()` 之前或之后调用的情况。为了说明这些情况，我会给出一个简单的例子，并逐一画出不同的执行顺序。

### 简单的代码示例
```javascript
const commitment = new Commitment((resolve, reject) => {
  setTimeout(() => {
    resolve("Success");
  }, 1000);
});

commitment.then((result) => {
  console.log(result);
});
```

### 情况1：`then()` 在 `resolve()` 之前调用

在这个场景中，`then()` 在 `resolve()` 之前被调用，因此回调函数被注册到 `resolveCallbacks` 队列中，等待 `resolve` 被调用后执行。
![[Untitled diagram-2024-09-19-021247.png]]

#### 解释：
- 用户在 `new Commitment()` 后，立即调用 `then()`，因为 `resolve` 还没有被调用，`then()` 中的回调被注册到 `resolveCallbacks` 队列中。
- 一秒后，`resolve("Success")` 被调用，将状态设为 `"RESOLVED"`，并异步执行之前注册的回调。

### 情况2：`then()` 在 `resolve()` 之后调用

在这个场景中，`resolve()` 在 `then()` 之前被调用。因为 `resolve` 改变了状态为 `"RESOLVED"`，当 `then()` 被调用时，它会立即触发并异步执行回调，而不是将回调推入队列。

![[Untitled diagram-2024-09-19-021351.png]]

#### 解释：
- 一秒后 `resolve` 被调用，将状态改为 `"RESOLVED"`，此时没有注册的回调。
- 当 `then()` 在 `resolve` 之后调用时，`then()` 发现状态已经是 `"RESOLVED"`，因此直接将回调加入微任务队列中进行异步执行。
