

### 1. **可继承的 CSS 属性**

可继承的属性主要与**文本内容**和**字体**相关，这些属性往往是页面中的所有子元素都应该一致的。常见的可继承属性有：

- **字体相关属性**：
  - `font-family`：字体家族
  - `font-size`：字体大小
  - `font-style`：字体样式
  - `font-weight`：字体粗细
  - `font-variant`：字体变体
  
- **文本相关属性**：
  - `color`：文本颜色
  - `text-align`：文本对齐方式
  - `line-height`：行高
  - `text-indent`：首行缩进
  - `text-transform`：文本转换（如大写、小写）
  - `letter-spacing`：字母间距
  - `word-spacing`：单词间距
  - `direction`：文本方向（如从左到右 `ltr` 或从右到左 `rtl`）
  - `white-space`：空白处理
  - `visibility`：可见性（在一些特定情况下）

- **列表相关属性**：
  - `list-style`：列表样式（包括 `list-style-type`、`list-style-image`、`list-style-position`）
  
- **表格相关属性**：
  - `border-collapse`：表格边框是否合并
  - `border-spacing`：表格单元格之间的间距
  - `caption-side`：表格标题的位置

- **光标样式**：
  - `cursor`：光标样式

### 2. **不可继承的 CSS 属性**

大多数 CSS 属性是**不可继承的**，这些属性通常涉及**盒模型**、**布局**、**定位**以及**视觉外观**，因为它们通常需要在每个元素上进行独立控制。常见的不可继承属性有：

- **盒模型相关属性**：
  - `margin`：外边距
  - `padding`：内边距
  - `border`：边框（包括 `border-width`、`border-style`、`border-color`）
  - `width`：宽度
  - `height`：高度

- **布局相关属性**：
  - `display`：元素显示类型（如 `block`、`inline`、`flex`、`grid`）
  - `position`：定位方式（如 `absolute`、`relative`）
  - `top`、`right`、`bottom`、`left`：位置偏移
  - `z-index`：层叠顺序
  - `float`：浮动
  - `clear`：清除浮动
  - `overflow`：溢出处理
  - `visibility`：可见性（在大部分情况下不会继承）
  
- **背景相关属性**：
  - `background-color`：背景颜色
  - `background-image`：背景图片
  - `background-repeat`：背景重复方式
  - `background-position`：背景位置
  - `background-size`：背景大小

- **表格相关属性**：
  - `border`：表格边框
  - `width`、`height`：表格单元格的宽度、高度

- **动画和过渡**：
  - `animation`：动画相关属性
  - `transition`：过渡相关属性

- **阴影相关属性**：
  - `box-shadow`：盒子阴影
  - `text-shadow`：文本阴影

- **其他属性**：
  - `opacity`：透明度
  - `transform`：元素变换
  - `pointer-events`：指针事件

