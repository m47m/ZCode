- 在下次 DOM 更新循环结束之后执行延迟回调。在修改数据之后立即使用这个方法，获取更新后的 DOM
- 当数据发生变化，`Vue`将开启一个异步更新队列，视图需要等队列中所有数据变化完成之后，再统一进行更新
- `nextTick`本质是一种优化策略
	- **是将回调函数延迟在下一次dom更新数据后调用**
	- **当数据更新了，在dom中渲染后，自动执行该函数**
-
- 如果想要在修改数据后立刻得到更新后的`DOM`结构，可以使用`Vue.nextTick()`
- 组件内使用 `vm.$nextTick()` 实例方法只需要通过`this.$nextTick()`
- ```
  that.$nextTick(function(){
          console.log(that.$refs.aa.innerText);  //输出：修改后的值
        });
  
  ```
-