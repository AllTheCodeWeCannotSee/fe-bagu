![[Pasted image 20240915095544.png]]

![[Untitled diagram-2024-09-15-020512.png]]

在 JavaScript 中，**事件捕获**和**事件冒泡**是事件传播的两种机制。它们决定了当一个事件发生在嵌套的 DOM 元素上时，事件如何在元素之间传播。

### 事件传播阶段

事件传播分为三个阶段：
1. **捕获阶段**（Capturing phase）：事件从根节点（`document`）开始向下传播，直到触发事件的目标元素。
2. **目标阶段**（Target phase）：事件到达目标元素，即事件实际发生的元素。
3. **冒泡阶段**（Bubbling phase）：事件从目标元素向上冒泡，经过其祖先元素，直到根节点（`document`）。

### 1. **事件捕获（Capturing phase）**

在捕获阶段，事件从页面的最顶层节点（如 `document`）开始，逐层向下传递到目标元素。这是事件传播的第一个阶段。

- **流程**：`document` → 父级元素 → 子级元素（直到事件目标元素）。
- **特点**：捕获阶段的默认行为不是常用的，因为大部分事件处理发生在冒泡阶段。
  
### 2. **事件冒泡（Bubbling phase）**

事件冒泡是事件传播的最后阶段。在事件冒泡过程中，事件从目标元素开始逐层向上传递，经过所有的祖先元素，直到 `document`。

- **流程**：事件先在目标元素触发，然后向上传递：目标元素 → 父级元素 → `document`。
- **特点**：事件冒泡是默认行为，许多 JavaScript 事件监听依赖于事件冒泡。

### 捕获与冒泡的控制

JavaScript 提供了 `addEventListener` 方法来控制事件是在捕获阶段还是冒泡阶段执行。默认情况下，事件监听是在冒泡阶段执行。

```javascript
element.addEventListener(event, handler, useCapture);
```

- **event**：事件类型，例如 `click`。
- **handler**：事件触发时执行的函数。
- **useCapture**：布尔值，默认为 `false`，表示在冒泡阶段触发。如果设置为 `true`，则在捕获阶段触发。

### 示例

假设有以下 HTML 结构：

```html
<div id="parent">
  <button id="child">Click me</button>
</div>
```

我们可以添加捕获和冒泡阶段的事件监听：

```javascript
const parent = document.getElementById('parent');
const child = document.getElementById('child');

// 捕获阶段监听
parent.addEventListener('click', function() {
  console.log('Parent captured');
}, true); // useCapture 为 true

// 冒泡阶段监听
parent.addEventListener('click', function() {
  console.log('Parent bubbled');
}, false); // useCapture 为 false（默认）

child.addEventListener('click', function() {
  console.log('Child clicked');
});
```

点击按钮时，输出顺序为：
1. `Parent captured` （捕获阶段，父元素先捕获事件）
2. `Child clicked` （目标阶段，事件到达目标元素）
3. `Parent bubbled` （冒泡阶段，事件冒泡回父元素）

### 阻止事件冒泡

如果你不希望事件冒泡，可以在事件处理函数中使用 `event.stopPropagation()`：

```javascript
child.addEventListener('click', function(event) {
  event.stopPropagation();  // 阻止事件冒泡
  console.log('Child clicked');
});
```

现在点击按钮后，只有 `Child clicked` 会被输出，事件不会冒泡到父元素。

### 总结

- **事件捕获**：从根节点向下传播，逐层到达目标元素。
- **事件冒泡**：从目标元素向上传递，经过其祖先节点，直到根节点。
- 使用 `addEventListener` 的第三个参数可以指定是在捕获阶段还是冒泡阶段触发监听器。
- 使用 `event.stopPropagation()` 可以阻止事件传播。

这两个机制帮助开发者在复杂的 DOM 结构中灵活处理事件。