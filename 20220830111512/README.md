# jquery getting elements into jquery object, single or multiple

When the jQuery function is invoked with a CSS selector, it will return a jQuery object wrapping any element(s) that match this selector.  It will match any and all elements unless targeted.  the most straight-forward way to select a particular element is to use the .eq() function.

```js
// Selecting all <h1> tags. 
let headings = $( "h1" );

//selecting only the first
let firstHeading = headings.eq( 0 );
let firstHeading = headings.eq[0]; // since jQuery object is array-like
```

Since, these are placed into a jQuery object, we can also retrieve the DOM element itself by using `get()` method.

```js
// Selecting only the first <h1> element on the page. 
let firstHeadingElem = $( "h1" ).get( 0 );
```
#jquery #selecting_elements #getting_elements