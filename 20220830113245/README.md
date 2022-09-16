# iterating over a jQuery collection

`.each()` method iterates over each matched element in the collection and performs a callback on that object. The index of the current element within the collection is passed as an argument to the callback. The value (the DOM element in this case) is also passed, but the callback is fired within the context of the current matched element so the this keyword points to the current element as expected in other jQuery callbacks.

```html
<ul>
    <li><a href="#">Link 1</a></li>
    <li><a href="#">Link 2</a></li>
    <li><a href="#">Link 3</a></li>
</ul>
````
may be used like so:

```js
$( "li" ).each( function( index, element ){
    console.log( $( this ).text() );
});
 
// Logs the following:
// Link 1
// Link 2
// Link 3
```

Anytime we want to create an array or concatenated string based on all matched elements in our jQuery selector, we're better served using .map().

```js
$( "li" ).map( function(index, element) {
    return this.id;
}).get();
```

Notice the .get() chained at the end. .map() actually returns a jQuery-wrapped collection, even if we return strings out of the callback. We need to use the argument-less version of .get() in order to return a basic JavaScript array that we can work with. To concatenate into a string, we can chain the plain JS .join() array method after .get().
[iterating](https://learn.jquery.com/using-jquery-core/iterating/)
#each_method #iterating #map_method