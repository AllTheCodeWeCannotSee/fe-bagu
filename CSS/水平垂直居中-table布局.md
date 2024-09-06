

通过将父元素的 `display` 设置为 `table`，子元素设置为 `table-cell`，然后使用 `vertical-align` 和 `text-align` 实现水平垂直居中。

#### 实现方法：
- 父容器使用 `display: table`。
- 子元素使用 `display: table-cell`，并通过 `vertical-align: middle` 实现垂直居中。
- 使用 `text-align: center` 实现水平居中。

#### 示例：
```html
<div class="container">
  <div class="child">Centered</div>
</div>

<style>
  .container {
    display: table;
    width: 100%;
    height: 300px;
    background-color: lightgray;
  }
  .child {
    display: table-cell;
    vertical-align: middle; /* 垂直居中 */
    text-align: center; /* 水平居中 */
  }
</style>
```

