**Flexbox**（弹性盒布局）是 CSS3 中的一种强大的布局方式，它可以高效地排列、对齐和分配容器内元素的空间。

### Flexbox 的核心概念

1. **Flex 容器（Flex Container）**：设置 `display: flex` 或 `display: inline-flex` 的元素即为弹性容器，容器中的子元素称为**Flex 项目（Flex Items）**。
   
   ```css
   .container {
     display: flex;
   }
   ```

2. **Flex 项目（Flex Items）**：Flex 容器内部的所有直接子元素，称为 Flex 项目，Flexbox 的布局规则直接作用在这些项目上。

### 主要属性

Flexbox 的属性分为两类：**容器属性** 和 **项目属性**。

#### 1. 容器属性

这些属性应用在 **Flex 容器** 上，控制容器中 Flex 项目的排列方式和布局行为。

- **`flex-direction`**：定义项目的主轴方向（即项目的排列方向）。
  - `row`（默认）：项目从左到右排列。
  - `row-reverse`：项目从右到左排列。
  - `column`：项目从上到下排列。
  - `column-reverse`：项目从下到上排列。

  ```css
  .container {
    flex-direction: row; /* 默认值 */
  }
  ```

- **`justify-content`**：定义项目在主轴上的对齐方式。
  - `flex-start`（默认）：项目从起点开始排列。
  - `flex-end`：项目从终点开始排列。
  - `center`：项目在主轴居中排列。
  - `space-between`：项目在主轴上均匀分布，第一个项目和最后一个项目分别贴靠容器两端。
  - `space-around`：项目之间有相等的间距，且首尾项目和容器边缘有半个间距。
  
  ```css
  .container {
    justify-content: center; /* 项目在主轴居中 */
  }
  ```

- **`align-items`**：定义项目在交叉轴上的对齐方式。
  - `stretch`（默认）：项目拉伸以填充容器的高度。
  - `flex-start`：项目在交叉轴的起点对齐。
  - `flex-end`：项目在交叉轴的终点对齐。
  - `center`：项目在交叉轴居中对齐。
  - `baseline`：项目的文本基线对齐。

  ```css
  .container {
    align-items: flex-start; /* 项目在交叉轴的起点对齐 */
  }
  ```

- **`flex-wrap`**：定义项目是否在一行中排列（默认不换行），还是可以换行。
  - `nowrap`（默认）：项目不换行，所有项目都在一行内排列。
  - `wrap`：项目自动换行，超出容器宽度的项目会移动到下一行。
  - `wrap-reverse`：与 `wrap` 类似，但项目从下往上排列。

  ```css
  .container {
    flex-wrap: wrap; /* 项目换行 */
  }
  ```

- **`align-content`**：定义多行项目的对齐方式（当 `flex-wrap` 为 `wrap` 时使用）。
  - `stretch`（默认）：各行将拉伸以占满整个容器的空间。
  - `flex-start`：各行向容器顶部对齐。
  - `flex-end`：各行向容器底部对齐。
  - `center`：各行在容器内居中。
  - `space-between`：各行之间的间距相等，第一行与最后一行靠近容器边缘。
  - `space-around`：各行之间的间距相等，且首尾行与容器边缘之间有间距。

  ```css
  .container {
    align-content: center; /* 各行在容器内居中 */
  }
  ```

#### 2. 项目属性

这些属性应用在 **Flex 项目** 上，控制单个项目在 Flex 容器中的布局方式。

- **`flex-grow`**：定义项目的放大比例，当有剩余空间时，项目按比例放大。默认值是 `0`，即项目不放大。
  
  ```css
  .item {
    flex-grow: 1; /* 项目可以按比例放大 */
  }
  ```

- **`flex-shrink`**：定义项目的缩小比例，当空间不足时，项目按比例缩小。默认值是 `1`，即项目可以缩小。

  ```css
  .item {
    flex-shrink: 1; /* 项目可以按比例缩小 */
  }
  ```


