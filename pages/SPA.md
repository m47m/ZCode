- single page application
- 通过动态重写当前页面与用户交互
- react、vue、angular、ember都属于SPA
- | | 单页面应用（SPA） | 多页面应用（MPA） |
  | :-- | :-- | :-- |
  | 组成 | 一个主页面和多个页面片段 | 多个主页面 |
  | 刷新方式 | 局部刷新 | 整页刷新 |
  | url模式 | 哈希模式 | 历史模式 |
  | SEO搜索引擎优化 | 难实现，可使用SSR方式改善 | 容易实现 |
  | 数据传递 | 容易 | 通过url、cookie、localStorage等传递 |
  | 页面切换 | 速度快，用户体验良好 | 切换加载资源，速度慢，用户体验差 |
  | 维护成本 | 相对容易 | 相对复杂 |
- 实现
	- 监听地址栏中`hash`变化驱动界面变化
	- 用`pushsate`记录浏览器的历史，驱动界面发送变化
-
- ## 首屏加载慢
- first contentful paint
	- 从用户输入网址，到首屏内容渲染完成的时间
- 原因
	- 网络延迟问题
	- 资源文件体积过大
	- 资源是否重复发送请求
	- 加载脚本时，渲染内容堵塞
- 解决方案
	- 减少入口文件体积
		- 路由懒加载
		- 在vue-router中采用动态加载路由的方式
			- ```
			  component: () => import('./components/ShowBlogs.vue')
			  ```
	- 静态资源本地缓存
	- UI框架按需加载
		- ```
		  import { Button, Input, Pagination, Table, TableColumn, MessageBox } from 'element-ui';
		  ```
	- 图片资源压缩
		- 对页面上使用到的`icon`，可以使用在线字体图标，或者雪碧图，将众多小图标合并到同一张图上，用以减轻`http`请求压力。
	- 组件重复打包
		- 在`webpack`的`config`文件中，修改`CommonsChunkPlugin`的配置
		- ```
		  minChunks: 3 //将使用三次以上的包抽离出来，放到公共依赖文件
		  ```
	- 开启Gzip压缩
	- 使用[[SSR]]
		- Server side 服务端渲染
-