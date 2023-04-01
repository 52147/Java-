# Spring Data JPA


## ORM(Object Relative Database Mapping)
ORM代表對象關係映射，
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
