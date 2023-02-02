## query thats searches across all collections for a particular field userId

Here's an example MongoDB query to search across all collections for a field "userId":

`
db.getCollectionNames().forEach(function(collection) {
   var cursor = db[collection].find({"userId": {$exists: true}});
   if (cursor.count() > 0) {
      print(collection + ": ");
      cursor.forEach(function(doc) {
         print("  " + doc._id + ": " + doc.userId);
      });
   }
});
`

This query uses the getCollectionNames() method to retrieve a list of all collections in the current database. It then loops through each collection and performs a find() operation with a query filter of {"userId": {$exists: true}}, which returns all documents that have a field "userId".

For each document returned, the query prints the document ID and the value of the "userId" field. This query can be modified to perform further operations on the returned documents.

*Note: This query should be executed in the MongoDB shell.
