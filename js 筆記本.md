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
