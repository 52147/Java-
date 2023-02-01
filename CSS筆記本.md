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

## 將box置中的方式
flex: 用一個容器包住物件，然後可以控制內部物件的排版方式，所以所有內容物都是彈性物件(flex)。
1. 利用 flex : 在父容器上套用flex，被父容器包住的物件box都可以彈性移動
```
.parent {
  display: flex;
  /* 水平置中 */
  justify-content: center;    
  /* 垂直置中 */
  align-items: center;        
}
```
