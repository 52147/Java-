# SpringBoot 筆記本
## SpringBoot 介紹
1. SpringBoot是一種框架，他繼承了Spring 框架原有的特性，並簡化了Spring 應用的搭建和開發過程。
2. SpringBoot集成大量框架，以解決依賴包間的衝突。
3. 嵌入Tomcat(embedded tomcat container), Jetty, Undertow
4. 自動配置Spring與第三方library
5. 提供隨時就緒的功能，例如：Metrics、程式的健康檢查、外部化配置。
6. 無任何需提前配置XML的需求。
7. SpringBoot是java開發REST Web最快的工具之一。    

https://ithelp.ithome.com.tw/articles/10213097

## SpringBoot vs Spring MVC vs Spring 關係
SpringBoot包含了 Spring MVC，同時簡化了配置。   

SpringBoot 和 Spring MVC都是一種框架。    

Spring 是一種框架，它包含了一系列IoC容器的設計、依賴注入(DI)、整合AOP功能。    

## SpringBoot 中的 Spring MVC
SpringBoot 中的 Spring MVC和Spring MVC中的差別是不用做XML配置。

MVC為一種軟體架構模式，把軟體設計分為3個部分：
1. Model : 負責進行資料庫管理
2. View：負責呈現數據在客戶端的瀏覽器上
4. Controller：負責處理用戶請求，放API接口與控制器邏輯

## Spring中的檔案架構
1. Controller: 負責API接口
2. Service
3. entity
4. Respository: 負責與資料庫進行操作
5. model:

https://medium.com/learning-from-jhipster/20-controller-service-repository%E7%9A%84%E5%BB%BA%E7%AB%8B-1-jparepository-%E7%9A%84%E4%BD%BF%E7%94%A8-6606de7c9d41
## Controller 介紹
控制器類來處理 HTTP 請求和回應。
@RestController 和 @RequestMapping 
## Respository 介紹
繼承 JpaRepository 的抽象介面，讓我們可以透過使用介面，直接與資料庫進行映射。
JpaRepository API中包含，新增、修改、刪除、排序、分頁、搜尋id等功能。

https://medium.com/learning-from-jhipster/20-controller-service-repository%E7%9A%84%E5%BB%BA%E7%AB%8B-1-jparepository-%E7%9A%84%E4%BD%BF%E7%94%A8-6606de7c9d41

## Entity 介紹
實體類來表示存放在資料庫中的各種數據。

標註：   

- @Entity：數據模型層的宣告    
- @Table(name = "posts")：對應資料庫中資料表的名稱   
- @Column(name = "created_at")：對應資料庫中資料表的欄位的名稱    
- @Id：代表該資料表的Primary Key    
- @ManyToOne(fetch = FetchType.LAZY):@ManyToOne代表在兩個實體間，建立多對一的關係。fetch = FetchType.LAZY 為@ManyToOne的一個參數，代表從數據庫中獲取實體時，應如何加載實體，LAZY代表只有在需要時，才加載關聯實體，這樣可以通過減少不必要的數據庫查詢來提高性能。
- @GeneratedValue(strategy = GenerationType.IDENTITY)： 
  - 在JPA中用於實體生成主見值的方式。 
  - GenerationType.IDENTITY代表數據庫負責在表中插入新列時，生成主鍵值。
  - 此方式常用在主鍵自增(support auto-incremented columns)的數據庫。
  - @id必須為數值類型，例如：Long, Integer


- @JoinColumn(name = "user_id"):
  - 用於指定表中外鍵的列名 
- @JsonIgnoreProperties({"hibernateLazyInitializer"})
  - 用於指示在Json序列化和反序列化的過程，應乎略特定屬性或字段。
  - hibernateLazyInitializer代表忽略 在Hibernate中，使用延遲加載lazy loading所自動生成的hibernateLazyInitializer屬性，忽略它可以避免序列化Hibernate proxy objects所發生的問題。
