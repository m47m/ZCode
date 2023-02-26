- gradle-to-grave
- 在`Vue`生命周期钩子会自动绑定 `this` 上下文到实例中，因此你可以访问数据，对 `property` 和方法进行运算这意味着**你不能使用箭头函数来定义一个生命周期方法** (例如 `created: () => this.fetchTodos()`)
-
- 八个阶段：创建前后、载入前后、更新前后、销毁前后
	- | 生命周期 | 描述 |
	  | ---- | ---- | ---- |
	  | beforeCreate | 执行时组件实例还未创建，通常用于插件开发中执行一些初始化任务 |
	  | created | 组件初始化完毕，各种数据可以使用，常用于异步数据获取 |
	  | beforeMount | 未执行渲染、更新，dom未创建 |
	  | mounted | 初始化结束，dom已创建，可用于获取访问数据和dom元素 |
	  | beforeUpdate | 更新前，可用于获取更新前各种状态 |
	  | updated | 更新后，所有状态已是最新 |
	  | beforeDestroy | 销毁前，可用于一些定时器或订阅的取消 |
	  | destroyed | 组件已销毁，作用同上 |
-