- ## 选择器
  collapsed:: true
	- 基本选择器
		- 子选择器
		- 相邻兄弟选择器
		- 通用兄弟选择器
		- 群组选择器
	- 属性选择器
		- `element [attribute]`为带有attribute属性的元素设置样式
		- `element [attribute = 'value']`为attribute='value'属性的元素设置样式
		- `element [attribute ~= 'value']` 选择attribute属性值包含 单词value的元素 并设置样式
		- `element [attribute *= 'value']`选择attribute属性值包含value的元素设置样式
		- `element [attribute ^= 'value']`选择attribute属性值是以value开头的元素
		- `element [attribute $= 'value']`选择attribute属性值是以value结尾的元素
		- ```
		  div[class^="test"]{
		      background:#ff0;
		  }
		  ```
	- 伪类选择器：只有在用户与网站交互的时候才能够体现出来
		- 锚点伪类
			- `:link`
			- `:visited`
		- 用户行为伪类
			- `:hover`
			- `:active`
			- `:focus`
		- 目标伪类
			- `:target`
				- 当我们点击锚点链接时，对应id的元素会显示在视口
				- ```
				  div {
				          height: 50px;
				          width: 100%;
				        }
				        div:target {
				          border: 5px solid red;
				          background-color: wheat;
				        }
				  ```
		- checked状态伪类
			- 仅适用于单选按钮和复选框
	- **nth选择器**
		- `element:first-child/last-child`
			- element为子元素
			- ```
			  .father p:nth-of-type(p){
			  	
			  }
			  ```
		- `nth-child(n)`
			- 括号里可以传递odd和even两个关键词
			- 先确定位置，在确定元素类型
		- `nth-last-child(n)`
		- `nth-of-type(n)`
			- 先确定元素类型，再确定位置（第二个p元素）
		- `nth-last-of-type(n)`
		- `first-of-type`
		- `last-of-type`
		- `only-child`
			- 匹配完全没有同胞的元素
		- `only-of-type`
			- 匹配子元素中唯一类型的元素
		- `:empty`：匹配没有子元素的每个元素（包括文本节点）
	- 否定选择器
		- 匹配非 元素或者选择器 的每一个元素
			- `ul:not(span){}`
	- 伪元素
		- `element::first-line` 只能用于块级元素
		- `element::first-letter`
		- `element::before` 在元素的内容前面插入新内容，常与content配合使用
			- ```
			  .box1::before{
			      content:"大家好"
			  }
			  .box1::after{
			      content:"宁在春"
			  }
			  
			  要给这些伪元素设置宽度、高度什么，一定得写上display:inline-block属性
			  ```
		- `element::after`
		- `element::selection`
- CSS边框和圆角
	- border-radius 圆角
	- box-shadow 盒阴影
		- 水平方向的偏移量、垂直方向的偏移量、模糊程度、扩展程度、颜色、是由具有内阴影（inset）
- CSS背景与渐变
	- background-image
	- background-clip指定背景的绘制区域
	- background-origin设置背景图像的原始起始位置
		- border-box
		- padding-box
		- content-box
		- background-position
	- background-repeat设置是否以及如何重复背景图像
		- repeat
		- repeat-x
		- repeat-y
		- no-repeat
		- inherit
	- background-size
		- number：宽度 高度
		- 百分比
		- cover：等比缩放
		- contain：紧贴
	- background
- CSS渐变
	- 线性渐变
		- background:linear-gradient(方向，开始颜色，结束颜色)
			- to right,red,blue
			- to right bottom,red,blue
			- 角度：0deg从下到上，90deg从左到右
		- 颜色节点
			- backgroud:linear-gradient(red 10%,blue 20%,green 30%,yellow 40%)
			- backgroud:linear-gradient(red , blue 30%)从0到30%为红色到蓝色的渐变
	- 径向渐变
		- 从起点到终点，颜色由内而外进行圆形渐变
		- background:radial-gradient(形状尺寸，开始颜色，结束颜色)
		- 形状分类
			- circle
			- ellipse
		- 尺寸大小
			- `background: radial-gradient (closest-side  circle,red,blue)`
			- `background: radial-gradient (farthest-side  circle,red,blue)`
			- `background: radial-gradient (closest-corner  circle,red,blue)`
			- `background: radial-gradient (farthest-corner circle  circle,red,blue)`
		- 颜色节点
			- `background: radial-gradient(circle,red 50%,blue 70%)`
		- 重复渐变
			- `background: repeating-radial-gradient(red 0%,blue 10%,red 20%)`
- CSS过渡
	- 允许css的属性，在一定区间内平滑的过渡，在鼠标点击、鼠标滑过或对元素任何改变中触发，并圆滑地以动画形式改变css的属性值
	- transition-property设置对象中参与过渡的属性
	- transition-duration设置对象过渡的持续时间
	- transition-timing-function设置对象中过渡的动画类型，即规定过渡效果 的速度曲线
	- transition-delay设置对象延迟的过渡时间
	- transition复合属性
- CSS变换
	- 让元素在一个坐标系统中变形，可以移动、旋转、缩放元素
	- 2d变换
		- rotate()旋转
		- translate()平移
			- 语法：`transform : translate(X,Y)`
		- scale()缩放 设置元素的缩放程度
			- 语法：`transform : scale(X,Y)`
		- skew()扭曲、倾斜
			- 语法：`transform : skew()`单位deg
		- 变换基点（旋转基点，比如基于右下基点`tragsform-origin : right bottom`）
			- transform-origin
	- 3d变换
- CSS动画
	- @keyframes
		- @keyframes-selector
	- animation属性
		- animation-name属性
		- animation-duration属性
		- animation-timing-function属性
-