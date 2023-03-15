# Redux 筆記本
- Redux 是js 的一種狀態state管理工具，他是一種前端的架構模式和library，他能套用任何程式語言，在框架中也很常見，ex:Wepay、Flutter。   
- Redux 使用稱為動作action 的事件還管理和更新state。他集中儲存state，來確保state是以可預測的方式更新，可預測代表我們可以知道應用程序的狀態何時、為何、如何更新，以及更新時的應用程序的邏輯將如何運行，有助於確保應用程序按預期工作。
Redux適合使用在以下情況：
- 應用程序有大量的狀態
- 狀態會頻繁的更新
- 更新狀態的邏輯非常複雜
- 應用程序有中型或大型的codebase，並且由許多人共同開發

## Redux工具：    
Redux是一個js庫，他通常與以下幾個包一起使用：      
1. react-redux     
Redux可以與任何UI 框架一起使用，React是最常使用的框架。      
使用react-redux的官方包，可以讓react組件通過讀取state與分派action來更新redux store。   
```
npm install react-redux
```
2. reduxjs/toolkit     
redux toolkit 是redux 官方推薦的寫redux 邏輯的方法。它包含構建redux的包和函數。
```
npm install @reduxjs/toolkit
```
3. Redux DevTools Extensions        
Redux DevTools Extensions可以顯示redux store中狀態改變的歷史紀錄。

### redux toolkit
redux toolkit包含以下幾種APIs:
1. configureStore():
   - 包裝 createStore 以提供簡化的配置與默認值。
   - 可以自動組合slice reducer，並添加 redux中間件，包含默認的 redux-thunk。
2. createSlice():
   - 接受一個reducer函數對象，一個slice名稱與一個初始state 值，並且可以為action creator 和action types自動生成對應的reducer 和state。
3. createAsyncThunk():
   - 接受一個表示action type的string，和一個返回promise的函數，並且基於返回的promise狀態，生成一個thunk分派action type(pending/ fulifilled/ rejected)。

https://redux-toolkit.js.org/introduction/getting-started#whats-included
### react redux
react redux 包含了以下幾種APIs:
1. Provider
   - Provider組件可以使redux store在所有app中的組件中被使用。
2. Hooks
   - react rudux提供了useSelector()和 useDispatch() 來讓 react 組件與redux store做互動。
   - useSelector()：
     -  從store讀取state的值，並且用訂閱來更新。
   - useDispatch():
     - 返回store的分派方法，讓我們分派action。  

```javascript
import React from 'react'
import { useSelector, useDispatch } from 'react-redux'
import {
  decrement,
  increment,
  incrementByAmount,
  incrementAsync,
  selectCount,
} from './counterSlice'
import styles from './Counter.module.css'

export function Counter() {
  const count = useSelector(selectCount)
  const dispatch = useDispatch()

  return (
    <div>
      <div className={styles.row}>
        <button
          className={styles.button}
          aria-label="Increment value"
          onClick={() => dispatch(increment())}
        >
          +
        </button>
        <span className={styles.value}>{count}</span>
        <button
          className={styles.button}
          aria-label="Decrement value"
          onClick={() => dispatch(decrement())}
        >
          -
        </button>
      </div>
      {/* omit additional rendering output here */}
    </div>
  )
}
```
## Redux 概念

1. state： 驅動應用程序的來源
2. 視圖：基於當前state的聲明性描述UI
3. action: 使用者輸入所觸發的事件，會觸發state的更新。

問題：   
如果是單一數據流的程序ex: 點擊按鈕，觸發事件，視圖根據狀態更新。如果是多個組件需要共享同一個state時，有時可以透過將狀態放到父組件來進行，但不是所有狀況都可以這樣進行操作。   
   
解決方式：    
從組件間提取共享狀態，並將其放在組件樹外的位置，這樣我們的組件樹就成為一個大的視圖，任何組件都可以訪問狀態和觸發動作，無論組件在組件樹中的哪個位置。    
   
通過保持狀態和視圖間的獨立性，為代碼提供了結構性和可維護性。   
   
Redux的概念就是，用一個單一的位置，來包含全局狀態，以及在更新狀態時，遵循特定的規則，使代碼變得可以預測。     
https://react-redux.js.org/introduction/getting-started#api-overview    

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

