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
子元素可以透過以操做做調整:   
  - justify-content   
  - align-items   
  - flex-direction   
 
flex box 和 display:inline-block 與display:block 不一樣的地方是，display:inline-block 與display:block是直接寫在子元素上。   

https://w3c.hexschool.com/flexbox/2186a786


### justify-content 

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
