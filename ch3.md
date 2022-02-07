# Chapter 3: Creating and Manipulating Documents

## Insert
- Every document must have a unique (within the collection) `_id` field value.
- Attempting to insert a document with existing `_id` field value raises and error and the document doesn't get inserted.
- While importing, `--drop` option removes the existing collection before inserting collection.
- `.findOne()` to retrive any collection that matches the query.
- `.insert()` to insert a document into a collection.
- By default, all objects are inserted in order.
  + If an insertion is failed, the process stops so the rest of the documents is not inserted.
- Pass option `{"unordered": true}` to insert without order, that means the insertions doesn't stop upon failure.
- An attempt to inserting document to non-existing collection gets the collection created implicity before the insertion.
  + Same applies for databases.

## Update
- MQL : Mongo Query Language
- `.update()` updates the first matched document, `.updateAll()` updates all matched documents.
- `.updateMany(<query>, <update operation given in MQL>)`
- `$inc` increment operator in MQL
  + Ex: `{"$inc": {"pop": 10, "abc": 20}}` tells to increase value of field `pop` by 10 and `abc` by 20.
  + If the given field doesn't exists, the value for the field is assumed `0`.
- `$set` set operator, sets the value(s) for the given field(s).
  + If the given field doesn't exist, it's created implicitly.
- `$push` to append to an array.
  + If the given field doesn't exists, the value for the field is assumed `[]`.

## Delete
- `.deleteOne()` deletes the first matched document (mostly used with querying by `_id`), `.deleteMany()` deletes all matching documents.
- `db.<collection name>.drop()` to drop collection along with its all documents.
- When all collections are deleted from a database, the database disappears from the output of `show dbs`.