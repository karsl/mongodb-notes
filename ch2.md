# Chapter 2: Importing, Exporting and Querying Data

- Data stored in BSON which is not readible by humans.
- Data is retrieved in JSON which is readible by humans.
- import/export for JSON, dump/restore for BSON.
- `show dbs` to list databases
- `use <name of db>` to select the database
- `show collections` to list collection in the selected database
- To query documents: `db.<collection name>.find(<json to query>)` (`db` points to selected database)
  + For example: `db.zips.find({"state": "NY", "city": "Albany"})`
- Call `it` command to iterate to the next page.
- `.count()` to returns number of matched documents. 