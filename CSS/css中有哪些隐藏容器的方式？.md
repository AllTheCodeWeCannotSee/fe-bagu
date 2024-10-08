
![[Untitled diagram-2024-09-06-004707.png]]

在 CSS 中有多种方式可以隐藏元素或容器，每种方式的效果和作用都略有不同。以下是几种常见的隐藏方法及其区别：

### 1. `display: none`

- **效果**：将元素从文档流中完全移除，页面布局和元素渲染都会忽略它，元素不占用任何空间。
- **特点**：
  - 不仅看不到元素，元素也不会占用任何空间，其他元素会重新排版。
  - 元素及其子元素不会被渲染，因此 JavaScript 事件监听器无法作用于该元素。
  - 不会影响屏幕阅读器的输出，屏幕阅读器无法“读到”这个元素。
  
- **示例**：
  ```css
  .hidden {
      display: none;
  }
  ```

### 2. `visibility: hidden`

- **效果**：元素仍然占据布局空间，但内容不可见。
- **特点**：
  - 元素在文档流中保留位置，但内容不可见。
  - JavaScript 仍然可以与元素交互（事件监听器有效）。
  - 屏幕阅读器仍然可以“读到”该元素的内容。
  
- **示例**：
  ```css
  .hidden {
      visibility: hidden;
  }
  ```

### 3. `opacity: 0`

- **效果**：将元素的透明度设置为 0，使元素完全透明，但它仍然可见并占据空间。
- **特点**：
  - 元素在页面上仍占据空间，并保持其原来的布局。
  - 元素保持渲染状态，JavaScript 事件监听器可以捕捉到它。
  - 屏幕阅读器仍然可以“读到”该元素的内容。
  
- **示例**：
  ```css
  .hidden {
      opacity: 0;
  }
  ```

### 4. `position: absolute` 或 `position: fixed` + `left: -9999px` 或 `top: -9999px`

- **效果**：通过将元素移到视口外来隐藏它。
- **特点**：
  - 元素从视口内消失，但仍然存在于页面的布局中，保持原有的功能。
  - 元素可以响应 JavaScript 事件，但由于它被移出视口，用户无法与之交互。
  - 屏幕阅读器仍能读到它的内容。
  
- **示例**：
  ```css
  .hidden {
      position: absolute;
      left: -9999px;
  }
  ```

### 5. `clip` 或 `clip-path`

- **效果**：使用 `clip` 或 `clip-path` 将元素裁剪，使其不可见。
- **特点**：
  - 元素仍然占据布局空间。
  - JavaScript 可以与该元素交互。
  - 屏幕阅读器通常仍能读取被裁剪的元素。
  
- **示例**：
  ```css
  .hidden {
      position: absolute;
      clip: rect(0, 0, 0, 0); /* 裁剪区域为0 */
  }
  ```

### 6. `transform: scale(0)`

- **效果**：通过缩放将元素大小设置为 0，使元素不可见。
- **特点**：
  - 元素仍然占据布局空间。
  - 元素的 JavaScript 事件仍可被触发。
  - 屏幕阅读器可以读取该元素的内容。

- **示例**：
  ```css
  .hidden {
      transform: scale(0);
  }
  ```

### 7. `z-index: -1` 或 `z-index` 低于其他元素

- **效果**：将元素的 `z-index` 设置为负值，使其被其他元素覆盖，从而隐藏。
- **特点**：
  - 元素仍然占据空间并参与布局。
  - 由于它仍然在页面上，JavaScript 事件可以触发该元素。
  - 屏幕阅读器仍可以读取它。
  - **注意**：如果设置了 `z-index: -1`，该元素可能会被其他元素完全遮盖，但它的空间和行为仍然存在。

- **示例**：
  ```css
  .hidden {
      z-index: -1;
  }
  ```

### 各种方法的区别

| 方法                          | 占据空间 | 可见性 | 是否渲染 | 可被 JavaScript 交互 | 屏幕阅读器是否可读 |
| --------------------------- | ---- | --- | ---- | ---------------- | --------- |
| `display: none`             | 否    | 否   | 否    | 否                | 否         |
| `visibility: hidden`        | 是    | 否   | 是    | 是                | 是         |
| `opacity: 0`                | 是    | 否   | 是    | 是                | 是         |
| `position: absolute` + 移出视口 | 否    | 否   | 是    | 是                | 是         |
| `clip: rect(0, 0, 0, 0)`    | 是    | 否   | 是    | 是                | 是         |
| `transform: scale(0)`       | 是    | 否   | 是    | 是                | 是         |
| `z-index: -1`               | 是    | 否   | 是    | 是                | 是         |

### 选择合适的隐藏方法

[[例子-隐藏容器]]