# 🍃 MongoDB Basic Syntax Cheat Sheet

---

## 📦 Database Operations

```js
// Show all databases
show dbs

// Create or switch to a database
use database_name

// Show current database
db

// Drop the current database
db.dropDatabase()
```

---

## 📋 Collection Operations

```js
// Show all collections
show collections

// Create a collection
db.createCollection("collection_name")

// Drop a collection
db.collection_name.drop()
```

---

## 📝 Document Operations

### 🔹 Insert Documents

```js
// Insert a single document
db.collection_name.insertOne({ key1: value1, key2: value2 })

// Insert multiple documents
db.collection_name.insertMany([
  { key1: value1, key2: value2 },
  { key1: value3, key2: value4 }
])
```

### 🔹 Query Documents

```js
// Find all documents
db.collection_name.find()

// Find with condition
db.collection_name.find({ key: value })

// Find one document
db.collection_name.findOne({ key: value })

// Projection (select specific fields)
db.collection_name.find({}, { key1: 1, key2: 1 })
```

### 🔹 Update Documents

```js
// Update one document
db.collection_name.updateOne(
  { key: value },
  { $set: { key_to_update: new_value } }
)

// Update multiple documents
db.collection_name.updateMany(
  { key: value },
  { $set: { key_to_update: new_value } }
)
```

### 🔹 Delete Documents

```js
// Delete one document
db.collection_name.deleteOne({ key: value })

// Delete multiple documents
db.collection_name.deleteMany({ key: value })
```

---

## 🔍 Query Operators

```js
// Comparison
$eq, $ne, $gt, $gte, $lt, $lte, $in, $nin

// Logical
$and, $or, $not, $nor

// Element
$exists, $type

// Evaluation
$regex, $expr
```

### Examples

```js
// Find documents with age > 25
db.users.find({ age: { $gt: 25 } })

// Find with multiple conditions
db.users.find({ $and: [ { age: { $gte: 18 } }, { status: "active" } ] })
```

---

## 🧩 Indexing

```js
// Create an index
db.collection_name.createIndex({ field: 1 })  // 1 = ascending, -1 = descending

// Drop an index
db.collection_name.dropIndex({ field: 1 })

// View indexes
db.collection_name.getIndexes()
```

---

## 🔐 Users and Roles (Admin Operations)

```js
// Create user with roles
db.createUser({
  user: "username",
  pwd: "password",
  roles: [ { role: "readWrite", db: "database_name" } ]
})

// Show users
db.getUsers()

// Drop a user
db.dropUser("username")
```

---

## 📎 Miscellaneous

```js
// Count documents
db.collection_name.countDocuments()

// Limit and sort
db.collection_name.find().limit(5).sort({ field: 1 })

// Aggregation framework (example)
db.collection_name.aggregate([
  { $match: { status: "active" } },
  { $group: { _id: "$category", total: { $sum: 1 } } }
])
```

---

## 🧠 Notes

- MongoDB stores data in **BSON** (binary JSON) format.
- Collections are schema-less — each document can have a different structure.
- Common data types: `String`, `Number`, `Object`, `Array`, `Date`, `Boolean`, `Null`.

