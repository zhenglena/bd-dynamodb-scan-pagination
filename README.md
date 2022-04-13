### Scan FoodItems with limit and last evaluated key

You own a grocery store and have a database table, `FoodItems`. The table keeps track of all the food items in your
store, the amount left in the inventory for each item, and whether you need to restock that item. 

First, use CloudFormation to populate the table.

1. Create the tables we'll be using for this activity by running the following `aws` CLI commands:
   ```none
   aws cloudformation create-stack --region us-west-2 --stack-name dynamodbscan-fooditemstable --template-body file://cloudformation/DynamoDB_FoodItems.yml --capabilities CAPABILITY_IAM
   ```
1. Make sure the `aws` command runs without error.
1. Log into your AWS account on and verify that the table exists in DynamoDB and has sample data.

The `FoodItems` table looks like the following:

* `id`: partition key — unique id for each food item
* `expirationDate`: expiration date for the food item
* `foodName`: name of the food item
* `foodSection`: section the food item belongs in (produce, canned, meat, etc.)
* `inventoryRemaining`: how many of each item is left in inventory

You want to implement the method, `scanFoodItemsWithLimit()`, in the `FoodItemDao` class to scan the table for all the  
food items so you can allow the store manager to browse the inventory. You want to limit the amount of items that you 
retrieve at one time since the table is very large.

The `FoodItem` class is already written and annotated for you.

The unit tests in `FoodItemDaoTest` are set-up with a mock database so that you can test your methods offline. The 
`main()` method is set-up in `FoodItemApp` so that you can connect to the real `FoodItems` table and test your methods 
that way.

HINTS:
* [How can I limit the results of the scane?](hints/hint-01.md)
