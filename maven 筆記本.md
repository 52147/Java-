# maven 筆記本

Maven 是為Java項目的管理和構建工具，主要功能有：
1. 標準化的項目結構
2. 標準化的構建流程（編譯、測試、打包、發布）
3. 標準化依賴管理機制

## maven 項目結構
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
  
  
  https://www.liaoxuefeng.com/wiki/1252599548343744/1309301146648610
