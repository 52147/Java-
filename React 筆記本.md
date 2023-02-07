# React 筆記本

## less
less (Leaner Style Sheets )是css的擴展(extension)語言。    

https://less.bootcss.com/

## Font Awesome
Font Awesom 是 使用css和less在html中加入圖標的工具套件，但在React 是使用 JSX 來寫html 物件，因JSX與一般的html 不相同，所以無法直解使用Font Awesome。    

1. 下載 font awesome 依賴
```
npm i --save @fortawesome/fontawesome-svg-core
npm i --save @fortawesome/free-solid-svg-icons
npm i --save @fortawesome/react-fontawesome
```
2. 導入 FontAwesomeIcon 和 圖標名 到 React
圖標名: 如在官網中是<i class = "fas fa-atom"></i>，我們則需要導入faAtom這樣的圖標名到React。
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
