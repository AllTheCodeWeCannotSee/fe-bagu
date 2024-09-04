
以下是使用 JavaScript 实现防抖的一个简单示例：

```js
import React, { useState, useRef } from 'react';

const useDebounce = (func, delay) => {
    const timeoutRef = useRef(null);

    return (...args) => {
        if (timeoutRef.current) {
            clearTimeout(timeoutRef.current);
        }
        timeoutRef.current = setTimeout(() => {
            func.apply(this, args);
        }, delay);
    };
};

const DebouncedInput = () => {
    const [inputValue, setInputValue] = useState('');

    const handleInput = useDebounce((event) => {
        console.log('Input value:', event.target.value);
        // 你可以在这里处理输入框的值，例如发送请求
    }, 100);

    return (
        <input
            type="text"
            value={inputValue}
            onChange={(e) => {
                setInputValue(e.target.value);
                handleInput(e); // 使用防抖后的事件处理函数
            }}
            placeholder="Type something..."
        />
    );
};

export default DebouncedInput;
```


在这个例子中，`handleInput` 函数只有在用户停止输入 300 毫秒后才会被执行。这种方式有效地减少了不必要的函数执行次数，提高了应用的性能。

