# Chapter 5: Indexing and Aggregation Pipeline

## Aggregation
+ `.aggregate()` function is used to aggregate.
+ which takes an array. Each element is an action. Order of the elements denotes the order of action in aggregation pipeline. So each action in applied in order.
+ `db.listingsAndReviews.aggregate([
{ "$project": { "address": 1, "_id": 0 }},
  { "$group": { "_id": "$address.country",
  "count": { "$sum": 1 } } }
  ])`

## Sort and Limit
+ `.sort({"pop": 1, "city": -1})` sorts by field "pop" in increasing order (+1 increases value) and then by "city" in decreasing order (-1 decreases value).
  - `null` is the smallest, so don't forget to filter them out.
+ `.limit(n)` limits the result for first `n` elements.
+ These two are cursor methods.
+ Even if you first limit then sort, MongoDB first sorts and limits (it assumes you meant to sort then limit)


## Index
+ Both filtering and sorting benefits from indexing, increases performance (in terms of time).
+ db.trips.createIndex({"birth year": 1) where 1 denotes increasing order

# Data modeling
+ **Data that is used together should be stored together**, all the required data should be in the same collection (i.e. joins (as in relational databases) shouldn't be required)

# Upsert
+ When `{"upsert": true}` is pass as third argument to the update function, if a matching document is found then it's updated otherwise a new document will be inserted.
