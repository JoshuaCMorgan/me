# jquery method chaining and object argument for getters and setters

Chaining methods and simplifying with Object Argument:
The `css()`  method can take either a property name and value as separate parameters, or a single object of key-value pairs. Below, both are equivalent. we can supply an object with key/value pairs that match up with the CSS property/value pairs you want to give the element, which lets you set any number of CSS property/value pairs at once. 
```js
$content.css('font-size', '18px').css('color', '#b00b00');
$content.css({'font-size': '18px', color: '#b00b00'})
```
#jquery #method_chaining #css_method #object_argument