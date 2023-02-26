- ```
  function promisify1 (fn ,context){
  	return function(...args){
      	return  new Promise((resolve,reject) => {
          	fn.apply(context,[...args,(err,res) =>{
              	err?reject(err): resolve(res);
              }])
          })
      }
  }
  
  // 我们希望调用的方式是
  const proxy = promisify(asyncFn)
  proxy(11,22).then(res => {
          // 此处输出异步函数执行结果
          console.log(res)
  })
  ```
- 手动实现一个promisify函数的意思是：我们把一个异步请求的函数，封装成一个可以具有 `then`方法的函数，并且在`then`方法中返回异步方法执行结果的这么一个函数。
-