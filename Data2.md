## Data with rating for every item

```

db.createCollection("gwlist")
{
	"user_id": 0001,
	"phone_num": "2021111111",
	"email": "Alison@gmail.com",
	"first_name": "Alison",
	"last_name": "Wiliam",
	"rating": 11,
	"items": [
		{
			"item_id": 0001,
			"item_name": "iphone6",
			"price": 720,
			"number_sold": 1,
			"rating": 2,
			"location": "New York",
			"delivery_info": "Fedfex"
		},
		{
			"item_id": 0002,
			"item_name": "Nike women's shoes",
			"price": 150,
			"number_sold": 1,
			"rating": 11,
			"location": "New York",
			"delivery_info": "UPS"
		}
	]
}



db.gwlist.insert(
{
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
                        "rating": 22,
                        "location" : "Washington DC",
                        "delivery_info" : "UPS"
                },
                {
                        "item_id" : 2,
                        "item_name" : "sunglass",
                        "price" : 50,
                        "number_sold" : 1,
                        "rating": 14,
                        "location" : "Washington DC",
                        "delivery_info" : "UPS"
                }
        ]})


db.gwlist.insert(
{
        "user_id" : 3,
        "phone_num" : "202222223",
        "email" : "Amanda@sina.com",
        "first_name" : "Amanda",
        "last_name" : "Gutman",
        "rating" : 15,
        "items" : [
                {
                        "item_name" : "Harry Potter series",
                        "price" : 320,
                        "number_sold" : 8,
                        "rating": 3,
                        "location" : "California",
                        "delivery_info" : "UPS"
                },
                {
                        "item_name" : "Starbuck cup",
                        "price" : 20,
                        "number_sold" : 1,
                        "rating": 22,
                        "location" : "Los Angles",
                        "delivery_info" : "UPS"
                }
        ]
})

db.gwlist.insert(
{
        "user_id" : 4,
        "phone_num" : "202222224",
        "email" : "Jack@yahoo.com",
        "first_name" : "Jack",
        "last_name" : "Chinesky",
        "rating" : 14,
        "items" : [
                {
                        "item_name" : "Helminton Blender",
                        "price" : 30,
                        "number_sold" : 1,
                        "rating": 10,
                        "location" : "Chicago",
                        "delivery_info" : "UPS"
                }
        ]
})

db.gwlist.insert(
{
        "user_id" : 5,
        "phone_num" : "202222225",
        "email" : "Tom@gmail.com",
        "first_name" : "Tom",
        "last_name" : "Meson",
        "rating" : 11,
        "items" : [
                {
                        "item_name" : "Nike Shoes",
                        "price" : 130,
                        "number_sold" : 11,
                        "rating": 8,
                        "location" : "New York",
                        "delivery_info" : "UPS"
                }
        ]
})

```
