- **混入**
- 面向对象程序设计语言中的类
- 其他类可以访问`mixin`类的方法而不必成为其子类
- 在需要该功能时“混入”，有利于代码复用又避免了多继承的复杂
-
- 只要将共用的功能以对象的方式传入 `mixins`选项中
	- ```
	  var myMixin = {
	    created: function () {
	      this.hello()
	    },
	    methods: {
	      hello: function () {
	        console.log('hello from mixin!')
	      }
	    }
	  }
	  
	  //组件通过mixins属性调用mixin对象
	  Vue.component('componentA',{
	  	mixins:[myMixin]
	  })
	  
	  ```
	- 全局混入
	- ```
	  Vue.mixin({
	  	created: function(){
	      	console.log("全局混入")
	      }
	  })
	  ```
-
-