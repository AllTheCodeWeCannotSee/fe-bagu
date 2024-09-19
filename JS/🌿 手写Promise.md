


![[Pasted image 20240911105443.png]]


#### 🧠 BrainStorm
- this指向
	- 如何处理传入的func？
		- 为func分配resolve、reject。
			- [[为什么 resolve 和 reject 在 new Promise()时就定义好了？]]
			- [[为什么Promise构造函数接受的函数要立即执行？]]
		- resolve、reject做了什么？
			- [[在new Promise时resolve和reject到底做了什么？]]
	- 为什么func要将resolve bind？
		- [[this._resolve.bind(this)]]
	- resolve、reject只接受一个参数
- then
	- [[为什么resolve要用setTimeout()？]]
	- [[then()与resolve()先后执行顺序的影响]]
- 执行异常
	- 如果传入new Promise()的函数中会抛出异常
	- 如果传入then的不是函数
- 异步
	- [[如何实现手写Promise的异步]]
- 链式
	- 


#### 代码

![[Pasted image 20240919102428.png]]

```js
class Commitment {
  constructor(func) {
    this.status = "PENDING";
    this.func = func;
    this.resolveCallbacks = [];
    this.rejectCallbacks = [];

    try {
      this.func(this.resolve.bind(this), this.reject.bind(this));
    } catch (error) {
      this.reject(error);
    }
  }
  resolve(result) {
    setTimeout(() => {
      this.status = "RESOLVED";
      this.result = result;
      this.resolveCallbacks.forEach((callback) => {
        callback(result);
      });
    });
  }
  reject(result) {
    setTimeout(() => {
      this.status = "REJECTED";
      this.result = result;
      this.rejectCallbacks.forEach((callback) => {
        callback(result);
      });
    });
  }
  then(onFULFILLED, onREJECTED) {
    return new Commitment((resolve, reject) => {
      onFULFILLED = typeof onFULFILLED === "function" ? onFULFILLED : () => {};
      onREJECTED = typeof onREJECTED === "function" ? onREJECTED : () => {};

      if (this.status === "RESOLVED") {
        setTimeout(() => {
          onFULFILLED(this.result);
        });
      }
      if (this.status === "REJECTED") {
        setTimeout(() => {
          onREJECTED(this.result);
        });
      }
      if (this.status === "PENDING") {
        this.resolveCallbacks.push(onFULFILLED);
        this.rejectCallbacks.push(onREJECTED);
      }
    });
  }
}


```