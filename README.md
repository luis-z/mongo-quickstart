# mongo-quickstart
Simple step by step process for creating an initial DB, Collection and an Admin User in Mongo DB

## Create a new admin user
After installing <b>MongoDB</b> access the mongo shell and execute:
```bash
use admin
db.createUser({ user: "testUser" , pwd: "strongPassword", roles: ["userAdminAnyDatabase", "dbAdminAnyDatabase", "readWriteAnyDatabase"]})
```
This will create a new user called <b>testUser</b> with Admin priviliges.
## Create a new DB
To create a DB called <b>testDB</b> execute:
```bash
use testDB
```
Add an user to the testDB:
```bash
db.createUser(
   {
     user: "dbUser",
     pwd: "strongPassword",
     roles: [ { role: "readWrite", db: "testDB" } ]
   }
)
```

## Create a new collection
```bash
db.createCollection("test", { capped : true, size : 5242880, max : 5000 } )
```
### Now you can connect to the new DB with Compass or backend app using this connect string:
```bash
mongodb://testUser:strongPassword@dbServer:27017/testDB?retryWrites=true&w=majority
```
