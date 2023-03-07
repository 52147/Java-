# Axios 筆記本

## Axios
Axios 是基於promise 的http 請求庫，類似於ajax，用於向後台發起請求。   

應用於瀏覽器（客戶端）和node.js（服務端）。在瀏覽器（客戶端）使用XmlHttpRequests，在服務端使用node.js的http module。   

特性：
   - 從瀏覽器創建XMLHttpRequests
   - 從node.js 創建http請求
   - 支持promise api
   - 攔截請求和響應
   - 轉換請求和響應數據
   - 取消請求
   - 自動轉換request body 為
     - json
     - Multipart/FormData
     - URL encoded form

## 發送一個GET請求

向指定用戶的ID發送請求
1. 第一種寫法：
```javascript
const axios = require("axios");

axios.get("/user?ID=12345")
  .then(function(response){
    // 處理成功的狀況
    console.log(response); 
  })
  .catch(function(error){
    // 處理錯誤的狀況
    console.log(error); 
  })
  .finally(function(){
    // 總是會執行
  });
```
2. 第2種寫法
```javascript
axios.get("/user", {
    params: {
      ID: 12345
    }
  })
  .then(function(response){
    console.log(response);
  })
  .catch(function(error){
    console.log(error);
  })
  .finally(function(){
  
  })
  ```
3. 第 3 種寫法，用async/await


```javascript
async function getUser(){
  try{
    const response = await axios.get("/user?ID=12345");
    console.log(response);
  }catch(error){
    console.error(error);
  }

}
```
  
