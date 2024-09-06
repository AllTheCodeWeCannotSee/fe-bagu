#### 默认绑定

![[Pasted image 20240906104405.png]]


- 在严格模式下，函数中的 this 如果没有明确绑定，将是 undefined。它不会默认指向 window。

#### 隐式绑定

![[Pasted image 20240906104729.png]]

- girl.detail()：调用detail()的是girl，所以this.name为小红
- girl.woman.detail()：调用detail()的是girl.woman，所以this.name为小黄
- girl.special()：调用special()的是girl，所以this.name为小红


#### 综合

![[Pasted image 20240906110619.png]]

a():
1. 在全局定义 var name = "小红"，会导致window.name = "小红"
2. 因为没有对象调用a()，所以是全局对象调用的
3. a()的结果是"小红"


c():
1. c是一个全局定义的函数
2. c()的结果是"小红"


b.a():
1. 结果是“小黄”

d(b.detail)
1. 结果是“小红”

e():
1. 结果是“小红”