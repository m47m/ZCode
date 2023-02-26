- ```
  function myNew(context){
  	const obj = new Object();
      obj.__proto__ = context.prototype;
      
      //使用context进行构建函数。执行构造函数的代码，参数取出第一个context
      const res = context.apply(obj,[...arguments].slice(1));
      
      return typeof res === 'object' ? res : obj;
  }
  ```