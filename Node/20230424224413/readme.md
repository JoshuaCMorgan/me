# what is middleware

It stands between the request that comes in and the response given.

```js
const express = require("express");
const app = express();

//  req => middleware => res

const logger = (req, res, next) => {
  const method = req.method;
  const url = req.url;
  const time = new Date().getFullYear();
  console.log(method, url, time);
  next();
};

app.get("/", logger, (req, res) => {
  res.send("Home");
});
app.get("/about", logger, (req, res) => {
  res.send("About");
});

app.listen(5000, () => {
  console.log("Server is listening on port 5000....");
});
```

We can simplify it. `express.use` allows us to not have to duplicate code. We can add our middleware to any route.
It's very important to know that placement matters. All routes below it will receive the middleware.

```js
const express = require("express");
const app = express();
const logger = require("./logger");
const authorize = require("./authorize");
//  req => middleware => res
app.use(logger);
// api/home/about/products
app.get("/", (req, res) => {
  res.send("Home");
});
app.get("/about", (req, res) => {
  res.send("About");
});
app.get("/api/products", (req, res) => {
  res.send("Products");
});
app.get("/api/items", (req, res) => {
  console.log(req.user);
  res.send("Items");
});

app.listen(5000, () => {
  console.log("Server is listening on port 5000....");
});
```

We can make our middlewear more specific by adding a path. Express will invoke the supplied function for any route starting with the supplied path. The example below will work with `/api/products` and `/api/items`

```js
app.use("/api", logger);
// api/home/about/products
app.get("/", (req, res) => {
  res.send("Home");
});
app.get("/about", (req, res) => {
  res.send("About");
});
app.get("/api/products", (req, res) => {
  res.send("Products");
});
app.get("/api/items", (req, res) => {
  console.log(req.user);
  res.send("Items");
});
```

If we have multiple middleware

```js
app.use([logger, authorize]);
```

With middleware, you can also add multiple middleware to argument like this:

```js
app.get("/api/items", [logger, authorize], (req, res) => {
  console.log(req.user);
  res.send("Items");
});
```

our middleware function is in its own file. There is something nice about middleware. You'll notice that we add to `req.user`

```js
// They will need to have url: http://localhost:5001/?user=josh
const authorize = (req, res, next) => {
  console.log(req);
  const { user } = req.query;
  if (user === "josh") {
    req.user = { name: "josh", id: 3 };
    next();
  } else {
    res.status(401).send("Unauthorized");
  }
};

module.exports = authorize;
```

By doing this, we can then use it anywhere in our application.

```js
//...
app.get("/api/items", (req, res) => {
  console.log(req.user);
  res.send("Items");
});
```

## Options for middleware

We can use or own, like those above, those from built-in fromexpress, and any third party.

Here is a built-in middleware from express.

```js
app.use(express.static("./public"));
```

Here is a third party, which has to be installed. `morgan` npm is a popular logger.

```js
const logger = require("./logger");
const authorize = require("./authorize");
//  req => middleware => res

// app.use([logger, authorize])
// app.use(express.static('./public'))
app.use(morgan("tiny"));
```

#express #middleware #req.user #morgan
