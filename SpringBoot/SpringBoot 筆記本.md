# SpringBoot 筆記本

## SpringBoot 介紹
1. SpringBoot是一種框架，他繼承了Spring 框架原有的特性，並簡化了Spring 應用的搭建和開發過程。
2. SpringBoot集成大量框架，以解決依賴包間的衝突。
3. 嵌入Tomcat(embedded tomcat container), Jetty, Undertow
4. 自動配置Spring與第三方library
5. 提供隨時就緒的功能，例如：Metrics、程式的健康檢查、外部化配置。
6. 無任何需提前配置XML的需求。
7. SpringBoot是java開發REST Web最快的工具之一。    
## 控制反轉 Inversion of Control (IoC)
- 物件導向程式設計的原則，用來降低耦和性。
- 最常見的實現方式是依賴注入(Dependency Injection, DI)和依賴尋找(Dependency Lookup)。
- 採用依賴注入，Class A 只需要定義一個private B物件，不需要直接new來獲得這個物件，而是通過容器控制來將B在外部new出來並注入到Ａ中。具體的的物件獲得方式與物件被取得的狀態，由設定擋(XML)來指定。
- Ioc 可以理解為把流程控制從應用程式轉移到框架中。
## 依賴注入(dependency injection DI)
- 依賴注入是一種軟件設計模式，是一種實現控制反轉的一種技術，這種模式能讓物件接收他所依賴的其他物件，並確保任何想要使用服務的物件不需要知道如何建立這些服務。
- 依賴是指接收方class所需要的對象
- 注入是指將依賴傳遞給接收方的過程
- 注入之後接收方才可以調用該依賴
- 該設計的特色是分離接收方和依賴，以此提供鬆耦合性、代碼重用性。
- 降低new 的重要性：依賴注入將對象構建與對想使用分開，因此會降低new的重要性。
### 角色
- Services:
  - 服務端包含有功能的類
- Clients:
  - 客戶端使用服務的類
  - 任何對象都可以是服務端或客戶端，名稱與對象在注入中扮演的角色有關。可以既是客戶端(使用注入服務)，又是服務端(被注入到其他對象中)。 
- interfaces接口：
  - 客戶不應該知道他們的依賴如何實現，只知道他們的名字與API。
  - 通過忽略實現細節，客戶端不需要在他們的依賴發生變化時進行更改。
- injector 注入器：
  - 向客戶端引入服務
  - 負責建立複雜的對象圖，對象可能既是客戶端又是服務端。
### 實現方式
1. 構造函數注入：依賴是通過客戶端的構造函數提供。
2. Setter注入：客戶端接受依賴的public setter方法
3. 接口注入：依賴的接口提供了注入方法，該方法將依賴注入給客戶端。
4. 註解注入：在java中，在private variable前加 @Autowird，則可以直接如外部容器傳入對應物件。
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
1. Controller: 負責API接口。接收Http 請求，並使用Service Implementations來執行業務邏輯。
2. Service Implementations: 使用 Respository來訪問與操作CURD數據，並使用Mapper在DTOs和Entity間進行映射。
4. DTO: 被Mapper映射到Entity或其他DTO
5. Service(interface)
   - Service 位於Controller 和 Respository 之間，它提供了兩者間的抽象層interface。
   - 封裝了Respositoty的實現細節並向Controller提供了一個簡單的API。
   - 負責實現業務邏輯和數據訪問
6. entity: 代表數據庫中的數據，entity中的數據可以被Respository訪問和操作。
7. Respository(interface): 
   - 負責與資料庫進行操作和對實體entity進行操作的接口。
   - 繼承 JpaRepository 的抽象介面，讓使用者可以透過使用介面，直接與資料庫進行映射，而無需了解底層數據庫的實現。
   - JpaRepository API中包含，新增、修改、刪除、排序、分頁、搜尋id等功能。
8. model:


https://medium.com/learning-from-jhipster/20-controller-service-repository%E7%9A%84%E5%BB%BA%E7%AB%8B-1-jparepository-%E7%9A%84%E4%BD%BF%E7%94%A8-6606de7c9d41
## Controller 介紹
控制器類來處理 HTTP 請求和回應。
@RestController 和 @RequestMapping 
## Respository 介紹

使用 Spring Data JPA 定義interface來操作資料庫。定義interface時，需要繼承 JpaRepository interface並使用其interface中的一些查詢方法。


## Entity 介紹
實體類來表示存放在資料庫中的各種數據。

標註：   

- @Entity：數據模型層的宣告    
- @Table(name = "posts")：對應資料庫中資料表的名稱   
- @Column(name = "created_at")：對應資料庫中資料表的欄位的名稱    
- @Id：代表該資料表的Primary Key    
- @ManyToOne(fetch = FetchType.LAZY):
  - @ManyToOne代表在兩個實體間，建立多對一的關係。
  - fetch = FetchType.LAZY 為@ManyToOne的一個參數，代表從數據庫中獲取實體時，應如何加載實體，LAZY代表只有在需要時，才加載關聯實體，這樣可以通過減少不必要的數據庫查詢來提高性能。
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
