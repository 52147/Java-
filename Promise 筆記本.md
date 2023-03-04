# Promise 筆記本



生產者代碼(producing code): executor，做了一些工作，需要一段時間，才能產出結果。ex: 通過網路加載數據的代碼。   

消費者代碼(consuming code): 想要在生產者代碼完成工作的第一時間就能獲得其工作成果。    

Promise 是將生產者代碼 與 消費者代碼 連接在一起的 js對象。   
## 同步 vs 異步
異步：指在方便時，才接收和處理信息，而不是立刻這麼做。 ex: Ajax就是請求HTTP 少量數據的非同步機制，代表結果會在響應完成時發回，而不是立刻發送。
## 回調函數
js 主機環境提供了許多函數，這些函數允許我們執行異步行為(action)，代表讓函式成為另一個函式的參數，因此可以讓函數控制參數函式的使用。ex: setTimeout(), 加載腳本loadScript(src)或模塊

### loadScript(src)
loadScript(src) 該函數給src 加載腳本，此函數將帶有給定src，動態創建標籤 <script src = ""> 插入到文黨中。瀏覽器將自動加載它，並在加載完成後執行它。
```
function loadScript(src){
   let script = document.createElement("script");
   script.src = src;
   documetn.head.append(script);
}
// 使用 loadScript() 加載在此路徑的腳本
loadScript("/my/script.js");
```
我們可以添加一個回調函數作為loadScript的第2個參數，該函數在腳本加載完後執行
```
function loadScript(src, callback){
   let script = document.createElement("script");
   script.src = src;
   script.onload = () => callback(script); // onload 事件，會在腳本加載和執行完後執行一個函數
   documetn.head.append(script);
}
// 使用 loadScript() 加載在此路徑的腳本
loadScript("/my/script.js");
```   
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
```
let promise = new Promise(function(resolve, reject){
   // 當promise 構建完成時，自動執行setTimeout()
   
   // 1s後執行resolve()回調函數，並帶有結果 “done”
   setTimeout(() => resolve("done"), 1000);
});
```
1. executor 被自動立即調用
2. excutor 接受2個參數，resolve 和 reject，這2個回調函數由js引擎預先定義好，因此我們不需要創建他們，只需要在excutor執行完成後調用他們。
3. 經過1s之後，excutor 調用 reolve("done")，這將改變promise對象的狀態從初始奘態pending改為 fulfilled，結果從原本undefined改為done。
4. executor 只能調用1 個resolve或reject，如果有其他的resolce或 reject都會被忽略。
![image](https://user-images.githubusercontent.com/79159894/222852864-edc436a6-d53a-475d-8378-b10d22798b2e.png)
### 改變狀態為fulfilled

## 用.then/.catch/.finally 來訪問 state 和 result
用消費者函數.then/.catch/.finally 來返回結果給消費者。

### then
```
promise.then(
   function(result){ // 成功狀態reolve()執行完後執行}
   function(error){ // 錯誤狀態reject()的執行完後執行}
)
```   
## resolve 狀態
```   
let promise = new Promise(function(resolve, rejct){
   setTimeout(() => resolve("done"),1000);
});
promise.then(
   result => alert(result), // resolve() 運行此函數
   error => alert(error)
)
```   
## reject 狀態
```   
let promise = new Promise(function(resolve, reject){
   setTimeout(() => reject(new Error("Whoops")), 1000);
});

promise.then(
   result => alert(result), // reject 運行此函數
   errot => alert(error)
);
```
也可以在.then() 中只提供一個函數
```
let promise = new Promise(function(resolve, reject){
    setTimeout(() => resolve("done"),1000);
});

promise.then(alert); // resolve 後執行 
```      
https://axios-http.com/zh/docs/intro    
https://zh.javascript.info/promise-basics/

## async/await
async/await 是以一種更容易理解的方式使用promise。
## async function
在函數前面加關鍵字async，表示這個函數返回一個reolved promise。
```   
async function f(){
   return 1;
}
f().then(alert); // 1
```   
等於：
```
async function f(){
   return Promise.resolve(1);   
}
f().then(alert); // 1
```
## await
await 只在async函數中運作。     
關鍵字 await 讓js 引擎等待promise完成並返回結果。   
await 可以暫停函數的執行，直到promise狀態變為settled，然後可以利用promise執行後的結果繼續做處理。這個行為不會耗費任何CPU，因為js引擎可以同時處理其他任務，ex:執行其他腳本，處理事件。   
他是比promise.then() 更簡單易讀的寫法來獲取promise結果。   
ex: 1 s 後reolved 的 promise。   
```
async function f() {

 let promise = new Promise((resolve, reject) => {
 setTimeout(() => resolve("done!"), 1000)
});

let result = await promise; //等待直到promise resolve
alert(result); // "done!"
}

f();
```
   
