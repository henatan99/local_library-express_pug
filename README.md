
### Schema Example

```

const mongoose = require("mongoose");

const Schema = mongoose.Schema;

const SomeModelSchema = new Schema({
    a_string: String,
    a_date: Date
});

const SomeModel = mongoose.model("SomeModel", SomeModelSchema);


<!-- Example of schema types -->

const schema = new Schema({
    name: String,
    binary: Buffer,
    living: Boolean,
    updated: { type: Date, default: Date.now() },
    age: { type: Number, min: 18, max: 65, required: true },
    mixed: Schema.Types.Mixed,
    _someId: Schema.Types.ObjectId,
    array: [],
    ofString: [String], // You can also have an array of each of the other types too.
    nested: { stuff: { type: String, lowercase: true, trim: true } },
    email: { type: String, lowercase: true, trim: true }
});
  

const breakfastSchema = new Schema({
    eggs: {
      type: Number,
      min: [6, "Too few eggs"],
      max: 12,
      required: [true, "Why no eggs?"],
    },
    drink: {
      type: String,
      enum: ["Coffee", "Tea", "Water"],
    },
});

```


### MongoDB Atlas documentation to creat connection 

```
require('dotenv').config();

const { MongoClient, ServerApiVersion } = require('mongodb');
const uri = process.env.MONGODB_DATABASE_URL;

<!-- Create a MongoClient with a MongoClientOptions object to set the Stable API version -->
const client = new MongoClient(uri, {
  serverApi: {
    version: ServerApiVersion.v1,
    strict: true,
    deprecationErrors: true,
  }
});

async function run() {
  try {
    // Connect the client to the server	(optional starting in v4.7)
    await client.connect();
    // Send a ping to confirm a successful connection
    await client.db("admin").command({ ping: 1 });
    console.log("Pinged your deployment. You successfully connected to MongoDB!");
  } finally {
    // Ensures that the client will close when you finish/error
    await client.close();
  }
}

run().catch(console.dir);

```