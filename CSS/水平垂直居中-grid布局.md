#### 实现方法：
- 将父容器的 `display` 设置为 `grid`。
- 使用 `place-items: center` 实现水平和垂直居中。

#### 示例：
```html
<div class="container">
  <div class="child">Centered</div>
</div>

<style>
  .container {
    display: grid;
    place-items: center; /* 水平和垂直居中 */
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
