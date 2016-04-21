## Start mongo

  I assume that you all put mongodb in your environment path, otherwise you need to go to the directory where you installed your mongo.

  * Open a command promt and input the following command 
    
    `mongodb.exe --dbpath "D:\Software\MongoDB 3.0.2\data"`
  * Open another command prompt and issue the following command 
   
    `mongo.exe`
  
## Commands about Database 

1. Create Database use the command `use`

    `use DATABASE_NAME`
    
2. Check your currently selected database use the command `db`

3. Check your databases list, then use the command `show dbs`

  **Note:** Your new created database is not present in list before you insert atleast one document into it.

4. The command `db.dropDatabase()` is used to drop a existing database

  *Tips:* You need to switch to the database you want to delete first by using `use` command, then use `db.dropdatabase()` command to drop the choosed database.

## Commands about Collection (As for tables in RMDB)

1. MongoDB `db.createCollection(name, options)` is used to create collection.

  `use test`
  `db.createCollection("mycollection")`

2. Check the created collection by using the command `show collections`

  **Note:** In mongodb you don't need to create collection. MongoDB creates collection automatically, when you insert some document.

3. MongoDB's `db.COLLECTION_NAME.drop()` is used to drop a collection from the database.

  **Note:** First, check the available collections into your database _mydbName_, then drop the collection with the name _mycollectionName_. Drop() method will return true, if the selected collection is dropped successfully otherwise it will return false

## Commands about Document

1. Insert Document

  `db.COLLECTION_NAME.insert(document)`

```

  db.glist.insert(
  {	
  	user_id: 0002,
  	phone_num: '202222222',
  	email: 'Emma@gmail.com',
  	first_name: 'Emma',
  	last_name: 'Wason',
  	rating: 5,
  	items: [
  		{
  			item_name: 'hello ketty shirt',
  			price: 20,
  			number_sold: 1,
  			location: 'Washington DC',
  			delivery_info: 'UPS'
  		},
  
  		{
  			item_name: 'hello ketty shirt',
  			price: 20,
  			number_sold: 1,
  			location: 'Washington DC',
  			delivery_info: 'UPS'
  		}
  	]
	})
	
```

  **Note:** To insert the document you can use `db.post.save(document`) also. If you don't specify `_id` in the document then save() method will work same as `insert()` method. If you specify `_id` then it will replace whole data of document containing _id as specified in `save()` method.

2. Query Document
  
  1. `db.COLLECTION_NAME.find()` will display all the documents in a non structured way.

  	`db.COLLECTION_NAME.find().pretty()` display the results in a formatted way.

  	**Note:** Apart from find() method there is findOne() method, that returns only one document.
  
  2. In the find() method if you pass multiple keys by separating them by ',' then MongoDB treats it AND condition. Basic syntax of AND is shown below −

  	`db.mycol.find({key1:value1, key2:value2}).pretty()`

  ```
	  >db.glist.find({"first_name":"Alison","items.item_id":1}).pretty()
	
	{
        "_id" : ObjectId("57100107b35de450e6bc25eb"),
        "user_id" : 1,
        "phone_num" : "2021111111",
        "email" : "Alison@gmail.com",
        "first_name" : "Alison",
        "last_name" : "Wiliam",
        "rating" : 11,
        "items" : [
                {
                        "item_id" : 1,
                        "item_name" : "iphone6",
                        "price" : 720,
                        "number_sold" : 1,
                        "location" : "New York",
                        "delivery_info" : "Fedfex"
                },
                {
                        "item_id" : 2,
                        "item_name" : "Nike women's shoes",
                        "price" : 150,
                        "number_sold" : 1,
                        "location" : "New York",
                        "delivery_info" : "UPS"
                }
        ]
	}
	
  ```
  
  3. To query documents based on the OR condition, you need to use `$or` keyword. Basic syntax of OR is shown below −

	```
	  db.mycol.find(
	   {
	      $or: [
	         {key1: value1}, {key2:value2}
	      ]
	   }
	  ).pretty()
	
	```  
	
	```
	
	>db.glist.find({"first_name":"Alison","items.item_id":1}).pretty()
	
	{
        "_id" : ObjectId("57100107b35de450e6bc25eb"),
        "user_id" : 1,
        "phone_num" : "2021111111",
        "email" : "Alison@gmail.com",
        "first_name" : "Alison",
        "last_name" : "Wiliam",
        "rating" : 11,
        "items" : [
                {
                        "item_id" : 1,
                        "item_name" : "iphone6",
                        "price" : 720,
                        "number_sold" : 1,
                        "location" : "New York",
                        "delivery_info" : "Fedfex"
                },
                {
                        "item_id" : 2,
                        "item_name" : "Nike women's shoes",
                        "price" : 150,
                        "number_sold" : 1,
                        "location" : "New York",
                        "delivery_info" : "UPS"
                }
        ]
	}
	
	```
  4. Using AND and OR together
  
     Below given example will show the documents that have price greater than 50 and whose location is either Washington DC or New York. Equivalent sql where clause is `where price>50 and (location='Washington DC' or rating>2')`
	
	```
	
	>db.glist.find({"items.price":{$gt:10}, $or:[{"items.location":"Washington DC"},{"items.rating":{$lt:50}}]}).pretty()
	
	{
        "_id" : ObjectId("570fff19b35de450e6bc25e9"),
        "user_id" : 2,
        "phone_num" : "202222222",
        "email" : "Emma@gmail.com",
        "first_name" : "Emma",
        "last_name" : "Wason",
        "rating" : 5,
        "items" : [
                {
                        "item_id" : 1,
                        "item_name" : "hello ketty shirt",
                        "price" : 20,
                        "number_sold" : 1,
                        "location" : "Washington DC",
                        "delivery_info" : "UPS"
                },
                {
                        "item_id" : 2,
                        "item_name" : "sunglass",
                        "price" : 50,
                        "number_sold" : 1,
                        "location" : "Washington DC",
                        "delivery_info" : "UPS"
                }
        ]
	}
	```
