# Using CSS Classes for Styling should be avoided

As a getter, the .css() method is valuable. However, it should generally be avoided as a setter in production-ready code, because it's generally best to keep presentational information out of JavaScript code.

Instead, write CSS rules for classes that describe the various visual states, and then change the class on the element.

```js
let h1 = $( "h1" );
 
h1.addClass( "big" );
h1.removeClass( "big" );
h1.toggleClass( "big" );

if ( h1.hasClass( "big" ) ) {
    h1.html('playing with jquery');
}
```

#css_classes #setter