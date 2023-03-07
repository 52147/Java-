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
  
## 發送一個POST請求
http header包含 Content-Type，代表資料發送的格式。     
 - "Content-Type" : "application/json" 代表資料格式為json    
 - 'Content-Type': "multipart/form-data" html 的 form，加上ectype屬性，代表可以把複數個資料格式一起傳送，用boundary將不同資料屬性分割開來 ex: name=karen&age=25   
 - "Content-Type" : "application/x-www-form-urlencoded" html 的 form，沒有設置ectype屬性下，會以application/x-www-form-urlencoded 的方式提交數據，也就是在url上加上key1 = val1   


https://github.com/52147/Java-Interview-Questions/blob/main/%E5%BE%8C%E7%AB%AF%E9%9D%A2%E8%A9%A6%E5%95%8F%E9%A1%8C.md#3-%E7%99%BC%E9%80%81http%E8%AB%8B%E6%B1%82


## 發送一個POST請求 

### JSON
1. 發送一個POST請求來創建新的user
```javascript
axios.post( "/user", {
   firstName: "Fred",
   lastName: "Flintstone"
   })
   .then(function(response){
   console.log(response);
   }).catch(function(error){
   console.log(error);
   });
```
2. 發送多個併發POST請求
```javascript
function getUserAccount(){
   return axios.get("/user/12345");
}

function getUserPermissions(){
   return axios.get("/user/12345/permissions");
}

const [acct, perm] = await Promise.add([getUserAccount(), getUserPermissions()]);

```
另一種寫法：
```
Promise.all([getUserAccount(), getUserPermission()])
   .then(function([acct, perm])){
      // ...
   }
```
以json 的格式Post 一個 html form :
```javascript
const {data} = await axios.post("/user", document.querySelector("#my-form"), {
   headers: {
      "Content-Type" : "application/json"
   }
})
```
