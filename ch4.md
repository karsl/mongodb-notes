# Advanced CRUD Operations

## Comparison Operators
+ Has the syntax `{<field name (left operand)> : {<operator> : <value (right operand)>}, ...}`
+ https://docs.mongodb.com/manual/reference/operator/query-comparison/
+ `$eq` operator can used implicity.
  - For example, `{"usertype": {"$eq": "Customer"}` can be written as `{"usertype": "Customer}`.

## Logical Operators
+ `$and`, `$or`, `$nor` has the syntax `{<operator>: [<expr1>, <expr2>, ...]}` while `$not` has the syntax `{<field name>: {"$not": <operator expr>}}`
  - Example for `$not`: `db.inventory.find( { price: { $not: { $gt: 1.99 } } } )`
+ https://docs.mongodb.com/manual/reference/operator/query-logical/
+ `$and` operator can used implicity.
  - For example, `{"$and": {"student_id": {"$gt": 25}}, {"student_id": {"$lt": 100}}}`
  - and even further: `{"student_id": {"$gt": 25, "$lt": 100}}`

## Expressive Query Operator
+ Syntax: {$expr: {<expression>}}
+ `$` denotes the operator and also addresses **value** of field
+ Use `$expr` if the query depends on a field value.

## Array Operators
+ `{<array field>: "val"` yields yields true if val in the array field's value.
  - `{"amentities": "Internet"}` true iff `"Internet"` in `$amentities`
+ Use `$all` operator to match collection of values (in any order).
+ Use `$size` to match the size of the array
  - `{"amentities": {"$size": 20, "$all": ["Internet", "Wifi"]}`
+ `$elemMatch` to run a predicate on an element of array.
  - `{ "scores": { "$elemMatch": { "score": { "$gt": 85 } } }`

## Projection
+ Second parameter of `.find()`.
+ Pass a JSON, where keys are the fields and values are 0 or 1 for exclusion and inclusion.
  - They can't be mixed. They all must be 0 or 1. 
    + `_id` field is an exception here since it's always included by default. It can be set to 0 to be excluded.
+ `$elemMatch` can also be used to project desired elements of an array.

## Subdocuments
+ Subdocument ~ Inner Object, use . (dot) to access fields of subdocument.
  - `find({outer document field.subdocument field : "some value"})`
+ For array fields, index can also be used after the dot to select the element at that index.
  - `find({field.0.innerfield: "value")`
