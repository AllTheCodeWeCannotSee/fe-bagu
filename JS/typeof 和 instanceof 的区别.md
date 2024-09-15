在 JavaScript 中，`typeof` 和 `instanceof` 都是用于检测变量类型的操作符，但它们的用途和功能有所不同。下面是对它们的详细解释和区别：

- [[typeof]]
- [[instanceof]]

### **`typeof` 和 `instanceof` 的区别**

| 特性                     | **`typeof`**                                | **`instanceof`**                         |
|--------------------------|---------------------------------------------|------------------------------------------|
| **检测对象**             | 原始类型、`function`、`object`              | 引用类型（如数组、对象、函数等）         |
| **返回类型**             | **字符串**，如 `"number"`、`"string"`        | **布尔值**，如 `true` 或 `false`         |
| **适用范围**             | 原始类型（number、string、boolean 等）       | 引用类型（如数组、函数、对象、日期等）   |
| **能否区分对象类型**     | 无法区分数组、对象等引用类型                | 可以区分对象是否为某构造函数的实例       |
| **检测 `null` 的表现**   | `typeof null` 返回 `"object"`                | 无法检测 `null`，只能用于引用类型        |
| **适用于原始类型**       | 是的，能检测 `number`、`string` 等原始类型  | 否，无法检测原始类型                     |
| **适用于引用类型**       | 可以检测是否是 `"object"` 或 `"function"`     | 可以检测对象是否继承自某个构造函数的原型 |

### **应用场景对比**

#### 1. **`typeof` 用于检测原始类型**：
`typeof` 更适合用于检测变量的原始类型，特别是当你想确定某个变量是 `number`、`string` 或 `boolean` 等基础类型时。

```javascript
let x = "Hello";
if (typeof x === 'string') {
  console.log('x 是一个字符串');
}
```

#### 2. **`instanceof` 用于检测对象的原型链**：
`instanceof` 更适合用于检测对象是否为某个构造函数的实例，特别是在需要确认一个对象是否是某个类的实例时非常有用。

```javascript
let arr = [];
if (arr instanceof Array) {
  console.log('arr 是一个数组');
}
```

