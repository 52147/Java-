# Document Object Model(DOM)文黨對象模型 筆記本
## document
- 一個網頁頁面是一個document，這個document可以在瀏覽器窗口或作為HTML源碼顯示出來。
- DOM為對Document的另外一種表示，即可以利用js對Document進行儲存和修改。

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
為簡單起見，在API中的語法中，通常會使用element代指節點，使用nodeList來代指結點數組，使用attribute來代指結點屬性。
### document
### Node
document中的每個對象都是一個節點。在HTML中，對象可以是element節點、text節點、attribute節點。
###  element
是指由DOM API中成員返回類型為element的一個元素。ex: document.createElement() 會返回一個node的引用對像，代表返回了在DOM中創建的element。 element對象實現了DOM Element 接口以及Node接口。
### nodeList
nodeList是一個元素數組，類似於document.querySelectorAll()返回的類型。 nodeList中的元素通過索引以以下兩種方式訪問：
 - list.item(1)
 - list[1]
### Attr
通過createAtrribute()方法返回屬性，返回的是一個引用的對象。Attribute 在DOM中為node。
## DOM接口
- 1. window對象代表瀏覽器
- 2. document對象代表 root document
- 3. Element 繼承Node接口，element和node 接口提供了對單個元素上使用的多種方法和屬性。這些element可能也有特定的接口來處理這些element 的數據類型。
以下是一些常用的使用DOM所編寫的網頁和XML的API:
  - document.querySelector(selector)
  - document.querySelectorAll(name)
  - document.createElement(name)
  - parentNode.appendChild(node)
  - element.innerHTML
  - element.style.left
  - element.setAttribute()
  - element.getAttribute()
  - element.addEventListener()
  - window.content
  - Window.onload
  - window.scrollTo()
  
## 1. window 對象
- window接口包含DOM document。document屬性指向該window加載的DOM document。
- 可以使用document.defaultView 屬性來獲取window
- 全局變量window表示運行script的 window。
- window 接口是種全局可用的函數、namespaces、對象、構造函數的家。不一定與用戶的window直接相關。
- 在所有有標籤頁功能的瀏覽器中，每個標籤頁都有自己的window對象。  
## 實例屬性 Instance Property
window 接口繼承 EventTarget 接口的屬性。
- window.innerHeight : 只能讀，獲得瀏覽器內的內容的高度，包含水平滾動條。
- window.pageYOffset : 只能讀，scrollY的別名，它返回文黨當前沿著垂直軸滾動的像素數，值為0.0表示當前文黨的上邊緣與window內容的上邊緣對齊。  
## 2. document 對象  
  
## 3. element 對象
### event.target
觸發事件的對象的引用(DOM 元素)。   
https://developer.mozilla.org/zh-CN/docs/Web/API/Event/target
