- ```
  function getObjectAllKeys(obj,res = []){
  	for(const key in obj){
      	res.push(key);
          
          if(type of obj[key] === 'object'){
          	getObjectAllKeys(obj[key],res)
          }
          
      }
      
      return res;
  }
  ```