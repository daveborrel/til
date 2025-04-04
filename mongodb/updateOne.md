# updateOne

In you want to update a document in a collection you need to feed in a filter, and what you want to change.

```typeScript
const myDB = client.db("myDB");
const myColl = myDB.collection("items");
const filter = { _id: 465 };
// update the value of the 'quantity' field to 5
const updateDocument = {
   $set: {
      quantity: 5,
   },
};
const result = await myColl.updateOne(filter, updateDocument);
```

This returns the following document with the following fields

`matchedCount` - number of matched Docuements
`modifiedCount` - the documents that we changed
`upsertedId` - containing the \_id of the upserted documents
`upsertedCount` - number of upserted documents
`acknowledged` - a boolean telling you if there was a write concern

### Source

[MongoDB UpdateOne](https://www.mongodb.com/docs/manual/reference/method/db.collection.updateOne/)
