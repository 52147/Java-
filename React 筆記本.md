# React 筆記本
## 腳本文件(scripts)
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
