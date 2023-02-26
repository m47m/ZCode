- 微任务：一个需要异步执行的函数
	- 在主函数执行结束之后，当前宏任务结束之前
	- Promise.then
	- MutaionObserver
	- process.nextTick
- 宏任务：时间粒度比较大， 执行的时间间隔不能精确控制
	- script
	- setTimeout
	- UI rendering
	- postMessage
	- setImmediate
- ```
  console.log(1)
  setTimeout(()=>{
      console.log(2)
  }, 0)
  new Promise((resolve, reject)=>{
      console.log('new Promise')
      resolve()
  }).then(()=>{
      console.log('then')
  })
  console.log(3)
  
  // 输出为  1 new Promise 3 then 2
  ```
-
-