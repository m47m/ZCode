- `Vue3`中已废弃`filter`
- ```
  <!-- 在双花括号中 -->
  {{ message | capitalize }}
  
  <!-- 在 `v-bind` 中 -->
  <div v-bind:id="rawId | formatId"></div>
  ```
-
- message 是第一个参数，而capitalize是过滤器id
- 局部过滤器优先于全局过滤器被调用
- 一个表达式可以使用多个过滤器。过滤器之间需要用管道符“|”隔开。其执行顺序从左往右
- 过滤器可以新增参数`capitalize(arg1,arg2)`
-
-
- 在组件options选项中定义过滤器
	- ```
	  filters:{
	  	capitalize: function(value){
	      	if(!value) return ""
	          value = value.toString()
	          return value.charAt(0).toUpperCase + value.slice()
	      }
	  }
	  ```
- 定义全局过滤器
	- ```
	  Vue.filter('capitalize',function(value){
	  	
	  })
	  
	  new Vue(){
	  
	  }
	  ```
-
- 应用场景
	- 单位转换、数字打点、文本格式化、时间格式化
-
-