- 在HTML中，slot是Web组件的一个占位符
- ```
  <template id="element-details-template">
    <slot name="element-name">Slot template</slot>
  </template>
  ```
- `template`不会展示到页面中，需要用先获取它的引用，然后添加到`DOM`中
-
- 当使用该组件标签时候，组件标签里面的内容就会自动填坑（替换组件模板中`slot`位置），作为承载分发内容的出口
- 通过`slot`插槽向组件内部指定位置传递内容，完成这个复用组件在不同场景的应用
	- 布局组件、表格列、下拉选、弹框显示内容
-
- 默认插槽
- 具名插槽
- 作用域插槽
-
- 本质上是返回VNode的函数
-
- v-slot指令取代了slot和slot-scope
-