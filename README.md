# Quick.MongoDB
Quick mongodb wrapper for beginners.

![QuickMongo](https://nodei.co/npm/quick.mongodb.png)

# Features
- Beginner friendly
- Easy to use
- Very similar to **[quick.db](https://npmjs.com/package/quick.db)**
- Dot notation support
- Import & export support
- Key value based
- Simple
- Asynchronous
- Multiple model support

# Quick Example

```js
const { Database } = require("quick.mongodb");
const db = new Database("mongodb://localhost/quick.mongodb");

db.on("ready", () => {
    console.log("Database connected!");
});

db.set("foo", "bar");

db.get("foo").then(console.log);
```

# Importing data from quick.db

```js
const db = require("quick.db");
const { Database } = require("quick.mongodb");
const mongo = new Database("mongodb://localhost/quick.mongodb");

function importData() {
    const data = db.all();
    mongo.import(data).then(() => {
        console.log("Done!");
    });    
}

mongo.on("ready", () => importData());
```

# Example

```js
const { Database } = require("quick.mongodb");
const db = new Database("mongodb://localhost/quick.mongodb");

// Setting an object in the database:
db.set("userInfo", { difficulty: "Easy" }).then(console.log);
// -> { difficulty: 'Easy' }

db.push("userInfo.items", "Sword").then(console.log);
// -> { difficulty: 'Easy', items: ['Sword'] }

db.add("userInfo.balance", 500).then(console.log);
// -> { difficulty: 'Easy', items: ['Sword'], balance: 500 }

// Repeating previous examples:
db.push("userInfo.items", "Watch").then(console.log);
// -> { difficulty: 'Easy', items: ['Sword', 'Watch'], balance: 500 }

db.add("userInfo.balance", 500).then(console.log);
// -> { difficulty: 'Easy', items: ['Sword', 'Watch'], balance: 1000 }

// Fetching individual properties
db.get("userInfo.balance").then(console.log);
// -> 1000
db.get("userInfo.items").then(console.log);
// -> ['Sword', 'Watch']
```