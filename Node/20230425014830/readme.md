## Form data with Express

If we have a form data of this sort:

```html
<main>
  <form action="/login" method="POST">
    <h3>Traditional Form</h3>
    <div class="form-row">
      <label for="name"> enter name </label>
      <input type="text" name="name" id="name" autocomplete="false" />
    </div>
    <button type="submit" class="block">submit</button>
  </form>
</main>
```

We will need to get that data when it the http request comes to our server. With express, we can use middleware.
We need to use `urlencoded` method and flag, which will add form values
to `req.body`.

```js
const express = require("express");
const app = express();
let { people } = require("./data");

// static assets
app.use(express.static("./methods-public"));
// parse form data
app.use(express.urlencoded({ extended: false }));
// parse json
app.use(express.json());

app.post("/api/people", (req, res) => {
  const { name } = req.body;
  if (!name) {
    return res
      .status(400)
      .json({ success: false, msg: "please provide name value" });
  }
  res.status(201).json({ success: true, person: name });
});

app.post("/login", (req, res) => {
  const { name } = req.body;
  if (name) {
    return res.status(200).send(`Welcome ${name}`);
  }

  res.status(401).send("Please Provide Credentials");
});
app.listen(5001, () => {
  console.log("Server is listening on port 5001....");
});
```
