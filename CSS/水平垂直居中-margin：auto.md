
如果元素的宽高是固定的，可以通过设置 `margin: auto` 实现水平垂直居中。

#### 实现方法：
- 将元素的上下左右 `margin` 设置为 `auto`。
- 确保元素的宽高是固定的，并且父容器有定义的宽高。

#### 示例：
```html
<div class="container">
  <div class="child">Centered</div>
</div>

<style>
  .container {
    height: 300px;
    background-color: lightgray;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .child {
    margin: auto; /* 水平和垂直居中 */
    width: 100px;
    height: 100px;
    background-color: red;
  }
</style>
```
