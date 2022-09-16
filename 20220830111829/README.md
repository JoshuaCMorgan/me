# Selecting jQuery objects

Posted in: Using jQuery Core
Selecting Elements
The most basic concept of jQuery is to "select some elements and do something with them." jQuery supports most CSS3 selectors, as well as some non-standard selectors. For a complete selector reference, visit the Selectors documentation on api.jquery.com.

- Selecting Elements by ID
```js 
$( "#myId" ); // Note IDs must be unique per page.
```

- Selecting Elements by Class Name
```js
$( ".myClass" );
```

-Selecting Elements by Attribute
```js
$( "input[name='first_name']" );
```

- Selecting Elements by Compound CSS Selector
```js
$( "#contents ul.people li" );
```

- Selecting Elements with a Comma-separated List of Selectors
```js
$( "div.myClass, ul.people" );
```

- Pseudo-Selectors
```js
$( "a.external:first" );
$( "tr:odd" );
 
// Select all input-like elements in a form (more on this below).
$( "#myForm :input" );
$( "div:visible" );
 
// All except the first three divs.
$( "div:gt(2)" );
 
// All currently animated divs.
$( "div:animated" );
```

Selecting element if it exists
```js
// Testing whether a selection contains elements.
if ( $( "div.foo" ).length ) {
    ...
}
```

- Refining and Filtering Selections
```js
// Refining selections.
$( "div.foo" ).has( "p" );         // div.foo elements that contain <p> tags
$( "h1" ).not( ".bar" );           // h1 elements that don't have a class of bar
$( "ul li" ).filter( ".current" ); // unordered list items with class of current
$( "ul li" ).first();              // just the first unordered list item
$( "ul li" ).eq( 5 );              // the sixth
```

- Selecting Form Elements
Using the :input selector selects all <input>, <textarea>, <select>, and <button> elements:
```js
$( "form :input" );
```

Using the :selected pseudo-selector targets any selected items in <option> elements:
```js
$( "form :selected" );
```
#selecting_elements #not #filter #first #eq