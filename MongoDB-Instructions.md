## Start mongo

  I assume that you all put mongodb in your environment path, otherwise you need to go to the directory where you installed your mongo.

  * Open a command promt and input the following command 
    
    `mongodb.exe --dbpath "D:\Software\MongoDB 3.0.2\data"`
  * Open another command prompt and issue the following command 
   
    `mongo.exe`
  
# Commands about Database 

1. Create Database use the command `use`

    `use DATABASE_NAME`
    
2. Check your currently selected database use the command `db`

3. Check your databases list, then use the command `show dbs`

  **Note:** Your new created database is not present in list before you insert atleast one document into it.

4. The command `db.dropDatabase()` is used to drop a existing database

  *Tips:* You need to switch to the database you want to delete first by using `use` command, then use `db.dropdatabase()` command to drop the choosed database.

# Commands about Collection (As for tables in RMDB)

1. MongoDB `db.createCollection(name, options)` is used to create collection.

  `use test`
  `db.createCollection("mycollection")`

2. Check the created collection by using the command `show collections`

  **Note:** In mongodb you don't need to create collection. MongoDB creates collection automatically, when you insert some document.

3. MongoDB's `db.COLLECTION_NAME.drop()` is used to drop a collection from the database.

  **Note:** First, check the available collections into your database _mydbName_, then drop the collection with the name _mycollectionName_. Drop() method will return true, if the selected collection is dropped successfully otherwise it will return false

## Commands about Document

