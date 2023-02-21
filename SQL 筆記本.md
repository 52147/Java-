# SQL 筆記本



## 問題 1
直接複製從網頁複製貼上sql query 到 phpmyadmin，出現 Error in processing request。   

原因:   
因為window和 Linux上的換行字符new line character不一樣導致。
不同OS間換行字符的差異:
- Windows 使用兩個字符的 CR LF 序列
- Unix 只使用 LF 而
- 舊的 MacOS（pre-OSX MacIntosh）使用 CR
解決方式:
將sql query貼到Notepad++後再貼到phpmyadmin就可以解決。
參考資料:
https://stackoverflow.com/questions/1552749/difference-between-cr-lf-lf-and-cr-line-break-types
