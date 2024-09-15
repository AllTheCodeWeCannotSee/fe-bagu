   - 用于表示任意精度的整数，可以处理比 `number` 类型更大的整数。
   - 通过在数字后加 `n` 来创建 `bigint` 类型。

   ```javascript
   let bigIntNum = 1234567890123456789012345678901234567890n;
   console.log(typeof bigIntNum); // "bigint"
   ```
