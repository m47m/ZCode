- ```
  function myInstanceof(target,origin){
  	if(typeof target !== "object" || target = null) return false;
      if(typeof origin !== "function") //!== 只有相同类型才会比较
      	throw new TypeError("origin must be function");
      
      let proto = Object.getPrototypeOf(target);//proto = target.__proto__
      while(proto){
      	if(proto === origin.prototype) return true;
          proto = Objcet.getPrototypeOf(proto); //循环向上请求原型链
      }
      
      return false;
  }
  ```