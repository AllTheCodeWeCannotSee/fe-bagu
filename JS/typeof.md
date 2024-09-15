- **用途**：`typeof` 用于检测变量的**原始类型**或是否是 `function` 类型。
- **返回值**：`typeof` 返回一个表示数据类型的**字符串**。
- **适用对象**：`typeof` 对于原始类型（primitive types）和 `function` 的检测非常有用，但对于引用类型（如数组、对象）其结果可能不如 `instanceof` 准确。

#### 常见返回值：
```javascript
console.log(typeof 42);             // "number"
console.log(typeof "hello");        // "string"
console.log(typeof true);           // "boolean"
console.log(typeof undefined);      // "undefined"
console.log(typeof null);           // "object" (历史遗留问题)
console.log(typeof {});             // "object"
console.log(typeof []);             // "object" (数组是对象)
console.log(typeof function(){});   // "function"
console.log(typeof Symbol());       // "symbol"
console.log(typeof 123n);           // "bigint"
```

#### 特点：
- **原始类型识别准确**：`typeof` 可以准确识别 `number`、`string`、`boolean`、`undefined`、`symbol` 和 `bigint`。
- **`null` 特殊情况**：`typeof null` 会返回 `"object"`，这是历史遗留问题。尽管 `null` 是原始类型，`typeof` 仍然将其识别为对象。
- **无法区分对象类型**：对于数组、对象、`null`，`typeof` 都会返回 `"object"`，无法区分它们之间的细微差异。