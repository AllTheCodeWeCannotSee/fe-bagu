`bind()` 是 JavaScript 中 `Function.prototype` 提供的一个方法，允许你创建一个新的函数，并**永久性地绑定**函数中的 `this` 指向到指定的对象。与 `call()` 和 `apply()` 不同，`bind()` 不会立即执行函数，而是返回一个新的函数，便于稍后调用。

### 语法

```javascript
const boundFunc = func.bind(thisArg, arg1, arg2, ...)
```

- **func**: 要绑定的目标函数。
- **thisArg**: 绑定的 `this` 指向对象。
- **arg1, arg2, ...**: 可选的预设参数，这些参数会在调用新函数时作为初始参数传递。

### 示例

1. **绑定 `this` 指向**：

   ```javascript
   const person = {
     name: 'Alice',
     greet() {
       console.log(`Hello, my name is ${this.name}`);
     }
   };

   const greetPerson = person.greet.bind(person);
   greetPerson(); // 输出: Hello, my name is Alice
   ```

   在这个例子中，我们将 `person.greet` 方法的 `this` 绑定到 `person` 对象，生成了一个新函数 `greetPerson`，即使它脱离了原来的上下文，`this` 仍然指向 `person`。
