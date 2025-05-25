# Mongodb

# 🍃 MongoDB Basic Syntax Cheat Sheet

## 🔹 1. Database Commands
```js
// Show all databases
show dbs

// Create or switch to a database
use database_name

// Show current database
db

// Drop a database
db.dropDatabase()
```

---

## 🔹 2. Collection Commands
```js
// Show collections (like tables)
show collections

// Create a collection
db.createCollection("collection_name")

// Drop a collection
db.collection_name.drop()
```

---

## 🔹 3. Insert Documents
```js
// Insert one document
db.collection_name.insertOne({ key1: value1, key2: value2 })

// Insert many documents
db.collection_name.insertMany([
  { key1: value1 },
  { key1: value2 }
])
```

---

## 🔹 4. Find / Query Documents
```js
// Find all documents
db.collection_name.find()

// Find with condition
db.collection_name.find({ key: value })

// Pretty print results
db.collection_name.find().pretty()
```

---

## 🔹 5. Update Documents
```js
// Update one document
db.collection_name.updateOne(
  { key: value }, // filter
  { $set: { key: new_value } } // update
)

// Update many documents
db.collection_name.updateMany(
  { key: value },
  { $set: { key: new_value } }
)
```

---

## 🔹 6. Delete Documents
```js
// Delete one document
db.collection_name.deleteOne({ key: value })

// Delete many documents
db.collection_name.deleteMany({ key: value })
```

---

## 🔹 7. Query Operators
```js
// Greater than, less than
{ age: { $gt: 18 } }
{ age: { $lt: 30 } }

// AND / OR
{ $and: [ { age: { $gt: 18 } }, { city: "Delhi" } ] }
{ $or: [ { city: "Delhi" }, { city: "Mumbai" } ] }

// IN / NOT IN
{ city: { $in: ["Delhi", "Mumbai"] } }
{ city: { $nin: ["Chennai"] } }

// NOT
{ age: { $not: { $gt: 25 } } }
```

---

## 🔹 8. Projection (Select Fields)
```js
// Include only name and age
db.collection_name.find({}, { name: 1, age: 1 })

// Exclude _id
db.collection_name.find({}, { name: 1, _id: 0 })
```

---

## 🔹 9. Sorting and Limiting
```js
// Sort by age ascending
db.collection_name.find().sort({ age: 1 })

// Sort by age descending
db.collection_name.find().sort({ age: -1 })

// Limit results
db.collection_name.find().limit(5)

// Skip results
db.collection_name.find().skip(5)
```

---

## 🔹 10. Aggregation (Basic)
```js
// Group by field and count
db.collection_name.aggregate([
  { $group: { _id: "$city", total: { $sum: 1 } } }
])

// Match + group example
db.collection_name.aggregate([
  { $match: { status: "active" } },
  { $group: { _id: "$city", count: { $sum: 1 } } }
])
```

---

## 🔹 11. Indexing
```js
// Create index
db.collection_name.createIndex({ key: 1 })   // 1 = ASC, -1 = DESC

// View indexes
db.collection_name.getIndexes()

// Drop index
db.collection_name.dropIndex("key_1")
```

---

## 🔹 12. Common Commands
```js
// Count documents
db.collection_name.countDocuments()

// Distinct values of a field
db.collection_name.distinct("fieldname")

// Rename collection
db.collection_name.renameCollection("new_name")

// Drop entire collection
db.collection_name.drop()
```

---

🧠 *MongoDB stores data as BSON (Binary JSON), and operations are performed using JavaScript-like syntax in the shell.*
