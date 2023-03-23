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

## 實例屬性 Instance Property
### event.target
觸發事件的對象的引用(DOM 元素)。   
https://developer.mozilla.org/zh-CN/docs/Web/API/Event/target
