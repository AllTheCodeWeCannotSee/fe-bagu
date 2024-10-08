BFC 是一个独立的渲染区域，元素在这个区域内的布局不会影响到区域外的元素，处理浮动元素、边距重叠、清除浮动等问题时有用。

- [[浮动元素]]
- [[边距重叠]]



### BFC 的触发条件

以下情况会创建 BFC：

1. **根元素**：如 `<html>`。
2. **浮动元素**：元素设置 `float` 为 `left`、`right`。
3. **绝对定位或固定定位的元素**：元素的 `position` 设置为 `absolute` 或 `fixed`。
4. **行内块元素**：元素的 `display` 设置为 `inline-block`。
5. **overflow 不为 `visible` 的块级元素**：元素的 `overflow` 设置为 `hidden`、`scroll`、`auto`。
6. **表格单元格和表格标题**：元素的 `display` 设置为 `table-cell` 或 `table-caption`。
7. **弹性布局元素**：元素的 `display` 设置为 `flex` 或 `inline-flex`。
8. **网格布局元素**：元素的 `display` 设置为 `grid` 或 `inline-grid`。

### BFC 的特性

1. **内部的盒子会在垂直方向，一个接一个地放置**。也就是说，BFC 内部的盒子会像普通文档流那样按顺序排列。

2. **同一个 BFC 下的元素的垂直外边距会发生重叠**。这意味着，如果两个元素在同一个 BFC 内，它们的外边距会重叠，而不是相加。

3. **BFC 区域不会与浮动元素重叠**。这意味着 BFC 会自动适应浮动元素的布局，不会与其发生重叠。

4. **BFC 是一个独立的容器，内部的元素不会影响外部的布局**。反之亦然，外部元素也不会影响到 BFC 内部的布局。

5. **计算 BFC 的高度时，浮动元素也会被计算在内**。这对于清除浮动非常有用，能够防止容器因为内部元素浮动而发生高度塌陷。

### BFC 的应用场景

1. **解决浮动引起的高度塌陷**：父元素包含浮动的子元素时，父元素可能会因为没有包含浮动元素而高度塌陷。通过触发父元素的 BFC，可以解决这个问题。
   
   ```css
   .clearfix {
       overflow: hidden; /* 触发 BFC */
   }
   ```

2. **防止外边距重叠**：两个相邻的块级元素会出现垂直方向上的外边距重叠，通过将其中一个元素放入 BFC 可以避免这种情况。

   ```css
   .no-margin-collapse {
       overflow: hidden; /* 触发 BFC */
   }
   ```

3. **避免与浮动元素的重叠**：当元素不希望与旁边的浮动元素重叠时，可以通过触发 BFC 来避免重叠。

   ```css
   .clear-floats {
       overflow: auto; /* 触发 BFC */
   }
   ```

