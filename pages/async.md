- async用来声明一个异步方法，[[await]]用来等待异步方法的执行
-
- async返回一个promise对象
	- ```
	  function fn(){
	  	return Promise.resolve("Test");
	  }
	  
	  async function fn2(){
	  	return "Test";
	  }
	  
	  ```
- await后面跟一个Promise对象，返回该对象的结果。
	- await永远都会阻塞后面的代码，即加入微任务队列（这一行除外）。先执行后面的同步代码
	- ```
	  async function fn(){
	  	console.log(1);
	      await fn2();
	      console.log(2);
	  }
	  
	  async function fn2(){
	  	console.log(fn2);
	  }
	  
	  fn()
	  console.log(3);
	  
	  // 1 fn2 3 2
	  ```
-