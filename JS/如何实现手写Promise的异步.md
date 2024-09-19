
![[Pasted image 20240918095350.png]]


- [[🌿 宏任务与微任务]]


使用setTimeout()放入任务队列

---

![[Pasted image 20240918102146.png]]

- 如果resolve也在setTimeout()，此时Promise.status为pending。需要在Promise.then()方法中进行status === pending的判断。
- 如果是pending就放入数组
- 


