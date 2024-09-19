可以通过递归调用 `setTimeout` 来模拟 `setInterval`，因为 `setTimeout` 只会执行一次，而 `setInterval` 会定期执行。我们可以让 `setTimeout` 在每次执行完毕后再次调用自身来实现循环执行。以下是用 `setTimeout` 模拟 `setInterval` 的方法：

```javascript
function mySetInterval(fn, delay) {
  let timer;

  function interval() {
    // 调用回调函数
    fn();

    // 使用 setTimeout 再次调用自身，达到循环的效果
    timer = setTimeout(interval, delay);
  }

  // 第一次调用
  timer = setTimeout(interval, delay);

  // 返回一个清除定时器的函数，以便在需要时停止循环
  return {
    clear: function() {
      clearTimeout(timer);
    }
  };
}
```

### 使用示例：

```javascript
let count = 0;
const interval = mySetInterval(() => {
  console.log('Interval running:', ++count);

  // 停止定时器，当 count 达到 5 时
  if (count === 5) {
    interval.clear();
    console.log('Interval stopped');
  }
}, 1000);
```

### 实现的要点：
1. **递归调用 `setTimeout`：** 通过在回调函数中再次调用 `setTimeout`，可以模拟 `setInterval` 的循环效果。
2. **返回停止函数：** 使用 `clearTimeout` 来提供停止功能，让用户可以手动停止定时器，就像 `clearInterval` 的作用一样。
3. **延迟执行：** 每次执行完后，再等待指定的延迟时间，确保函数按时循环运行。

这种方法通过 `setTimeout` 实现了 `setInterval` 的效果，并且可以灵活控制何时停止执行。