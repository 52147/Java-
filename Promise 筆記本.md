# Promise 筆記本

生產者代碼(producing code): executor，做了一些工作，需要一段時間，才能產出結果。ex: 通過網路加載數據的代碼。   

消費者代碼(consuming code): 想要在生產者代碼完成工作的第一時間就能獲得其工作成果。    

Promise 是將生產者代碼 與 消費者代碼 連接在一起的 js對象。   


## Promis對象的構造器(constructor)
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

## Promis對象具有以下內部屬性
 - state: 
   - 1. 最初是pending，
   - 2. 然後在resolve 被 調用時，變為fulfilled，
   - 3. 在reject被調用時變為 rejected。
   - executor最終將promise移至這兩種狀態之一。
 - result: 
   - 最初是undefined，然後在resolve 被 調用時，變為value，在reject被調用時變為 error。

![image](https://user-images.githubusercontent.com/79159894/219904099-550610a4-f231-4d33-894c-53939c57101b.png)

## executor 如何改變Promise 狀態
### 改變狀態為fulfilled
例子：
Promise 構造器中有 setTimeOut() 作為生產者代碼

let promise = new Promise(function(resolve, reject){
   // 當promise 構建完成時，自動執行setTimeout()
   
   // 1s後執行resolve()回調函數，並帶有結果 “done”
   setTimeout(() => resolve("done"), 1000);
});
1. executor 被自動立即調用
2. excutor 接受2個參數，resolve 和 reject，這2個回調函數由js引擎預先定義好，因此我們不需要創建他們，只需要在excutor執行完成後調用他們。
3. 經過1s之後，excutor 調用 reolve("done")，這將改變promise對象的狀態從初始奘態pending改為 fulfilled，結果從原本undefined改為done。
4. executor 只能調用1 個resolve或reject，如果有其他的resolce或 reject都會被忽略。
![image](https://user-images.githubusercontent.com/79159894/222852864-edc436a6-d53a-475d-8378-b10d22798b2e.png)
### 改變狀態為fulfilled

https://axios-http.com/zh/docs/intro    
https://zh.javascript.info/promise-basics
