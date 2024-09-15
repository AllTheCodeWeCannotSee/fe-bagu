
- **语法**：`func.call(thisArg, arg1, arg2, ...)`
  - `thisArg` 是函数执行时 `this` 的值。
  - `arg1, arg2, ...` 是传给函数的其他参数。
- **作用**：`call()` 方法允许你显式地设置 `this` 的值，而不必像构造函数那样依赖 `new`。

###  **解释 `Mother.call(son, "Da")`**

- `Mother` 是一个构造函数（或者普通的函数），当你使用 `Mother.call(son, "Da")` 时，你是在调用 `Mother` 函数，并将 `son` 对象作为 `this` 来使用。
- 这意味着在 `Mother` 函数中，`this` 不再是一个新创建的对象，而是已经存在的 `son` 对象。

#### 具体过程：

```javascript
function Mother(lastName) {
  this.lastName = lastName; // 这里的 this 是 son
}

const son = {}; // 这是一个已经存在的空对象

Mother.call(son, "Da"); // 调用 Mother 函数，并将 this 绑定到 son 对象上
console.log(son.lastName); // 输出 'Da'
```

1. **`son = {}`**：这是一个空对象。
2. **`Mother.call(son, "Da")`**：调用 `Mother` 函数，将 `this` 绑定到 `son` 对象，并传入参数 `"Da"`。因此在 `Mother` 函数内部，`this.lastName = lastName` 会将 `"Da"` 赋值给 `son.lastName`。
3. **输出**：`son.lastName` 的值是 `"Da"`，因为 `call()` 方法将 `this` 绑定到现有对象 `son` 上。
