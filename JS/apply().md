`apply()` 是 JavaScript 中 `Function.prototype` 提供的方法，用来**调用一个函数**，并且可以显式地指定 `this` 的指向，同时将参数作为数组传入。这与 `call()` 方法类似，区别在于 `apply()` 接收的是参数数组，而 `call()` 接收的是一个个独立的参数。

### 语法

```javascript
func.apply(thisArg, [argsArray])
```

- **func**: 目标函数。
- **thisArg**: 需要绑定的 `this` 对象。如果为 `null` 或 `undefined`，`this` 将指向全局对象（在浏览器中是 `window`）。
- **argsArray**: 一个数组或类数组对象，作为调用函数时的参数。

### 示例

1. **调用函数并指定 `this`**：

   使用 `apply()` 调用函数并指定 `this` 的指向。

   ```javascript
   function greet(greeting, punctuation) {
     console.log(greeting + ', my name is ' + this.name + punctuation);
   }

   const person = { name: 'Alice' };
   greet.apply(person, ['Hello', '!']);  // 输出: Hello, my name is Alice!
   ```

   在这个例子中，`greet` 函数通过 `apply()` 被调用，`this` 指向了 `person` 对象，参数通过数组 `['Hello', '!']` 传递。





