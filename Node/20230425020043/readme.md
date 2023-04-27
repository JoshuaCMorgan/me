# Express Router

Right now, our app is getting quite busy. As you can see, we have `/login`, `/api/people`, `/api/people`, `/api/people:id`. Wouldn't it be nice if we could group like routes togeher. The solution is using expert router where we can group those routes together.
Then set each up as seperate controllers, using MVC pattern.

```js
const express = require("express");
const app = express();
let { people } = require("./data");

app.use(express.static("./methods-public"));
app.use(express.urlencoded({ extended: false }));
app.use(express.json());

app.post("/login", (req, res) => {
  // stuff
});
app.get("/api/people", (req, res) => {
  //stuff
});
app.post("/api/people", (req, res) => {
  // stuff
});
app.put("/api/people/:id", (req, res) => {
  // stuff
});
app.delete("/api/people/:id", (req, res) => {
  // stuff
});
app.listen(5000, () => {
  console.log("Server is listening on port 5000....");
});
```
