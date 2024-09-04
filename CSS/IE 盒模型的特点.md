IE 盒模型（也称为非标准盒模型或怪异盒模型）是指一种不同于标准盒模型的计算元素宽度和高度的方法。这种模型最初由早期的 Internet Explorer（特别是 IE5 及更早版本）引入，因此得名。


### 如何使用 IE 盒模型

在现代浏览器中，可以通过 CSS 的 `box-sizing` 属性来选择使用标准盒模型还是 IE 盒模型。具体设置如下：

- **标准盒模型**（默认行为）：

  ```css
  .element {
    box-sizing: content-box; /* 默认值 */
  }
  ```

- **IE 盒模型**：

  ```css
  .element {
    box-sizing: border-box;
  }
  ```

当使用 `box-sizing: border-box;` 时，元素的宽度和高度属性将包括内容区域、内边距和边框。这样在调整元素的内边距和边框时，不会改变元素的总宽度和高度。


