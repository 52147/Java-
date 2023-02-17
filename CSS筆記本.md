# CSS筆記本
## Boostrap
網格系統:    

透過利用 container 中的 flex來將子元素水平排列，width 來固定寬度，利用col 中的 min-width來設置media query，讓 col在網頁不的不同的寬度下做斷點。   
一行一共有12個col，可以分配不同的的col長度給不同的col。   
   
https://bootstrap5.hexschool.com/docs/5.0/layout/grid/   
https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox   
https://css-tricks.com/snippets/css/a-guide-to-flexbox/#flexbox-background



## Tailwind css
Tailwind css是css 框架，他定義了 css class內的atribute，只需要直接在html element 中加入 class就可以使用，這樣可以不用自己寫class內容然後放到css file。   
Tailwind的class可以在官方文黨內找到。   
|  Class  | Properties  |
|  ----  | ----  |
| py-4  | padding-top: 1rem; /* 16px */ <br> padding-bottom: 1rem; /* 16px */ |
| 单元格  | 单元格 |   


Background color:    
Tailwind 中定義的背景色class色很少沒有的顏色需要自己使用styles定義。    

[安裝tailwind](https://tailwindcss.com/docs/guides/create-react-app)   

https://tailwindcss.com/docs/background-color   

https://tailwindcss.com/docs/flex

## 把文字放到圖片上
 利用 position absolute將文字定位到圖片上，再調整文字的座標。
 ```css
.text-on-image {
  position: absolute;
  right: 50%;
  left: 50%;
  bottom: 15%;
}
```
https://stackoverflow.com/questions/64400365/how-to-add-text-on-image-in-reactjs
## flex box
![image](https://user-images.githubusercontent.com/79159894/217377949-132ea2a8-1131-4ce6-b5a0-1aac5a328f26.png)

flex box: 利用主軸(主軸起點、終點)，交錯軸(交錯起點、交錯終點)對齊來排版。   
如果要在所有子元素上排版，需要在父元素上加上display: flex，預設將所有子元素並排，還可以針對單一子元素做彈性調整。        

父元素須加上:  display: flex   

父元素可以透過以下操做對子元素做調整:   
  - justify-content   
  - align-items   
  - flex-direction   
 
flex box 和 display:inline-block 與display:block 不一樣的地方是，display:inline-block 與display:block是直接寫在子元素上。   

https://w3c.hexschool.com/flexbox/2186a786


### justify-content 
用主軸線作排版。 
justify-content 屬性:     
- justify-content: flex-start  預設值，對其主軸線最前端
- justify-content: flex-end 對其主軸線最終端
- justify-content: center 對其主軸線中央
- justify-content: space-around 平均分配寬度和間距
- justify-content: space-between 平均分配寬度，第一項和最後一項貼齊邊緣   

https://w3c.hexschool.com/flexbox/4a029043

### align-items
用交錯軸來排版。   
align-items 屬性:   
- align-items: flex-start 對齊交錯軸最前端
- align-items: flex-end 對齊交錯軸最末端
- align-items: center 對齊交錯軸中央
- align-items: stretch 預設值，將內容元素撐開至flexbox大小
- align-items: baseline 對其內容物的基線   

https://w3c.hexschool.com/flexbox/87d66dc4

### flex-direction
當我們將父元素加入 display: flex 時，子元素會依照交錯軸橫向排列成一行，如果我們想將內容物程直項排列，可以透過flex-direction來設定。   
flex-direction 屬性:      
- flex-direction: row 預設值，內容物依照主軸線橫向排列。
- flex-direction: row-reverse，內容物依照主軸線橫向排列，但子元素起點從主軸向終點開始排列。
- flex-direction: column，內容物依照交錯軸線直向排列
- flex-direction: column-reverse，內容物依照交錯軸線直向排列，但子元素起點從交錯軸線向終點開始排列
https://w3c.hexschool.com/flexbox/c1b62b9b
### 將box置中的方式
flex: 用一個容器包住物件，然後可以控制內部物件的排版方式，所以所有內容物都是彈性物件(flex)。
1. 利用 flex : 在父容器上套用flex，被父容器包住的物件(box)都可以彈性移動
```
.parent {
  display: flex;
  /* 水平置中 */
  justify-content: center;    
  /* 垂直置中 */
  align-items: center;        
}
```


## overflow

## position
position 是用來設定物件定位時所需要的參考對象，如果對物件添加了不同的position後，就能改變物件參考的對象，進而改變物件的位置。   
可以透過添加top，left，right、bottom 屬性來 移動不同 box的位置。    
或是添加 z-index來設定不同box的前後位置，讓box上下疊層。    

position 共有5種屬性:     
1. static 靜態定位: 
   - 將該物件定位特性取消。
3. relative 相對定位: 
   - 將設定的物件，讓其參考空間跟隨資料流位置。
4. fixed 固定定位: 
   - 將設定的物件，讓其參考空間設定為視窗。
   - 當物件設定了fixed之後，將會自己獨立一層，不會與其他物件有任何關聯。
   - fixed 和absolute 不一樣的地方是，fixed因為參考的定位空間是視窗，所以不管如何捲動視窗，fixed物件都不會換位置，但如果定位為absolute，則會被捲走，所以常見的固定在瀏覽器上方的nav bar 都是使用 fixed 定位的。
6. absolute 絕對定位: 
   - 將設定的物件，讓其參考空間跟隨離自身最近且具備定位設定的父層元素，如果沒有父層元素具備定位設定，該物件將採用視窗空間作為參考位置。
   - 當物件設定了absolute之後，將會自己獨立一層，不會與其他物件有任何關聯。
8. sticky 黏貼定位: 
   - 結合fixed 與 relative的特性，只fixed在該物件的父層空間。
   - sticky 物件會跟著卷軸移動，但僅限於在父層空間內移動，一但視窗超過父層空間的話，sticky 物件 就會被捲離。     
   
   
https://ithelp.ithome.com.tw/articles/10253500
