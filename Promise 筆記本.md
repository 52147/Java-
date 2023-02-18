# Promise 筆記本

生產者代碼(producing code): executor，做了一些工作，需要一段時間，才能產出結果。ex: 通過網路加載數據的代碼。   

消費者代碼(consuming code): 想要在生產者代碼完成工作的第一時間就能獲得其工作成果。    

Promise 是將生產者代碼 與 消費者代碼 連接在一起的 js對象。   


Promis對象的構造器(constructor):
```
let promise = new Promise(function(resolve, reject){
   // executor 生產者代碼
});
```
傳遞給 Promis對象 的函數為 executor。 當Promis對象 被創建，executor會自動執行。    
參數resolve 與reject是由js提供的回調。 我們需要完成的代碼僅在executor內部。    
當executor獲得了結果，應該調用以下回調:   
   - resolve(value): 如果任務成功，調用reolve 回調函數，並帶有結果value。
   - reject(error): 如果出現了error，調用reject 回調函數，error即為error對象。

Promis對象具有以下內部屬性:    
 - state: 
   - 最初是pending，然後在resolve 被 調用時，變為fulfilled，在reject被調用時變為 rejected。
   - executor最終將promise移至這兩種狀態之一。
 - result: 
   - 最初是undefined，然後在resolve 被 調用時，變為value，在reject被調用時變為 error。

![image](https://user-images.githubusercontent.com/79159894/219904099-550610a4-f231-4d33-894c-53939c57101b.png)


https://axios-http.com/zh/docs/intro    
https://zh.javascript.info/promise-basics
