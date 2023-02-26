- Vue.observable，让一个对象变为响应式数据。
	- Vue内部会用它来处理date函数返回的对象
- 在非父子组件通信时，可以使用通常的`bus`或者使用`vuex`，但是实现的功能不是太复杂，而使用上面两个又有点繁琐。这时，`observable`就是一个很好的选择
-
- ```
  //创建一个js文件
  import Vue form 'vue'
  
  创建state对象，使用observable使对象可响应
  
  export let state = Vue.observable({
  	name :'张三',
      'age': 38
  })
  
  export let mutations = {
  	changeName(name){
      	state.name = name;
      },
      setAge(age){
      	state.age = age;
      }
  }
  ```
- ```
  //在.vue文件中直接使用
  import {state,mutations} from ''
  
  export default{
  	//在计算属性拿到state中的值
      computed:{
      	name(){
          	return state.name
          },
          age(){
          	return state.age
          }
      },
      
      methods:{
      	chageName:mutations.changeName,
          setAge:mutations.setAge
      }
  }
  ```