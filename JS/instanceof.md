- **用途**：`instanceof` 用于检测一个对象是否是某个构造函数的**实例**。
- **返回值**：`instanceof` 返回一个**布尔值**，表示一个对象是否继承自某个构造函数的 `prototype`。
- **适用对象**：`instanceof` 主要用于检测**引用类型**（如对象、数组等）的实例关系，无法检测原始类型。

#### 示例：
```javascript
console.log([] instanceof Array);     // true
console.log([] instanceof Object);    // true
console.log({} instanceof Object);    // true
console.log(function(){} instanceof Function); // true
console.log(new Date() instanceof Date);       // true
console.log(new Date() instanceof Object);     // true
```

#### 特点：
- **引用类型检测准确**：`instanceof` 可以检测数组、对象、日期等是否是某个构造函数的实例。
- **原始类型无效**：`instanceof` 对于原始类型无效，无法用于检测 `number`、`string` 等。
- **原型链检测**：`instanceof` 检测对象的原型链，查看是否继承自指定的构造函数的原型。
- **跨 `iframe` 或窗口失效**：在某些情况下，比如在多个 `iframe` 或窗口中，`instanceof` 检测可能会失败，因为不同的环境中构造函数不同。
