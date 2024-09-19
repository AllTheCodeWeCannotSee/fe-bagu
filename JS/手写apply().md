

```javascript
Function.prototype.myApply = function (context, args) {
  // 如果没有传入 context 或 context 为 null 或 undefined，默认指向全局对象（浏览器中为 window）
  context = context || globalThis;

  // 创建一个独特的属性名，防止覆盖 context 上已有的属性
  const fnSymbol = Symbol();

  // 将当前函数（即 this）作为 context 对象的一个属性
  context[fnSymbol] = this;

  // 判断 args 是否为数组类型，如果不是则赋值为空数组
  args = args || [];

  // 使用 context 调用该函数并展开参数
  const result = context[fnSymbol](...args);

  // 删除临时添加的属性
  delete context[fnSymbol];

  // 返回函数执行的结果
  return result;
};
```

### 使用示例：

```javascript
function greet(greeting, name) {
  console.log(`${greeting}, ${name}. My name is ${this.name}`);
}

const person = { name: 'Alice' };

// 使用原生 apply 方法
greet.apply(person, ['Hello', 'Bob']); // 输出：Hello, Bob. My name is Alice

// 使用自定义的 myApply 方法
greet.myApply(person, ['Hello', 'Bob']); // 输出：Hello, Bob. My name is Alice
```

### 实现的要点：
1. `context = context || globalThis;` 用于确保 `context` 为 `null` 或 `undefined` 时默认指向全局对象。
2. 使用 `Symbol` 创建一个唯一的键，防止覆盖 `context` 上已有的属性。
3. `args = args || [];` 确保传入的参数是一个数组类型，如果不是，使用空数组。
4. 展开数组参数传递给函数，最后返回函数执行的结果。

这种实现模仿了 JavaScript 原生 `apply` 方法的行为，确保可以传递数组形式的参数并改变 `this` 的指向。