# Ajax and forms: serialization

Two methods come supported natively: .serialize() and .serializeArray(). 

The .serialize() method serializes a form's data into a query string. For the element's value to be serialized, it must have a name attribute. Please note that values from inputs with a type of checkbox or radio are included only if they are checked.

```js
// Turning form data into a query string
$( "#myForm" ).serialize();
 
// Creates a query string like this:
// field_1=something&field2=somethingElse
```
While plain old serialization is great, sometimes your application would work better if you sent over an array of objects, instead of just the query string. For that, jQuery has the .serializeArray() method. It's very similar to the .serialize() method listed above, except it produces an array of objects, instead of a string.

```js
// Creating an array of objects containing form data
$( "#myForm" ).serializeArray();
 
// Creates a structure like this:
// [
//   {
//     name : "field_1",
//     value : "something"
//   },
//   {
//     name : "field_2",
//     value : "somethingElse"
//   }
// ]
```

[ajax and forms](https://learn.jquery.com/ajax/ajax-and-forms/)
#ajax #serialize_data