# maven 筆記本

Maven 是Java項目的管理和構建工具，主要功能有：
1. 標準化的項目結構
2. 標準化的構建流程（編譯、測試、打包、發布）
3. 標準化依賴管理機制

## maven 項目結構
```
a-maven-project
├── pom.xml
├── src
│   ├── main
│   │   ├── java
│   │   └── resources
│   └── test
│       ├── java
│       └── resources
└── target
```
- pom.xml 項目依賴文件
- src/main/java 存放java源碼
- src/main/resources 存放資源文件（sql）
- src/test/java 存放測試源碼
- src/test/resources 存放測試資源文件
- target 存放所有編譯、打包生成的文件

## pom.xml
pom.xml用來定義項目中的依賴。
- groupId : 為包名，通常為公司或組織名稱
- artifactId : java 類名，通常為項目名稱
- version
- dependency : 使用<dependency> 聲明一個依賴後，maven 會自動下載這個依賴包並放到項目的classpath中。依賴中包含groupId、artifactId、version。   

## 依賴管理
 如果我們聲明了需要依賴abc，maven會自動導入abc的jar包，再判斷abc需要xyz，又會自動導入xyz的jar包，所以最終我們的項目會有abc, xyz兩個jar 包。

## 中央倉庫
maven 維護了一個中央倉庫，所有第三方庫將自身的jar以及相關信息上傳到中央倉庫，maven可以從中央倉庫把所需依賴下載到本地。    
一個jar一但被下載過，就會自動被緩存在本地目錄，後需編譯不會再重複下載相同的jar，所以只有第一次編譯時，需要下載jar所以速度會比較慢，後續因有本地緩存，編譯速度變快。
- snapshot: 只有以 -SNAPSHOT 結尾的版本號，會被maven 視為開發版本，開發版本每次都會重複下載，SNAPSHOT版本只能用於內部私有的Maven repo，攻伐物的版本不允許出現SNAPSHOT。   
## Lifecycle 構建流程
 maven 定義了標準化的構建流程：clean, validate, complie, test, package, verify, install, site, deploy
- clean
- validate
- complie: maven 會把依賴直接放入classpath
- test
- package
- verify
- install
- site
- deploy
https://www.liaoxuefeng.com/wiki/1252599548343744/1309301178105890

https://www.liaoxuefeng.com/wiki/1252599548343744/1309301146648610
