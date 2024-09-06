#### 1. 水平居中和垂直居中
```html
<div class="container">
  <div class="item">Centered</div>
</div>

<style>
  .container {
    display: flex;
    justify-content: center; /* 水平居中 */
    align-items: center; /* 垂直居中 */
    height: 100vh; /* 容器高度 */
  }
  .item {
    width: 100px;
    height: 100px;
    background-color: red;
  }
</style>
```

#### 2. 三列等宽布局
```html
<div class="container">
  <div class="item">Column 1</div>
  <div class="item">Column 2</div>
  <div class="item">Column 3</div>
</div>

<style>
  .container {
    display: flex;
  }
  .item {
    flex-grow: 1; /* 每列等宽 */
    padding: 10px;
    background-color: lightgray;
    border: 1px solid #000;
  }
</style>
```

#### 3. 响应式换行布局
```html
<div class="container">
  <div class="item">Item 1</div>
  <div class="item">Item 2</div>
  <div class="item">Item 3</div>
  <div class="item">Item 4</div>
  <div class="item">Item 5</div>
</div>

<style>
  .container {
    display: flex;
    flex-wrap: wrap; /* 自动换行 */
  }
  .item {
    flex-basis: 200px;
    margin: 10px;
    background-color: lightblue;
  }
</style>
```
