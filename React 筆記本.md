# React 筆記本
## 腳本文件(scripts)
## ES6
import 模塊時要記得加 {C }     
https://www.runoob.com/w3cnote/es6-module.html

## JSX
JSX會自動消除html中的空格，所以如果想要在字間加入空格效果，可以用 &nbsp; 。
## 初始一個React App
使用 npx create-react-app <文件夾名> 創建一個初始的React App，其中包含了開發react所需要的工具。     
npx create-react-app 幫你做了以下工作:
1. 安裝了一些npm 包
2. 加入啟動react app所需要的腳本文件
3. 創建結構化的子文件夾，奠定app的基礎架構
4. 如果電腦上安裝了git，順便幫你把git倉庫建好。


創建好React app後，cd 到你的 React app文件夾下，輸入 npm start，由create-react-appt創建的腳本會用默認瀏覽器，啟動react app在localhost:3000。

### 初始 React App 的文件結構
```
moz-todo-react
├── README.md
├── node_modules
├── package.json
├── package-lock.json
├── .gitignore
├── public
│   ├── favicon.ico
│   ├── index.html
│   └── manifest.json
└── src
    ├── App.css
    ├── App.js
    ├── App.test.js
    ├── index.css
    ├── index.js
    ├── logo.svg
    └── serviceWorker.js
```    
src 是React 源碼存放地。   

public中包含了瀏覽器會讀取的文件，其中最重要的是index.html。      

index.js 為app的入口點(entry point)，為渲染App的地方，包含渲染位置(Dom 元素)與想要渲染內容，為使用根組件App component的地方。      

App.js 為 為react app中的根組件root component，為所有component中最頂層的組件。     

inde.js 定義了整個app的global style。      

package.json包含了npm為了建立該React app 的依賴的文件信息。      

[React app 中 index.js 與 app.js 間的關係](https://stackoverflow.com/questions/50493069/why-does-create-react-app-creates-both-app-js-and-index-js)   



## CSS 預處理器
https://juejin.cn/post/7005755782926958605
## less
less (Leaner Style Sheets )是css的擴展(extension)語言(預處理器)。    

https://less.bootcss.com/

## Font Awesome
Font Awesom 是 由css和less所組成，在html中加入圖標的工具套件，但在React 是使用 JSX 來寫html 物件，因JSX與一般的html 不相同，所以無法直解使用Font Awesome。    

### 下載 font awesome 依賴
```
npm i --save @fortawesome/fontawesome-svg-core
npm i --save @fortawesome/free-solid-svg-icons
npm i --save @fortawesome/react-fontawesome
```
### 導入 FontAwesomeIcon 和 圖標名 到 React     
1. 先導入 FontAwesomeIcon
2. 再導入不同類型圖標對應的包
不同類型圖標對應的包: 
如果是一般圖標，則需要導入@fortawesome/free-solid-svg-icons
如果是商標，則需要導入@fortawesome/free-brands-svg-icons，ex: fb, ig, Linkedin。
```
import React from "react";
import { FontAwesomeIcon } from '@fortawesome/react-fontawesome'
import { faAtom } from '@fortawesome/free-solid-svg-icons'

class App extends React.Component
{
    render()
    {
        return(
            <div className="icon">
                <FontAwesomeIcon icon={faAtom} />
            </div>
        )
    }
}

export default App;
```
https://ithelp.ithome.com.tw/articles/10231200?sc=rss.qu


## 在 React 中使用 Axios

https://www.freecodecamp.org/chinese/news/how-to-use-axios-with-react/


## SyntheticEvent
React事件處理event handler將被傳遞給SyntheticEvent，SyntheticEvent是瀏覽器原生事件Native Events的包裝器，他與瀏覽器原生事件有相同的接口。   
SyntheticEvent 具有跨瀏覽器和可重複性的功能。      

https://ithelp.ithome.com.tw/articles/10194857
## event.target.value
event.target 為觸發事件的元素   
event.target.value 為該元素的值(在input filed中輸入的值).   


https://stackoverflow.com/questions/67014481/what-is-event-target-value-in-react-exactly


## useEffect

當組件加載後（副效應），網頁隨之改變。   
1. 第一個參數： 一個函數，要改變的負效應      
2. 第二個參數：指定負效應函數的（第一個參數）的依賴項，只有依賴項改變，才會重新渲染頁面。如果沒有寫第二個參數，副效應只會在組件加載的時候，執行（重整頁面）。    

用途：
 - 1. 獲取數據
 - 2. 是件監聽或訂閱
 - 3. 改變DOM
 - 4. 輸出日誌

利用GET，從url中獲取資料，並利用useEffect()將資料返回到頁面：

```javascript
import React, {useState, useEffect} from "react";
import axios from "axios";

export const FetchData = () => {
    const[data, setData] = useState([]);
    
    useEffect(() => {
        const fetch = async () => {
            const res = await axios.get("https://hn.algolia.com/api/v1/search?query=redux");
            
            setData(res.data.hits); // 不能直接setData為res，因為res是一個object，map只能處理array(我們想利用array，將資料放在html list裡)
            console.log(res); // res是一個object
            console.log(res.data); // res 中的 data 是一個object
            console.log(res.data.hits); // res 中的 data 中的 hits是 array
        
        };
        fetch();
    
    },[]);
    
    return (
        <ul>
            {data.map((item) =>(
                <li key = {item.objectID}>
                    <a href = {item.url}>{item.title}</a>
                </li>
            ))}
        </ul>    
    );
}
```
https://github.com/52147/Java-Interview-Questions/blob/main/js%20%E7%AD%86%E8%A8%98%E6%9C%AC.md#map     

https://codesandbox.io/s/sleepy-mcclintock-l5is7z?file=/src/index.js.   

https://www.ruanyifeng.com/blog/2020/09/react-hooks-useeffect-tutorial.html

## Props
props 是將數據從父組件傳遞到子組建的方法。    
props 只能讀不能修改，代表子組件不能修改props，通常是另一個組件用useState更新state，然後父組件再傳遞state為props到子組件，傳到需要使用的子組件中，子組件使用props來更新內部或觸發操作。     
    
ex: 頁面更新依賴於上一個頁面的操作：    
上一個頁面點擊 申請intern -> 將 intern作為props傳到子組件 -> 子組件更新為intern的內容     
上一個頁面點擊 申請full-time -> 將 full-time作為props傳到子組件 -> 子組件更新為full-time的內容    
    
結論： 這樣只需同一個頁面，然後利用props來更新頁面為相對應的內容。        
    
https://github.com/52147/Diamond-Tofu-Career/blob/main/src/App.js   

## React Boostrap Pagination
1. 一個paginationClickHandler，讓使用者點擊Pagination 圖標時將資料更新到post，一次推１０比資料之後，post當作props傳到Post.jsx，以table的樣子呈現，再將pagination 對應該頁碼的圖標設定為active。
3. item[] 用來更新pagination 數字圖標，資料數量／１０，增加一個數字圖標，頁碼如果等於paginationClickHandler所展示的頁面，就將頁碼設定為active。
4. 用useEffect，當每次進入頁面時，設定paginationClickHandler 為１。


https://github.com/52147/CS673-Project-Fronted/blob/dev/src/parking-garage-automation/authority-management/Autho.jsx    



