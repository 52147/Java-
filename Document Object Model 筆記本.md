# Document Object Model(DOM)文黨對象模型 筆記本
## Document
- 一個網頁頁面是一個檔案，這個檔案可以在瀏覽器窗口或作為HTML源碼顯示出來。
- DOM則為對Document的另外一種表示，即可以利用js對Document進行儲存和修改。

## DOM
- DOM是HTML和XML檔案的程式接口。
- DOM 提供了對檔案的結構化表示。並定義了一種方式，可以從程序中對該結構進行訪問，進而改變檔案結構、樣式和內容。
- DOM 將檔案解析為一個節點和對象(包含屬性和方法的對象)組成的結構，使程式語言與網頁互動。
## DOM 與 js
- DOM 不是js的一部分，DOM 是用來創建web的 web API。
- js也可以不使用DOM。ex: node.js運行 js程序時，使用了另外一組不同於DOM API的API，因此DOM API不是node.js在執行時期的主要API。
- DOM被設計為獨立於程式語言，使的document結構可以從單一、一致的API獲得。雖然大多數網頁開發人員都通過js使用DOM，建構DOM可以被任何語言實現。ex: python
## 如何訪問DOM
當我們在創建一個腳本時，無論是無論是使用<script>或是使用腳本加載的方法，都可以使用doument或window API來操作來獲取document本身或document的子類(網頁上的各種元素)。
Dom 編程會像以下例子一樣簡單，ex: 使用window對象的alert()顯示一個警告信息。
```javascript
<body onload = "window.alert('welcome!');">
</body>
```
但通常不建議混合使用頁面結構(html)和DOM操作(js)，因此這裡的例子是，用一個函數創建一個h1 element，然後向該元素添加text，然後再將其添加到document tree：

```javascript
<html lang = "en">
  <head>
    <script>
      window.onload = () =>{
        const heading = document.createElement("h1");
        const headingText = document.createTextNode("123456789");
        heading.appendChild(headingText);
        document.body.appendChild(heading);
      };
    </script>
  </head>
  <body></body>
</html>  
```
## 數據類型
未簡單起見，在API中的語法中，通常會使用element代指節點，使用nodeList來代指結點數組，使用attribute來代指結點屬性。
|  表头   | 表头  |
|  ----  | ----  |
| document  | 单元格 |
| element  | 是指由DOM API中成員返回類型為element的一個元素。ex: document.createElement() 會返回一個node的引用對像，代表返回了在DOM中創建的element。 |  
## 實例屬性 Instance Property
### event.target
觸發事件的對象的引用(DOM 元素)。   
https://developer.mozilla.org/zh-CN/docs/Web/API/Event/target
