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
- show all the users in admin db.
```
show users
```
or
```
db.system.users.find()
```
![image](https://user-images.githubusercontent.com/79159894/201467980-368bda22-51ce-449e-a31d-a1217471ac4c.png)
- mechanisms: [ 'SCRAM-SHA-1', 'SCRAM-SHA-256' ]
- means we use two type of authentication mechanisms.

```
admin> db.system.users.find()

[
  {
    _id: 'admin.mongoloide',
    userId: UUID("34c13f08-35ef-4e0e-8dcf-f866c5c7a3b3"),
    user: 'mongoloide',
    db: 'admin',
    credentials: {
      'SCRAM-SHA-1': {
        iterationCount: 10000,
        salt: '1Tf5UDwFx536ff6znryYPA==',
        storedKey: '77FysqbVE45fFFjfSd+7tyQEFcM=',
        serverKey: 'FpICDELOC/JcjRizCKvZC5pdbMk='
      },
      'SCRAM-SHA-256': {
        iterationCount: 15000,
        salt: 'aOCsfRFUjj7P64UNcbcOZK+YLAIjmK33iKpMFQ==',
        storedKey: 'yD48H09x06Gj6q76PmxxCPiQlf0tUB6gqfQX58gWemM=',
        serverKey: 'ZVTfyQTRHHautig0TRB6Hsfr6lZBlmfFs54R+UjbaBU='
      }
    },
    roles: [ { role: 'root', db: 'admin' } ]
  },
  {
    _id: 'admin.accountUser',
    userId: UUID("5ec9ae5f-6b2f-4cc5-8a1a-daaed7e62275"),
    user: 'accountUser',
    db: 'admin',
    credentials: {
      'SCRAM-SHA-1': {
        iterationCount: 10000,
        salt: 'n1skEThWp+Oy/w5OZyzNGw==',
        storedKey: 'cJ6Gl5sC8XR3bZ97uAu8a+j1jcQ=',
        serverKey: '6/E7bX4SJEkbnvioVu3tF6l8Nvw='
      },
      'SCRAM-SHA-256': {
        iterationCount: 15000,
        salt: 'EmRiX9CURFszypiwAiaJZJFoEfN+GJVNHQkqMg==',
        storedKey: 'C1TxZH7YpY2tcLttmad/lOpN1BGv9HBcxFfFMsuOSkE=',
        serverKey: 'yp+s2F/zAzP9eno7J8JlfUlYlY2W35M+tgybhi7cRoM='
      }
    },
    roles: [
      { role: 'readWrite', db: 'admin' },
      { role: 'dbAdmin', db: 'admin' }
    ]
  }
]
```

## Create new DB
If we don't have test db, mongodb will create it.
```
use test
```
- But if we don't add any data in test db.
- We can use show tables to see data in test db.
- We use show db, test db would not gonna show out.

![image](https://user-images.githubusercontent.com/79159894/201468468-64154df5-49b6-4af7-a1af-7a97fd7d74f9.png)

- if we insert one document in test collection,
- the test db will show
```
test> db.test.insertOne({"name":"shoutzu han"})
test> show dbs
```
![image](https://user-images.githubusercontent.com/79159894/201469047-8533f471-0dd3-4547-a503-be96ac55fcbb.png)
- Drop the test db.
- 1 means successfully drop, 0 means fail.
```
test> db.dropDatabase()
{ ok: 1, dropped: 'test' }
test> show dbs
622DB         8.09 MiB
admin       180.00 KiB
blogDB       72.00 KiB
config      108.00 KiB
local        80.00 KiB
todolistDB  144.00 KiB
wikiDB       80.00 KiB
```
