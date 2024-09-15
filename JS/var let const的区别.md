![[Pasted image 20240911202043.png]]


`var`、`let` 和 `const` 是 JavaScript 中声明变量的三种方式，它们在**作用域**、**变量提升**、**可变性**等方面存在明显的区别。下面我们来详细比较它们的不同点：

---

### 1. **作用域（Scope）**

#### `var`
- **函数作用域**：`var` 声明的变量具有函数作用域，如果它在函数内声明，那么它的作用域仅限于该函数。如果它在函数外声明，则它是全局作用域。
- 不能局限在块作用域（如 `if`、`for` 等块中）。

```javascript
function testVar() {
    if (true) {
        var a = 10;
    }
    console.log(a);  // 输出 10, 因为 var 只遵循函数作用域，不是块作用域
}

testVar();
```

#### `let` 和 `const`
- **块作用域**：`let` 和 `const` 声明的变量是块作用域的，意味着它们只在 `{}` 之间的代码块中有效。块作用域包括 `if`、`for` 等代码块。

```javascript
function testLetConst() {
    if (true) {
        let b = 20;
        const c = 30;
    }
    console.log(b);  // 报错, b is not defined
    console.log(c);  // 报错, c is not defined
}

testLetConst();
```

### 2. **变量提升（Hoisting）**

#### `var`
- **变量提升**：`var` 声明的变量会被提升到当前作用域的顶部，但**不会初始化**。这意味着可以在变量声明之前访问到变量，值为 `undefined`。

```javascript
console.log(x);  // 输出 undefined
var x = 5;
```

上面的代码相当于：
```javascript
var x;
console.log(x);  // undefined
x = 5;
```

#### `let` 和 `const`
- **不完全提升**：`let` 和 `const` 也会被提升，但不会初始化。在声明之前访问它们会导致**暂时性死区**（Temporal Dead Zone，TDZ），即在声明之前访问变量会抛出 `ReferenceError`。

```javascript
console.log(y);  // 报错, ReferenceError: Cannot access 'y' before initialization
let y = 10;
```

### 3. **可变性（Reassignment）**

#### `var` 和 `let`
- **可重新赋值**：`var` 和 `let` 声明的变量都可以被重新赋值。

```javascript
var a = 5;
a = 10;  // 可以重新赋值

let b = 15;
b = 20;  // 也可以重新赋值
```

#### `const`
- **不可重新赋值**：`const` 声明的变量是常量，不能重新赋值。一旦初始化后，不能再改变其值。

```javascript
const c = 25;
c = 30;  // 报错, TypeError: Assignment to constant variable.
```

但需要注意的是，**`const` 只保证变量引用的内存地址不变**，如果它引用的是对象或数组，其内容仍然是可以修改的。

```javascript
const obj = { name: "John" };
obj.name = "Doe";  // 允许修改对象的属性
console.log(obj.name);  // 输出: Doe
```

### 4. **重复声明**

#### `var`
- **允许重复声明**：在同一个作用域内，`var` 允许重复声明同名变量，后一次声明会覆盖前一次声明。

```javascript
var x = 5;
var x = 10;  // 允许重复声明
console.log(x);  // 输出: 10
```

#### `let` 和 `const`
- **不允许重复声明**：`let` 和 `const` 不允许在同一个作用域内声明同名变量，否则会抛出错误。

```javascript
let y = 5;
let y = 10;  // 报错, Identifier 'y' has already been declared
```

### 5. **初始化要求**

#### `var` 和 `let`
- **不要求初始化**：`var` 和 `let` 声明变量时可以不初始化。

```javascript
var a;
let b;
```

#### `const`
- **必须初始化**：`const` 声明变量时，必须同时初始化，否则会抛出错误。

```javascript
const c;  // 报错, Missing initializer in const declaration
```

### 6. **全局对象属性**
- 当在全局作用域中声明变量时，`var` 声明的变量会成为全局对象（在浏览器中是 `window` 对象）的属性，而 `let` 和 `const` 声明的变量不会。

```javascript
var x = 10;
console.log(window.x);  // 输出: 10

let y = 20;
console.log(window.y);  // 输出: undefined

const z = 30;
console.log(window.z);  // 输出: undefined
```

---

