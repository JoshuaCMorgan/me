# Handlebarsjs iterate over array property values

The each-helper iterates an array, allowing you to access the properties of each object via simple handlebars expressions.
It can be retrieved using `this` or current context `.`
```javascript
{ 
  makes: ['Honda', 'Toyota', 'Suzuki', 'Audi'],
  models: ['Accord', 'Camry', 'Corolla', 'Swift', 'A4'],
  prices:  [7000, 11000, 12500, 15000, 9000, 25000, 26000],
  years:  [2005, 2008, 2009, 2016, 2014, 2013] 
}

{
  "people": [
    "John",
    "Peter",
    "Mary"
  ]
}
```

Then my template should be written as
```html
<select id="standard-select">
  <option value="all" selected>All</option>
  {{# each makes}}
  <option value="{{.}}">{{.}}</option>
  {{/each}}
</select>

{{#people}}
Hello, {{.}}!
{{/people}}

```
# handlebarsjs #block-helpers
