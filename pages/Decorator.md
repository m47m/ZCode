- 在不改变原类和使用继承的情况下，动态地扩展对象功能的设计理论
- 优点
	- 代码可读性变强
	- 对功能进行扩展
- 使用
	- 类的装饰
	- ```
	  function testable(isTestable){
	  	return function(target){
	      	target.isTestable = isTestable;
	      }
	  }
	  
	  @testable(true)
	  calss MyTestableClass{}
	  
	  
	  MyTestableClass.isTestable;//true
	  
	  
	  ```
	- 类的属性的装饰
	- ```
	  function readonly(target, name, descriptor){
	    descriptor.writable = false; // 将可写属性设为false
	    return descriptor;
	  }
	  ```
	- 装饰器不能用于修饰函数
- 场景
	-