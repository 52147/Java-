
# Jest 筆記本

jest 是js的測試框架，它提供了單元測試環境，他不用安裝其他的工具，就提供了很多其他功能，例如：判斷方法、分析測試覆蓋率、mock功能、錯誤提示訊息。   

jest 可以用來測試後端的node.js 與前端Vue, Angular, React。
## 使用jest 流程
1. npm 安裝
2. jest 配置
3. 執行jest

## jest 指令

## jest 測試方法
### 匹配器 toBe()
#### toBe()
```
test('two plus two is four', () => {
  expect(2 + 2).toBe(4);
});
```
expect() 返回了一個預期對象，為這個預期對象調用一個匹配器.toBe()。
#### toEqual()
toBe()使用Object.is來進行測試，如果需要測試object的value，可以用toEqual。
#### not
```
test('adding positive numbers is not zero', () => {
  for (let a = 1; a < 10; a++) {
    for (let b = 1; b < 10; b++) {
      expect(a + b).not.toBe(0);
    }
  }
});
```
可以使用not來進行與expect結果相反的測試。
#### toMatch
toMatch
#### toContain
toContain用來檢查，數組中是否包含特定的對象。
#### toThrow
toThrow 用來測試函數在調用時，是否拋出了錯誤。

## mock functions 模擬函數
