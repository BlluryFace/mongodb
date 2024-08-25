## Basic commands
### Clear past commands
* `cls`
### To use and create a new databse
* `use database_name`
### Create a new collection
* `db.createCollection("collection_name")`
### Return all the documents in a database
* `db.collection_name.find()`
### Delete a database
* `db.dropDatabase()`
### Insert one collection
* `db.collection_name.insertOne({field: "value"})`
### Insert one many
* `db.collection_name.insertMany([{field1: "value1"}, {field2: "value2"}])`
### Sort
* `db.collection_name.find().sort({key: sort_type})`
* sort_type = 1 -> bottom to top
* sort_type = -1 -> top to bottom
### Limit
* `db.collection_name.find().limit(desired_limit)`
* If the limit is added without sort, the default sort will be according to id
* Limit with sort: `db.collection_name.find().sort(key: sort_type).limit(desired_limit)`
### Find document with a specific value
* `db.collection_name.find({query}, {projection})`
### Update a document
* `db.collection_name.updateOne({filter}, {update})`
* update = $set: update information
* update = $unset: remove a field (Ex: $unset:{fullTime:""})
### Update many documents
* `db.collection_name.updateMany({selection_criteria}, {update}`
### Delete one document
* `db.collection_name.deleteOne({key: value})`
### Delete many documents
* `db.collection_name.deletemMany({key: value})`
### Comparison operators
* `$ne`: excluded\
Ex: `db.students.find({name: {$ne:"Spongebob"}})`
* `$lt`: less than\
Ex: `db.students.find({age:{$lt:20}})`
* `$lte`: less than (included)\
Ex: `db.students.find({age:{$lte: 27}})`
* `$gt`: greater than\
Ex: `db.students.find({age:{$gt: 27}})`
* `$gte` greater than (included)\
Ex: `db.students.find({age: {$gte: 27}})`
* `$in`: included specific values\
Ex: `db.students.find({name:{$in:["Spongebob","Larry"]}})` 
* `$nin`: not included specific values\
Ex: `db.students.find({name:{$nin:["Spongebob","Larry"]}})` 
* `$and`: return documents that satisfy more than 2 conditions\
Ex: `db.students.find({$and: [{fullTime:true}, {age:{$lte:22}}]})`
* `$or`: return documents that satisfy on of the 2 conditions\
Ex: `db.students.find({$or: [{fullTime:true}, {age:{$lte:22}}]})`
* `$nor`: return documents that non of the 2 conditions\
Ex: `db.students.find({$nor: [{fullTime:true}, {age:{$lte:22}}]})`
* `$not`: return all values that the opposite of a condition. Use to include null in returned value
Ex: `db.students.find({age:{$not:{$gte:30}}})`
### Indexing
* Indexing allows for quicker lookup by indexing a field in a particular order
* Use wisely because it will take more time to update a field
* Recommend for doing more searches than updates
* `db.collection_name.createIndex({name: 1})`
* To see all indexes: `db.collection_name.getIndexes()`
* To delete an index: `db.collection_name.dropIndex(index_name)`
* 