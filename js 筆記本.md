# JS 筆記本

## Array

### map

利用map()創建一個新的數組，新數組由原數組中的每個元素調用回調函數後的結果所組成。   
map()的參數只能放數組，不能放object，如果要放object，要把object放在array中。    

```javascript

const arr1 = [1, 4, 9, 16];

const map1 = arr1.mpa(x => x * 2);

console.log(map1); // output: [2, 8, 18, 32]
```
### map arrow function

```javascript
map((element) => {})
map((element, index) => {})
map((element, index, array) => {})
```

參數：
回調函數中包含了３個參數：
  - 1. current value: 正在處理的數組中的元素
  - 2. index： 正在處理的數組中的元素的索引
  - 3. array：map()調用的數組（原數組）



https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/map
