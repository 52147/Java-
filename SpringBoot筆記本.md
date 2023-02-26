# SpringBoot筆記本

## Issue
### 用tomcat server run intellj web
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


## hibernate

org.hibernate.HibernateException: Access to DialectResolutionInfo cannot be null when 'hibernate.dialect' not set   

解決：把 application properties 中的password 改成自己的 sql password。    
