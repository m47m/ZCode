- ## ((63b2b5b6-7baf-469b-8940-ba9e1feeb5c8))
- ((63b2b632-3923-406f-bc11-55d8bef81d2f))
	- async 立即下载
		- 只适用于外部脚本
		- 不能保证标记async的脚本按他们出现的次序执行
		- ((63b2baa2-90fc-4cc9-a5ce-fd06e5e8b8a8))
	- charset 代码字符集
	- crossorigin CORS设置跨源资源共享
		- crossorigin = "anonymous"配置文件请求不必设置凭据标志
		- crossorigin = "use-credentials"设置凭据标志
	- defer 延迟
		- `<script defer src="example2.js"></script>`立即下载，但延迟执行
			- 此时可包含在<head>中
			- defer只对外部脚本文件
	- integrity 确保内容分发网络Content Delivery Network 不会提供恶意内容
	- language
	- src 要执行的代码的外部文件
	- type 代替language
		- text/javascript application/javascript
		- ((63b2b807-b7a9-4cee-9ae8-21fa39d50bf7))
- 通过<script>
	- ((63b2b848-1988-4c32-898c-f89dcc2d7705))
		- ((63b2b882-4075-4556-8e7e-c0b775e7fce4))
	- ((63b2b852-0d55-451f-90c1-664c6c8d3b89))
		- `<script src = ""example.js"/>`
	- ((63b2b945-51a9-4d19-83ea-b59de7a0419e))
- 动态加载脚本
	- ```
	  let script = document.createElement('script');
	  script.src = 'gibberish.js';
	  document.head.appendChild(script);
	  //默认以异步加载，相当于添加了async
	  ```
	- ```
	  //明确设置问同步加载
	  let script = document.createElement('script');
	  script.src = 'gibberish.js';
	  script.async = false;
	  document.head.appendChild(script);
	  
	  //可在文档头部显式声明
	  <link rel = 'preload' href = "gibberish.js">
	  ```
- 可扩展超文本标记语言XHTML
	- ((63b2bce3-96e7-428a-88d8-e466c155377e))
- ## ((63b2be3b-1da2-4deb-9e8d-caa480fc8785))
- 推荐使用外部文件的理由
	- 可维护性
	- 缓存
		- 两个页面用到同一个文件，则只需下载一次
	- 适应未来
- ## ((63b2beaf-d402-4c5d-af7d-b81224b2baa6))
- 混杂模式 quirks mode
- 标准模式 standards mode
- 准标准模式 almost standards mode
	- 通过过度性文档类型Transitional 和框架集文档类型 Frameset
- ## ((63b2bfb2-2199-4581-89bd-f3576abbcc2e))
- 处理页面降级方案（并不支持JavaScript）
- 可以包含任何可以出现在<body>中的HTML元素，<script>除外
- 出现情况
	- 浏览器不支持脚本
	- 浏览器对脚本的支持被关闭
- ## ((63b2c01d-5344-40be-8f93-efdd431c2850))
-