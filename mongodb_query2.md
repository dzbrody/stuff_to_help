Here's an example MongoDB query that joins three collections "users", "transactions", and "wagers" on the "userId" field:
```
db.users.aggregate([
   {
      $lookup: {
         from: "transactions",
         localField: "userId",
         foreignField: "userId",
         as: "transactions_docs"
      }
   },
   {
      $lookup: {
         from: "wagers",
         localField: "userId",
         foreignField: "userId",
         as: "wagers_docs"
      }
   }
])
```
This query uses the MongoDB aggregate() method to join the three collections. The `aggregate()` method takes an array of stages as input, and each stage performs a specific operation on the documents in the pipeline.

In this query, the first stage uses the `$lookup` operator to join the "users" collection with the "transactions" collection. The from parameter specifies the collection to join with, the localField parameter specifies the field from the current collection to join on, and the foreignField parameter specifies the field from the joined collection to join on. The as parameter specifies the name of the new array that contains the joined documents.

The second stage uses another `$lookup` operator to join the previous result set with the "wagers" collection. The same parameters are used as in the first stage, except the as parameter specifies a different name for the new array of joined documents.

The result of this query is a single document for each user that contains the user information, along with the transactions and wagers documents related to that user, as arrays. The arrays can be further manipulated or filtered as needed.
