# 📘 MongoDB CRUD & Aggregation Project

## 🎯 Objective

This project demonstrates the implementation of **CRUD operations** and the **Aggregation Framework** in MongoDB.

---

## 🗂️ Database & Collection

* Database: `library`
* Collection: `books`

---

## ➕ Insert Operations

* Inserted single and multiple book documents
* Fields used: `title`, `author`, `published_year`, `price`

---

## 🔍 CRUD Operations

### Create

* `insertOne()`
* `insertMany()`

### Read

* `find()`
* Filter using conditions

### Update

* `updateOne()`

### Delete

* `deleteOne()`

---

## 🔃 Sorting

* Ascending: `sort({ published_year: 1 })`
* Descending: `sort({ published_year: -1 })`

---

## ⚙️ Aggregation Operations

### 🔹 Filter

```js
db.books.aggregate([
  { $match: { published_year: { $gt: 2010 } } }
])
```

### 🔹 Sort

```js
db.books.aggregate([
  { $sort: { price: -1 } }
])
```

### 🔹 Limit

```js
db.books.aggregate([
  { $sort: { price: -1 } },
  { $limit: 3 }
])
```

### 🔹 Group (Count Books per Author)

```js
db.books.aggregate([
  {
    $group: {
      _id: "$author",
      totalBooks: { $sum: 1 }
    }
  }
])
```

### 🔹 Average Price

```js
db.books.aggregate([
  {
    $group: {
      _id: "$author",
      avgPrice: { $avg: "$price" }
    }
  }
])
```

### 🔹 Highest Price per Author

```js
db.books.aggregate([
  { $sort: { price: -1 } },
  {
    $group: {
      _id: "$author",
      highestPrice: { $first: "$price" }
    }
  }
])
```

### 🔹 Total Books Count

```js
db.books.aggregate([
  {
    $group: {
      _id: null,
      totalBooks: { $sum: 1 }
    }
  }
])
```

---

## ⚠️ Key Learning

* Maintain **consistent data types** (numbers for year & price)
* Use aggregation for **data analysis**
* `$sort + $group + $first` helps find **maximum values**

---

## 🧠 Conclusion

MongoDB aggregation provides powerful tools to **filter, group, and analyze data efficiently** within the database.

---

## 🚀 Tools Used

* MongoDB
* Mongo Shell (mongosh)
