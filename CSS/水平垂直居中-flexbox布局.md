#### 实现方法：
- 将父容器的 `display` 设置为 `flex`。
- 使用 `justify-content: center` 来实现水平居中。
- 使用 `align-items: center` 来实现垂直居中。

#### 示例：
```html
<div class="container">
  <div class="child">Centered</div>
</div>

<style>
  .container {
    display: flex;
    justify-content: center; /* 水平居中 */
    align-items: center; /* 垂直居中 */
    height: 300px; /* 必须设置高度 */
    background-color: lightgray;
  }
  .child {
    width: 100px;
    height: 100px;
    background-color: red;
  }
</style>
```
