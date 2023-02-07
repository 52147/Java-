# CSS筆記本

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
flex box: 利用主軸(主軸起點、終點)，橫軸(交錯起點、交錯終點)對齊來排版。   
如果要在所有子元素上排版，需要在父元素上加上display: flex，預設將所有子元素並排，還可以針對單一子元素做彈性調整。        

父元素須加上:  display: flex   

子元素可以透過以下操做做調整:   
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
用交錯軸(橫軸)來排版。   
align-items 屬性:   
- align-items: flex-start 對齊交錯軸最前端
- align-items: flex-end 對齊交錯軸最末端
- align-items: center 對齊交錯軸中央
- align-items: stretch 預設值，將內容元素撐開至flexbox大小
- align-items: baseline 對其內容物的基線   

https://w3c.hexschool.com/flexbox/87d66dc4
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
