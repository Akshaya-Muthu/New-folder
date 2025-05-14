📚 MongoDB Database Documentation
This document describes the MongoDB database schema, collections, fields, relationships, and query examples used in this project.

🧩 Database Name
myDatabaseName
📦 Collections Overview
1. users
Field	Type	Description
_id	ObjectId	Unique identifier (auto-generated)
name	String	Full name of the user
email	String	Email address
password	String	Hashed password
createdAt	Date	Account creation date
2. products
Field	Type	Description
_id	ObjectId	Unique identifier
name	String	Product name
price	Number	Product price
category	String	Product category
stock	Number	Quantity in stock
createdAt	Date	Product addition date
3. orders
Field	Type	Description
_id	ObjectId	Unique identifier
userId	ObjectId	Reference to users collection
products	Array	List of product IDs and quantities
totalAmount	Number	Total price of the order
orderDate	Date	Date of order
🔗 Relationships
orders.userId → references users._id

orders.products → contains multiple products._id

🧪 Sample Queries
📄 Find all users
db.users.find({})
🛒 Find orders by user
db.orders.find({ userId: ObjectId("user_id_here") })
🔍 Find products under a category
db.products.find({ category: "Electronics" })
📦 Update stock after an order
db.products.updateOne(
  { _id: ObjectId("product_id_here") },
  { $inc: { stock: -1 } }
)
📂 Import/Export
Export a collection:
mongoexport --db=myDatabaseName --collection=users --out=users.json
Import data:
mongoimport --db=myDatabaseName --collection=users --file=users.json
🔐 Security Tips
Always hash passwords (use bcrypt)

Enable authentication in MongoDB

Use environment variables for DB connection strings
