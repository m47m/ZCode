- 在函数内，使用for循环，进行每两个数据的函数处理
- ```
  
  //此时的f简化为add函数，做两个值的相加
  
  Array.prototype.reduce = Function (f,value){
  	const arr = this;//此处的this为调用reduce的数组
      let total = value || arr[0];
      
      for(let i = value ? 0:1;i<arr.length;i++){
      	total = f(arr[i],value)
      }
      
      return total;
  }
  ```
-