   - 表示唯一的、不可变的值，通常用作对象属性的键，避免冲突。
   - 每个从 `Symbol()` 创建的值都是唯一的。

   ```javascript
   let sym1 = Symbol('description');
   let sym2 = Symbol('description');
   console.log(sym1 === sym2); // false
   ```



- [[Symbol类型的注意事项]]
