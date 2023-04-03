# Spring Data JPA


## ORM(Object Relative Database Mapping)
ORM代表對象關係映射，
ORM 利用 Model 數據層與數據訪問層做關聯，代表直接利用數據層的名稱與資料表名稱互相對應關聯起來。
在利用hibernate與JPA對資料庫做CRUD。
## Hibernate
Hibernate是一種ORM框架，
## ORM、Hibernate、JPA 間的關係
Hibernate 是JPA的實現，是一種框架。
Spring Data JPA 是 JPA的抽象層，底層依賴Hibernate。
## JPA(Java Persistance API)
JPA是java 持久化API，是基於ORM規範，及一種對象/關聯映射工具，由一系列的接口與抽象類所組成，用來管理java應用中的關係數據。

JPA 特性：
1. 標準化：
   - JPA是Java EE 標準之一，任何符合JPA標準的框架都遵循相同的架構，提供相同的API。
   - 這保證了基於JPA開發的企業，能夠經過少量的修改，就能在不同的JPA框架下運行。
2. 容器特性
   - JPA框架支持大數據集、事務、併發等容器及事務。
3. 簡單：
   - 提供簡單的編程模型，在JPA框架下創建實體和創建類一樣，只需要使用javax.persistance.Entity進行注釋。
4. 查詢能力：
   - JPA得查詢語言是面向對象而非面向數據庫，類似於Hibernate HQL。
   - JPA定義了獨特的JPQL(Java Persistance Query Language)
   - JPQL 是 EJBQL 的一種擴展，是針對實體的一種查詢語言，操作對象是實體，而不是關係數據庫的表。
   - 能夠支持批量的更新和修改，可以使用JOIN, GROUP BY, HAVING和子查詢。
5. 高級特性：
   - JPA能夠支持面向對象的特性，例如，類之間的繼承，多態和類之間的關係

## Spring Data JPA
Spring Data JPA 是在實現JPA規範的基礎上封裝一套JPA應用框架，雖然ORM框架實現了JPA規範，但在不同的ORM框架間切換，仍然需要編寫不同的代碼，而使用Spring Data JPA能夠在不同的ORM框架間進行切換而不需要更改代碼。   

特性：   

1. Spring Data JPA通過統一ORM 框架的訪問持久層操作，來提高開發效率。   
2. 可以配置多個DataSource
3. 可以對多個資料表查詢
4. 可以自訂sql 查詢
5. 有分頁與排序功能

![image](https://user-images.githubusercontent.com/79159894/229261133-04c2dae8-4325-4f86-9825-774c2a002529.png)
https://zhuanlan.zhihu.com/p/115507328    

https://ithelp.ithome.com.tw/articles/10194906
## 使用JPA API
1. 創建Customer 實體類對應的數據庫表 customer
2. 創建maven 項目，並加入相關依賴
3. 加上JPA配置信息
4. 編寫客戶Customer實體類，配置類屬性和表之間的映射關係
5. 在test package中創建 CustomerDaoTest，使用Junit進行測試
