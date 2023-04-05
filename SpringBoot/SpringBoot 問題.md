# SpringBoot 問題
Parking Lot Management System 問題

## 問題 1 : Upload file
如果後端需要接收前端的 multipart/form-data request，後端需要在function 加上 @RequestParam("file") MultipartFile file。    

以下spring boot function接收前端傳來的post request帶有excel黨：    
讀取檔案中的資料後，加到db。
```java
    @PostMapping("/import")
    public Boolean imp(@RequestParam("file") MultipartFile file) throws Exception {
        InputStream inputStream = file.getInputStream();
        ExcelReader reader = ExcelUtil.getReader(inputStream);
        List<User> list = reader.readAll(User.class);
        userService.saveBatch(list);
        return true;
    }
```
https://stackoverflow.com/questions/47493549/spring-file-upload-with-requestparam   

https://github.com/52147/Java-Interview-Questions/blob/main/Axios%20%E7%AD%86%E8%A8%98%E6%9C%AC.md#%E7%99%BC%E9%80%81%E4%B8%80%E5%80%8Bpost%E8%AB%8B%E6%B1%82
## 問題 2: 用tomcat server run intellj web
出現localhost:1099 already in use   
試圖用以下指令在cmd中查看 端口1099 的server   
netstat -aon | find "1099"    
沒有反應。     
解決方式:   
1. 用管理員權限打開cmd
2. 照順序在cmd打以下指令:
斷開網路連線。
net stop winnat

net stop LanmanWorkstation

net stop WlanSvc

net stop WwanSvc

從端口保留名單中，排除1099端口。    

netsh int ipv4 add excludedportrange protocol=tcp startport=1099 numberofports=4

開始網路連線。
net start winnat

net start LanmanWorkstation

net start WlanSvc

net start WwanSvc


https://stackoverflow.com/a/66827598

### 延伸討論: 解決window端口占用問題


## 問題 3 : hibernate

org.hibernate.HibernateException: Access to DialectResolutionInfo cannot be null when 'hibernate.dialect' not set   

解決：把 application properties 中的password 改成自己的 sql password。    

https://stackoverflow.com/questions/26548505/org-hibernate-hibernateexception-access-to-dialectresolutioninfo-cannot-be-null    

## 問題 4: Homebrew
用homebrew 安裝舊版sql
https://bbs.huaweicloud.com/blogs/351111

## 問題 5: Unknown column 'user0_.a1' in 'field list'
```
java.sql.SQLSyntaxErrorException: Unknown column 'user0_.a1' in 'field list'
```
原因：     

spring boot中所使用的sql 查詢有問題。      

sql 查詢試圖 引用user 表中名稱為a1的column，但實際上a1不存在於表中。    

解決：     

1. 確保在entity中引用了正確的col 名稱
2. 確保 db 中的table 有個名稱a1的col.    
