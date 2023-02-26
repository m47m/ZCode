- 核心作用：局部刷新
-
- 在不重新加载页面的情况下，发送请求给服务器
- 接收并使用从服务器发来的数据
- ```
  // 1.创建 XMLHttpRequest 对象
  var xhr = new XMLHttpRequest();
  // 2.设置状态监听函数
  xhr.onreadystatechange = function () {// 状态发生变化时，触发回调函数
      if (xhr.readyState !== 4) return;
      if (xhr.status === 200) {
          // 成功：从服务器获取数据，通过responseText拿到响应的文本
          console.log(xhr.responseText)
          // do what
      } else {
          // 失败，根据响应码判断失败原因
          new Error(xhr.statusText)
      }
  };
  // 3.规定请求的类型、URL 以及是否异步处理请求
  xhr.open("GET", url, true);
  // 4.将请求发送到服务器
  xhr.send();
  ```
- **open(*method*,*url*,*async*)** 方法 规定 **`请求的类型`**、**`URL`** 以及 **`是否异步处理请求`**
- **send(*string*)** 方法 将请求发送到服务器
- 如果需要像获取 HTML 表单那样 POST 数据，请使用 `setRequestHeader()` 来添加 HTTP 头
-