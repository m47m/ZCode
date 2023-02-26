- 程序代码和数据结构的结合体
- 使用
	- export 用于规定模块对外接口
		- 使用as进行输出变量的重命名
	- import 用于输入其他模块提供的功能
		- 通过as关键字给输入变量起别名
		- 加载整个模块用*
		- 输入的变量只读，但对象的属性可以修改
	- 动态加载
		- 将import作为函数使用，它返回一个promise对象
- 场景
	- 组件化开发
-