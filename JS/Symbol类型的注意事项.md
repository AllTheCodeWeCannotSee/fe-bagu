![[Pasted image 20240910200640.png]]


假设我们有一个皇帝的对象，其中包含了皇子的名字和公主的名字。然而，皇帝有一个“私生子”，这个信息我们不希望在普通情况下被访问到或遍历出来。因此，我们需要一个方式将这个私生子的信息隐藏起来，同时仍然能够通过特殊方式访问。这时，`Symbol` 就派上用场了。



#### 覆盖
在普通的对象中，如果我们定义一个属性，后面再用相同的键定义新的属性，旧的属性会被覆盖。比如在例子中：

```javascript
let emperor = {
  prince: ['prince1', 'prince2', 'prince3'],
  princess: ['princess1', 'princess2', 'princess3'],
  prince: 'bastard' // 这个会覆盖前面的 prince 属性
};

console.log(emperor);
```

输出结果：
```javascript
{
  prince: "bastard",  // 之前的 "prince1", "prince2", "prince3" 被覆盖
  princess: ["princess1", "princess2", "princess3"]
}
```

这里可以看到，`prince` 的数组被覆盖成了 `bastard`（私生子），这不是我们想要的结果。

![[Pasted image 20240910201021.png]]

- ⬆️后面的prince会将前面的覆盖



#### 不会覆盖

![[Pasted image 20240910201102.png]]
- ⬆️ 不会覆盖

`Symbol` 是一种独特的、不可重复的标识符，适合用于定义一些属性，且不会与对象中的其他属性冲突，**不会被 `for...in` 或 `Object.keys()` 遍历到**。用 `Symbol` 来定义私生子时，其他代码就无法无意中覆盖或枚举这个私生子属性。

```javascript
let emperor = {
  prince: ['prince1', 'prince2', 'prince3'],
  princess: ['princess1', 'princess2', 'princess3'],
};

const prince = Symbol('bastard');
emperor[prince] = 'bastard';  // 用 Symbol 定义私生子

console.log(emperor);
```

输出结果：
```javascript
{
  prince: ["prince1", "prince2", "prince3"],
  princess: ["princess1", "princess2", "princess3"],
  Symbol(bastard): "bastard"
}
```

- 通过 `Symbol`，我们为皇帝对象定义了一个属性，名字是私生子，但这个属性不会影响其他现有的属性。
- `Symbol` 的独特性确保了属性键不会与其他属性冲突，也不会被无意中覆盖。





#### `Symbol` 的不可枚举性
`Symbol` 属性不会出现在 `for...in` 循环或者 `Object.keys()` 这样的枚举操作中，因此这个“私生子”是隐藏的，不容易被普通方式发现。

```javascript
for (let key in emperor) {
  console.log(key);  // 这里只会打印 prince 和 princess，不会打印 Symbol 属性
}
```

但是，可以通过特殊方法 `Object.getOwnPropertySymbols()` 来访问 `Symbol` 属性：
```javascript
let symbols = Object.getOwnPropertySymbols(emperor);
console.log(symbols);  // 打印出 Symbol(bastard)
```
