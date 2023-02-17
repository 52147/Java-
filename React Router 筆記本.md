# React Router 筆記本

## Link
Link 可以讓使用者透過點擊link到另一個頁面。它與<a href = "<path>"> 元素的作用相同。
使用:
<Link to = "不加/url的路徑"> 不需要以斜槓為開頭，相對於父路由進行解析，所以我們選擇的頁面會到父路由/指定的路徑。    
路徑中加上..代表到上一層的file。     
 https://reactrouter.com/en/main/components/link
## NavLink
NavLink 是一種特殊的<Link> ， 他可以知道link是否是active的狀態，代表被選擇，這樣我可以為已選擇的link添加不同的style。     
因為這個特性，NavLink 很常被使用在 Navigation Bar 上。   
  
https://reactrouter.com/en/main/components/nav-link   
  
### Bootstrap 
Navbar.Brand  幫Navigation Bar 最左邊的品牌加Style，用href指定路徑。
Nav.Link 幫Navigation Bar 最品牌的右邊的link加Style，ex: Home，About，Career。
