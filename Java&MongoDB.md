# MongoDB

- MongoDB is a distrubuted Datbase writed by C++.
- MongoDb is a type a non-relational database.
- MongoDb stored data in Bson document, which are JSON-like structure.
- Sechema flexiable :This collection can contain document with differnet field and data types and allows for high flexibility.
- Ad-hoc query: allow developers update quert in real time. Support field query, range query, regular expression searchs because mongodb index BSON document.
- Indexing BSON: index is used to improve search speed. With a right index, database don't need to scan all documents one by one to identify the ones that mathch the query statement.


## Install MongoDB

## Basic mongoDB command 
- Open mongoDB shell
- use 27027 default port
![image](https://user-images.githubusercontent.com/79159894/201466864-6188fc47-8222-483d-913d-3417fe9a3a24.png)

- show all database
```
show dbs
```
![image](https://user-images.githubusercontent.com/79159894/201466881-825fb50c-6ba2-45ab-bbf1-b2b1460e8e9f.png)
- close the shell
```
exit
```
Use admin database
```
use admin
```
create user in admindb
```
db.createUser( {user:"mongoloide", pwd:"mongoloide*2017", roles:["root"]} )
```
root can only be used in the admin database and has all privileges.
![image](https://user-images.githubusercontent.com/79159894/201467234-5d876392-c896-4754-a907-ae90ce7c4562.png)
- Return 1 means we successfully login