3. Update Document

  The command `db.COLLECTION_NAME.update(SELECTIOIN_CRITERIA, UPDATED_DATA)` updates values in the existing document. 

  ```
  
  >db.glist.update({'user_id':2,'items.item_id':2},{$set:{'item_name':'sunglasses'}})

  WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

  ```
  
  **Note:** By default mongodb will update only single document, to update multiple you need to set a paramter 'multi' to true.
  
  `db.glist.update({'location':'New York'},{$set:{'location':'Boston'}}, {multi:true})`
  
4. Replace the existing document with the new document passed in save() method.

  `db.COLLECTION_NAME.save({_id:ObjectId(),NEW_DATA})`

5. Delete Document

  **_deletion criteria_ : (Optional) deletion criteria according to documents will be removed.
 
    `db.COLLECTION_NAME.remove(DELLETION_CRITTERIA)`
 	
  ** _justOne_: (Optional) if set to true or 1, then remove only one document.
  
    `db.COLLECTION_NAME.remove(DELETION_CRITERIA,1)`
    
  ** _remove all documents_: If you don't specify deletion criteria, then mongodb will delete whole documents from the collection. **This is equivalent of SQL's truncate command**.
  
    `db.glist.remove({'first_name':'Alison'})`  
    
    `db.glist.remove({'first_name':'Alison', 1})`
    
    `db.glist.remove()`
    
## Projection: Selecting only necessary data
  
1. Set list of fields with value 1 or 0. 1 is used to show the field while 0 is used to hide the field.
  
  `db.COLLECTION_NAME.find({},{KEY:1})`
  
  `db.glist.find({"first_name":1, _id:0})`
  
2. Limiting Records
  
  `db.COLLECTION_NAME.find().limit(NUMBER)`

  **Note:** If you don't specify number argument in limit() method then it will display all documents from the collection.
  
3. Apart from limit() method there is one more method skip() which also accepts number type argument and used to skip number of documents.
  
  `db.COLLECTION_NAME.find().limit(NUMBER).skip(NUMBER)`

  `db.glist.find({},{"email":1, _id:0}).limit(1).skip(1)` Only display second document.
  
4. Sortting Records
  
  `db.COLLECTION_NAME.find().sort({KEY:1})`
  
  **Note:** 1 is used for ascending order while -1 is used for descending order.Please note if you don't specify the sorting preference, then sort() method will display documents in ascending order.

5. Indexing
  
  Create an index. Here key is the name of filed on which you want to create index and 1 is for ascending order. To create index in descending order you need to use -1.

  `db.COLLECTION_NAME.ensureIndex({KEY:1})` 

  `db.glist.ensureIndex({"rating:-1"})`
  
  In ensureIndex() method you can pass multiple fields, to create index on multiple fields.
  
  `db.glist.ensureIndex({"rating:-1","user_id":1})`
  
6. Aggregation

  `db.COLLECTION_NAME.aggregate(AGGREGATE_OPERATION)`
  
  `db.glist.aggregate([{$group:{_id: "rating",num_rate:{$sum:1}}}])`

  Sql equivalent query for the above use case will be `select rating, count(*) from glist group by rating`

  [A list of available aggregation expressions](http://www.tutorialspoint.com/mongodb/mongodb_aggregation.htm)
  
  
  
