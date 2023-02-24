# Redux 筆記本
Redux 是js 的一種狀態管理工作，他是一種前端的架構模式，他能套用任何程式語言，在框架中也很常見，ex:Wepay、Flutter。   
## Redux vs Flux
### Flux
Flux 是 fb用於構建客戶端網頁的架構，是一種應用程序中的數據流設計模式，Redux 是基於Flux的核心思想實現的一套解決方案。   
Flux 中的角色:    

- Dispacher: 調度器，接收Action，並接他們發送給Store。
- Action: 動作消息，包含動作類型與動作方式。
- Store: 數據中心，持有應用程序的數據，並響應Action。
- View: 視圖，可展示Store 數據，並實時響應Store的更新。

以網路通訊的角度可以將流程視為:    
Action 請求層 -> Dispatcher 傳輸層 -> Store 處理層 -> View 視圖層   
#### Flux 中數據以單一方向流動
1. 視圖產生動作消息，將動作傳遞給調度器
2. 調度器將動作消息發送給每一個數據中心
3. 數據中心再將數據傳遞給視圖
## 狀態管理

狀態管理: 管理UI 畫面與資料間的對應關係。    
狀態管理在不同框架會有不同的處理方式:
- JQuery: 資料與畫面分離
- Vue 和 Angular: 資料與畫面雙向綁定
- React: 只需要管理資料，藉由狀態渲染出畫面
https://juejin.cn/post/6844903806644256782    
https://hackmd.io/@Heidi-Liu/redux    
