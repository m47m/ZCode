- 作用都是动态修改当前函数内部环境对象this的指向
-
- call和apply是改变后页面加载之后立即执行，是同步代码
- bind是异步代码，改变后不会立即执行，而是返回一个新的函数
-
- call和bind传参是一个一个传入，不能使用剩余参数传参
- apply可以使用数组的方式传入
-
- call和apply是临时修改一次this指向
- bind是返回一个永久修改的函数
-
- bind手写实现
	- ```
	  Function.prototype.bind = function (context) {
	      // 调用 bind 的不是函数，需要抛出异常
	      if (typeof this !== "function") {
	        throw new Error("Function.prototype.bind - what is trying to be bound is not callable");
	      }
	      
	      // this 指向调用者
	      var self = this;
	      // 实现第2点，因为第1个参数是指定的this,所以只截取第1个之后的参数
	      var args = Array.prototype.slice.call(arguments, 1); 
	      
	      // 实现第3点,返回一个函数
	      return function () {
	          // 实现第4点，这时的arguments是指bind返回的函数传入的参数
	          // 即 return function 的参数
	          var bindArgs = Array.prototype.slice.call(arguments);
	          // 实现第1点
	          return self.apply( context, args.concat(bindArgs) );
	      }
	  }
	  ```
	- ((63d529e0-7c13-4909-bc1f-5e2a48af2656))
	- ```
	  Function.prototype.myBind = function(context){
	  	if(typeof this != function){
	      	throw new Error('type error');
	      }
	      
	      const args = [...arguments].slice(1);
	      const self = this;
	      
	      const fToBind = function(){
	      	console.log(arguments);//返回函数的参数
	          const isNew = this instanceof fToBind;
	          const context = isNew? this:Object(args);
	          return self.apply(context,args.concat([...arguments]));
	      }
	      //返回的函数拥有其构造函数原型上的方法
	      if(self.prototype){
	      	// Object.create拷贝原型对象	
	      	fToBind.prototype = Object.create(self.prototype);
	         
	      }
	      
	      //也可以通过原型继承
	      let fNop = function(){};
	      fNop.prototype = this.prototype;
	      fBound.prototype = new fNop();
	      
	      return fToBind;
	  }
	  ```
- call手写实现
	- ```
	  //call方法，在使用一个指定的this和若干个指定的参数值的前提下，调用某个函数或方法
	  
	  var obj = {
	  	value:"test1",
	  }
	  
	  function fn(){
	  	console.log(this.value);
	  }
	  
	  fn.call(obj);//test1
	  ```
	- ```
	  Function.prototype.myCall = function(context){
	  	//判断调用对象是否为函数
	      if(typeof this != "function"){
	      	throw new Error("Type error");
	      }
	      
	      //获取除了第一个context之外的参数
	      let args = [...arguments].slice(1);
	   	let result = null;
	      
	      //判断context是否传入
	      context = context || window;
	      
	      //将被调用的方法this（函数）设置为context的属性
	      
	      context.fn = this;
	      
	      //执行方法，将数组遍历
	      result = context.fn(...args);
	      
	      delete context.fn;
	      
	      return result;
	      
	  }
	  ```
-
- apply手写实现
	- ```
	  //与call方法的区别在于，传参方式不同
	  Function.prototype.myApply = function(context){
	  	if(typeof this != "function"){
	      	throw new Error("type error");
	      }
	      
	      let result = null;
	      
	      context = context || window;
	      
	      //使用Symbol来保证属性唯一
	      const fnSymbol = Symbol();
	      context[fnSymbol] = this;
	      
	      //传入的数组是否存在
	      if(arguments[1]){
	      	result = context[fnSymbol](...arguments[1]);
	      }else{
	      	result = context[fnSymbol]();
	      }
	      
	      delete context[fnSymbol];
	      
	      return result;
	  }
	  ```