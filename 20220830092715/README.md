# jquery object methods: getters and setters

Once you obtain an object from jQuery, you can perform a variety of tasks with it. 
When using `.css()` as a setter, jQuery modifies the element's style property.   `$( "#mydiv" ).css( "color", "green" )` is equivalent to `document.getElementById( "mydiv" ).style.color = "green"`.

- Getter and Setter methods
-  Some jQuery methods, including css, have both setter and getter forms: if you omit the last argument, the method acts as a getter; otherwise, it acts as a setter.

```js
console.log($content.css('font-size'));    // getter
$content.css('font-size', '18px');         // setter
```

```js
var width = $content.width();  // 800 (getter)
$content.width(width / 2);     // Sets to 400
console.log($content.width()); // now 400 (getter)
```

Chaining methods and simplifying with Object Argument:
This method can take either a property name and value as separate parameters, or a single object of key-value pairs. Below, both are equivalent
```js
$content.css('font-size', '18px').css('color', '#b00b00');
$content.css({'font-size': '18px', 'color': '#b00b00'})
```

#object_methods #jquery #css_method #getter #setter