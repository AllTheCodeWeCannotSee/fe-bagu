
![[Untitled diagram-2024-09-06-011148.png]]


#### 面试

"JavaScript 由三部分组成：  
1. **ECMAScript（ES）**：定义了 JavaScript 的核心语法和功能，比如变量、函数、控制结构等。  
2. **DOM（文档对象模型）**：允许操作网页中的 HTML 和 XML 文档，控制页面的内容和结构。  
3. **BOM（浏览器对象模型）**：提供与浏览器窗口、导航和历史记录等相关的 API，比如 `window`、`location` 和 `history`。"





### 1. **ECMAScript（ES）**
   - **定义**：ECMAScript 是 JavaScript 的标准化语言规范。它定义了语言的语法、基本功能和核心概念，如变量、数据类型、表达式、操作符、控制语句、函数、对象等。
   - **作用**：ECMAScript 规定了 JavaScript 语言的基本语法和行为，比如如何声明变量、函数如何定义与执行等。它是 JavaScript 的基础部分。
   - **主要内容**：
     - 变量与作用域（如 `var`、`let`、`const`）
     - 数据类型（如字符串、数字、布尔值、对象、数组等）
     - 表达式和操作符（如算术操作、逻辑操作等）
     - 控制结构（如条件语句 `if`、循环语句 `for`、`while` 等）
     - 函数与闭包
     - 异步编程（如 `Promise`、`async/await` 等）
   
   **示例**：
   ```javascript
   let x = 10;
   function sum(a, b) {
     return a + b;
   }
   console.log(sum(5, 7)); // 输出: 12
   ```

### 2. **DOM（Document Object Model，文档对象模型）**
   - **定义**：DOM 是浏览器提供的接口，允许 JavaScript 与 HTML 或 XML 文档交互。它将网页内容以树形结构表示，使得 JavaScript 可以访问和修改页面的结构、样式和内容。
   - **作用**：通过 DOM，JavaScript 能够动态操作 HTML 元素，修改页面内容、添加或删除节点、处理用户输入和交互。
   - **主要功能**：
     - 查找和选择页面元素（如 `document.getElementById()`、`querySelector()` 等）
     - 修改元素的属性、内容和样式（如 `element.innerHTML`、`element.style`）
     - 监听和响应用户事件（如点击、键盘输入等）
     - 动态创建、插入或删除元素节点
   
   **示例**：
   ```javascript
   const element = document.getElementById('myElement');
   element.innerHTML = 'Hello, World!';
   element.style.color = 'blue';
   ```

### 3. **BOM（Browser Object Model，浏览器对象模型）**
   - **定义**：BOM 是浏览器提供的另一组 API，允许 JavaScript 访问和操作浏览器窗口、控制台、导航、位置和历史记录等功能。BOM 使得 JavaScript 可以与浏览器本身交互，而不仅仅是网页内容。
   - **作用**：通过 BOM，JavaScript 可以控制浏览器的行为，如重定向页面、控制浏览器窗口、获取用户浏览器信息、管理浏览历史记录等。
   - **主要功能**：
     - **`window` 对象**：代表浏览器窗口，是 BOM 的核心对象，包含了全局变量、定时器等功能。
     - **`navigator` 对象**：提供有关浏览器和用户操作系统的信息。
     - **`location` 对象**：用于获取或修改当前文档的 URL。
     - **`history` 对象**：用于访问和操作浏览器的历史记录。
     - **定时器功能**：`setTimeout()` 和 `setInterval()` 用于延时和周期性执行代码。
   
   **示例**：
   ```javascript
   // 获取当前页面的 URL
   console.log(window.location.href);

   // 跳转到另一个页面
   window.location.href = 'https://www.example.com';

   // 弹出警告框
   window.alert('Hello, World!');

   // 设置 2 秒后执行的定时器
   setTimeout(() => {
     console.log('2 seconds passed');
   }, 2000);
   ```

