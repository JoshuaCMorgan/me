# convert html form data to JSON with jQuery
The snippet below is a utility function to serialize a form's data to JSON:
```js
function convertFormToJSON(form) {
  const array = $(form).serializeArray(); // Encodes the set of form elements as an array of names and values.
  const json = {};
  $.each(array, function () {
    json[this.name] = this.value || "";
  });
  return json;
}

// or 
function convertFormToJSON(form) {
  return $(form).serializeArray().reduce(function (json, { name, value }) {
      json[name] = value;
      return json;
    }, {});
}
```

- What `$(form).serializeArray()` returns:
```js
(2) [{…}, {…}]
    0: {name: 'name', value: 'Red Pens'}
    1: {name: 'message', value: 'here is my message'}
    length: 2
    [[Prototype]]: Array(0)
        at: ƒ at()
        concat: ƒ concat()
        constructor: ƒ Array()
        copyWithin: ƒ copyWithin()
        entries: ƒ entries()
        every: ƒ every()
        fill: ƒ fill()
        filter: ƒ filter()
        find: ƒ find()
        //...(more methods)
```

- What `convertFormToJSON(form)` returns:
```js
{name: 'Red Pens', message: 'here is my message'}
```

- Used with `submit` listener:
```js
$("#contact-form").on("submit", function (e) {
  e.preventDefault();
  const form = $(e.target);
  const json = convertFormToJSON(form);
  console.log(json);
});
```

- Full Code

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <script
      src="https://code.jquery.com/jquery-3.6.0.js"
      integrity="sha256-H+K7U5CnXl1h5ywQfKtSj8PCmoN9aaq30gDh27Xc0jk="
      crossorigin="anonymous"
    ></script>
  </head>
  <body>
    <!-- HTML-->
    <form id="contact-form">
      <label for="name">Name</label>
      <input type="text" id="name" name="name" placeholder="Name" required="" />
      <label for="message">Message</label>
      <textarea
        id="message"
        name="message"
        placeholder="Message"
        required=""
      ></textarea>
      <button type="submit">Send</button>
    </form>

    <!-- JavaScript -->
    <script>
      function convertFormToJSON(form) {
        const array = $(form).serializeArray(); // Encodes the set of form elements as an array of names and values.
        const json = {};
        $.each(array, function () {
          json[this.name] = this.value || "";
        });
        return json;
      }

      $("#contact-form").on("submit", function (e) {
        e.preventDefault();
        const form = $(e.target);
        const json = convertFormToJSON(form);
        console.log(json);
      });
    </script>
  </body>
</html>
```
[form syntax](20220830125949)
#form #submit #json #serialize