- ## 使用promise封装[[ajax]]
- 如果遇到必须请求这个数据后才能请求另一个数据的情况，容易形成回调地狱
	- 不方便阅读，不易维护
- 封装ajax实现了链式调用
- ```
  function ajax(method,url,data){
  	var xhr = new XMLHttpRequest();
      return new Promise(function	(resolve,reject) => {
      	xhr.onreadystatechange = function(){
          	if(xhr.readyState !== 4)return;
              if(xhr.status == 200){
              	resolve(xhr.responseText);
              }else{
              	rejcet(xhr.statusText);
              }
          };
      	xhr.onerror = function(){
       		reject(Error("网络异常"));
     		}
          xhr.open(method,url);
          xhr.send(data);
      });
  }
  ```
-
- ---
- {{renderer :linkpreview,https://blog.csdn.net/Senora/article/details/122220983}}
- {{renderer :linkpreview,https://juejin.cn/post/7015842918799769637}}
-