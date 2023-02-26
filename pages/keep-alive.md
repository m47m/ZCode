- 是vue中的内置组件，能在组件切换过程中将状态保存在内存中，防止重新渲染DOM
- 属性props
	- include 接收字符串或正则表达式
	- exclude 接收字符串或正则表达式
	- max
- 匹配首先检查组件自身的 `name` 选项，如果 `name` 选项不可用，则匹配它的局部注册名称 (父组件 `components` 选项的键值)，匿名组件不能被匹配
- 设置了 keep-alive 缓存的组件，会多出两个生命周期钩子（`activated`与`deactivated`）
-
- 在路由中设置`keepAlive`属性判断是否需要缓存
	- ```
	  {
	  	path:'list',
	      name:'itemlist',
	      component(resolve){
	      	require(['@/pages/item/list'],resolve)
	      },
	      meta:{
	      	keepAlive:true,
	          title:'列表页'
	      }
	  }
	  ```
- ```
  <div id="app" class='wrapper'>
      <keep-alive>
          <!-- 需要缓存的视图组件 --> 
          <router-view v-if="$route.meta.keepAlive"></router-view>
       </keep-alive>
        <!-- 不需要缓存的视图组件 -->
       <router-view v-if="!$route.meta.keepAlive"></router-view>
  </div>
  ```
-