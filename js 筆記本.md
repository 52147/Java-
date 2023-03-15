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

### filter

filter()：
- 為數組中的每個元素調用回調函數，並利用所有使回調函數返回true的元素創建一個新的數組。
- filter 不會改變原數組
箭頭函數： 
```javascript
filter((element) => {})
filter((element, index) => {})
filter((element, index, array) => {})
```
回調函數：
  - 用來測試數組中每個元素的函數。
  - 返回true代表該元素通過測試，保留該元素，返回false則不保留。
  - 回調函數接受以下３個參數：
    - 1. element: 數組中當前在處理的元素
    - 2. index: 數組中當前在處理的元素的索引
    - 3. array: 調用filter的數組，被遍歷的數組

利用filter在數組中搜尋包含特定字串的元素：
```javascript
const fruits = ["apple", "banana", "grapes", "mango", "orange"];

function filterItems(arr, query){
  return arr.filter((el)) => el.toLowerCase().inclues(query.toLowerCase());
}

console.log(filterItems(fruits, "ap")); // output: ["apple", "grapes"]
console.log(filterItems(fruits, "an")); // output: ["banana", "mango", "orange"]
```
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/filter#%E8%BF%87%E6%BB%A4_json_%E4%B8%AD%E7%9A%84%E6%97%A0%E6%95%88%E6%9D%A1%E7%9B%AE
