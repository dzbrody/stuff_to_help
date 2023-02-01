## query thats searches across all collections for a particular field userId

Here's an example of how you could search across all collections for a particular field "userId" in MongoDB:
```
db.getCollectionNames().forEach(function(collection) {
    var cursor = db[collection].find({"userId": {$exists: true}});
    if (cursor.count() > 0) {
        print(collection + ": ");
        cursor.forEach(function(doc) {
            print("\t" + doc._id + ": " + JSON.stringify(doc.userId));
        });
    }
});
```
This query will loop through all the collections in the current database, check if the field "userId" exists in each document, and print out the document id and the value of the "userId" field if it does exist.
