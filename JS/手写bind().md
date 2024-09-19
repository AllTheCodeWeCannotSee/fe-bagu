`bind` 方法的作用是创建一个新函数，并绑定指定的 `this` 值和预设的参数，而不会立即执行。它返回一个新的函数，稍后可以调用。这不同于 `call` 和 `apply`，因为它不会立即调用函数。以下是如何手写实现 `bind` 的步骤：

```javascript
Function.prototype.myBind = function (context, ...args) {
  // 保存原始函数
  const self = this;

  // 返回一个新的函数
  return function (...newArgs) {
    // 合并预设参数和新的参数，并使用 apply 调用原始函数
    return self.apply(context, [...args, ...newArgs]);
  };
};
```

### 使用示例：

```javascript
function greet(greeting, name) {
  console.log(`${greeting}, ${name}. My name is ${this.name}`);
}

const person = { name: 'Alice' };

// 使用原生 bind 方法
const boundGreet = greet.bind(person, 'Hello');
boundGreet('Bob'); // 输出：Hello, Bob. My name is Alice

// 使用自定义的 myBind 方法
const myBoundGreet = greet.myBind(person, 'Hello');
myBoundGreet('Bob'); // 输出：Hello, Bob. My name is Alice
```

### 实现的要点：
1. **闭包保存上下文：** 使用 `self = this` 保存当前函数的引用，确保可以在返回的函数内部访问。
2. **参数合并：** 使用 `apply` 方法，将原本传递的 `args`（即绑定时传递的参数）和 `newArgs`（调用时传递的参数）合并后传递给原始函数。
3. **延迟执行：** 返回一个新的函数，在调用该函数时才执行绑定的函数。

这种实现模仿了 JavaScript 原生 `bind` 方法，能够延迟调用并且支持传递参数。