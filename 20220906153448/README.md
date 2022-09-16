# Reading data attributes in jQuery

If you want to set and retrieve custom data on an element after the page has been rendered, use the `.data` method. 
As a setter method, data will store the value on the node that can be retrieved with the data method as a getter, but it will not update the HTML markup.

A `data-*` attribute: `data-block` is our attribute.  
```html
<li><a href="#" data-block="gold">Gold Sponsors</a></li>
```

## Two methods to read data
- `.attr`
  - allows you to specify the attribute name and get the value of the attribute. 
- `.data`
  - You have to be careful when using this method, since it can be used for two different data sets
  

## How to use
- Using the `data()` method to update data does not affect attributes in the DOM. To set a `data-*` attribute value, use `attr`.
- use the data method and pass the name of the data attribute minus the `data-` at the beginning.
```javascript
//syntax: key refers to the attribute
$(selector).data(key);
//example
$link.data('block');
```
## Example
```html
<div data-role="page" data-last-value="43" data-hidden="true" data-options='{"name":"John"}'></div>
```
```javascript
$( "div" ).data( "role" ) === "page"; // true
$( "div" ).data( "lastValue" ) === 43; // true
$( "div" ).data( "hidden" ) === true;  // true
$( "div" ).data( "options" ).name === "John"; // true
```

## .data()
- this will get or set values
- Calling .data() with no parameters returns a JavaScript object containing each stored value as a property. 

```javascript
var elem = document.createElement( "span" );
$( elem ).data( "foo" ); // undefined
$( elem ).data(); // {}
 
$( elem ).data( "foo", 42 );
$( elem ).data( "foo" ); // 42
$( elem ).data(); // { foo: 42 }
```
## the method .data() will not manipulate HTML data attributes
```javascript
var $a = $('a[data-block=gold]');

console.log($a.attr('data-block')); // gold
console.log($a.data('block')); // gold

$a.data('block', 'silver');

console.log($a.attr('data-block')); // gold
console.log($a.data('block')); // silver
```
#data #attr #attribute