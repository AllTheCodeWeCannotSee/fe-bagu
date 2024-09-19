
1. **状态改变**：它们会根据传入的值或原因，将 Promise 的状态从 pending 改为 fulfilled 或 rejected。

2. **回调执行**：它们会触发相应的回调函数（then()、catch()），但这些回调函数会在下一次事件循环中执行，确保异步行为的一致性。

3. **传递参数**：resolve 传递成功的值，reject 传递错误的原因。

4. **状态不可逆**：Promise 状态一旦改变，后续的 resolve 或 reject 调用将不会产生任何效果。