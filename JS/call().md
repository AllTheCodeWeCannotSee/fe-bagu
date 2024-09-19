`call()` 是 JavaScript 中 `Function.prototype` 提供的一个方法，用于**调用一个函数**，并显式地指定调用该函数时 `this` 的指向。`call()` 可以接受多个参数，第一个参数用于绑定 `this`，后续参数是传给目标函数的实参。

### 语法

```javascript
func.call(thisArg, arg1, arg2, ...)
```

- **func**: 要调用的目标函数。
- **thisArg**: 在调用函数时，`this` 将指向的对象。如果传入 `null` 或 `undefined`，则默认指向全局对象（在浏览器中是 `window`）。
- **arg1, arg2, ...**: 调用目标函数时传递的参数。

### 示例

1. **改变函数的 `this` 指向**：

   ```javascript
   function greet() {
     console.log(`Hello, my name is ${this.name}`);
   }

   const person = { name: 'Alice' };
   greet.call(person);  // 输出: Hello, my name is Alice
   ```

   在这个例子中，`greet` 函数本身没有定义 `this` 的上下文，通过 `call()`，我们显式将 `this` 绑定到了对象 `person`，从而可以访问 `person.name`。

2. **传递参数给目标函数**：

   ```javascript
   function add(a, b) {
     return a + b;
   }

   console.log(add.call(null, 2, 3));  // 输出: 5
   ```

   在这个例子中，`add` 函数需要两个参数。通过 `call()`，我们可以传递参数 `2` 和 `3`，并让函数执行。


