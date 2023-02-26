- ## 基本介绍
	- 执行 `Generator` 函数会返回一个遍历器对象，可以依次遍历 `Generator` 函数内部的每一个状态
		- `function`关键字与函数名之间有一个星号
		- 函数体内部使用`yield`表达式，定义不同的内部状态
	-
	- yield关键词可以暂停返回状态，通过next函数才能遍历到下一个返回状态（yield或者是renturn或者是undefined）
	-
	- 调用next方法时传入参数，可以作为上一个yield表达式的值
	-
	- `Generator `函数返回`Iterator`对象，因此我们还可以通过`for...of`进行遍历
- ## 函数异步执行
	- ```
	  const gen = function*(){
	  	const f1 = yield readFile("/etc/fstab");
	      const f2 = yield readFile("/etc/shells");
	      
	      console.log(f1.toString());
	      console.log(f2.toString());
	  }
	  ```
	- async实际上是Generator的语法糖，专门用来处理异步操作，使用上更加简洁。
	  id:: 63e30046-6ed2-4d7a-9488-a4b853971f11
	- ```
	  const gen = async function(){
	  	const f1 = await readFile("/etc/fstab");
	      const f2 = await readFile("/etc/shells");
	      
	      console.log(f1.toString());
	      console.log(f2.toString());
	  }
	  ```
- ## 使用场景
	- 将异步操作同步化表达出来
	- ```
	  function* loadUI(){
	  	showLoadingScreen();
	      yield loadUIDataAsynchronously();
	      hideLoadingScreen();
	  }
	  
	  var loading = loadUI();
	  
	  loading.next();//加载UI 执行返回loadUIDataAsynchronously
	  loading.next();//卸载UI 执行yield下面一行的代码并到return
	  ```
	- 在对象上实现，Iteratior接口
	- ```
	  function* iterEntries(obj){
	  	let keys = Object.keys(obj);
	      for(let i = 0;i<keys.length;i++){
	      	let key = keys[i];
	          yield [key,obj[key]];
	      }
	  }
	  
	  for(let [key ,value] of iterEntries(myObj)){
	  	console.log(key--value);
	  }
	  ```