- 轻量的HTTP客户端
- 特性
	- 从浏览器创建XMLHttpRequests
	- 从node.js创建http请求
	- 支持Promise API
	- 拦截请求和响应
	- 转换请求数据和响应数据
	- 取消请求
	- 自动转化json数据
	- 客户端支持防御XSRF
- axios.all
	- ```
	  function getUserAccount() {
	      return axios.get('/user/12345');
	  }
	  
	  function getUserPermissions() {
	      return axios.get('/user/12345/permissions');
	  }
	  
	  axios.all([getUserAccount(), getUserPermissions()])
	      .then(axios.spread(function (res1, res2) { 
	      // res1第一个请求的返回的内容，res2第二个请求返回的内容
	      // 两个请求都执行完成才会执行
	  }));
	  ```
- 为了提高我们的代码质量，我们应该在项目中二次封装一下 `axios` 再使用
	- 设置超时时间、设置请求头、根据项目环境判断使用哪个请求地址、错误处理等等操作
-
- ## 设置接口请求前缀
  collapsed:: true
	- 利用node环境变量，作为区分
		- ```
		  if(process.env.NODE_ENV === 'development'){
		  	axios.defaults.baseURL = 'http://dev.xxx.com'
		  }else if(process.env.NODE_ENV === 'producetion'){
		  	axios.defaults.baseURL = 'http://prod.xxx.com'
		  }
		  ```
	- 在vue.config.js中配置devServer实现代理转发，跨域
		- ```
		  devServer: {
		      proxy: {
		        '/proxyApi': {
		          target: 'http://dev.xxx.com',
		          changeOrigin: true,
		          pathRewrite: {
		            '/proxyApi': ''
		          }
		        }
		      }
		    }
		  ```
- ## 设置请求头和超时时间
  collapsed:: true
	- 将普适的请求头作为基础配置，当需要特殊请求头时，传入覆盖
		- ```
		  const service = axios.create({
		  	timeout:30000,
		      headers:{
		      	get:{
		          	'Content-Type': 'application/x-www-form-urlencoded;charset=utf-8'
		          },
		          post:{
		          	'Content-Type': 'application/json;charset=utf-8'
		          }
		      },
		  })
		  ```
- ## 封装请求方法
  collapsed:: true
	- ```
	  export function HttpGet({
	  	url,
	      params = {}
	  }){
	  	return new Promise((resolve,reject) =>{
	      	axios.get(url,{
	          	params
	          }).then((res) =>{
	          
	          }).catch((err) =>{
	          	reject(err)
	          })
	      })
	  }
	  ```
- ## 请求拦截器
  collapsed:: true
	- 在每个请求中加上token，方便管理维护
		- ```
		  axios.interceptors.request.use(
		  	config =>{
		      	//需要先判断是否存在token
		      	token && (config.headers.Auth = token)
		          return config
		      },
		      error =>{
		      	return Promise.error(error)
		      })
		  ```
- ## 响应拦截器
  collapsed:: true
	- 在接到响应后先做处理，（根据状态码判断登录状态、授权）
		- ```
		  axios.interceptors.response.use(
		  	reponse=>{
		      	if(reponse.status === 200){
		          	if(response.data.code === 511){
		              	//511表示未授权
		              }else if(response.data.code === 510){
		              	//510表示未登录
		              }else {
		              	return Promise.resolve(response)
		              }
		          }else{
		          	return Promise.reject(response)
		          }
		      },
		      error =>{
		      	//返回不同的处理方法
		      	if(error.response.status){
		          	
		              return Promise.reject(error.response)
		          }
		      })
		  ```
- ## 取消请求
	- 声明一个全局变量cancel
	- 在axios请求的时候，配置一个cancelToken属性，这个属性的值是一个CancelToken对象，对象的参数是一个回调函数
	- 取消的时候，只需要调用cancel函数即可
	- ```
	  //方式一
	  const CancelToken = axios.CancelToken();
	  const source = CancelToken.source();
	  
	  axios.get('xxx',{
	  	cancelToken: source.token
	  })
	  
	  source.cancel('主动取消请求')
	  
	  //方式二
	  const CancelToken = axios.CancelToken;
	  let cancel;
	  
	  axios.get('xxxx',{
	  	cancelToken: new CancelToken(function executor(c){
	      	cacel = c;
	      })
	  });
	  
	  cancel('主动取消请求')
	  ```
- ## 原理
-