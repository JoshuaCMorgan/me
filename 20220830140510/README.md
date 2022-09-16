# jQuery DOM Traversal looking inwards from an object: siblings

Sometimes, however, you may want to do something like grab all of the sibling elements that come after the current one and perform some action on them. 

- The `nextAll` method will return all siblings after, with an optional selector passed in.
-  `prevAll` goes in the opposite direction. 
-  And if you needed all the siblings, rather than grabbing the parent and then getting all its children, you could simply use `siblings` with an optional selector.

```html
<ul id="navigation">
  <li>
    <a href="#">Categories</a>
    <ul>
      <li><a id="html" href="#">HTML</a></li>
      <li><a id="css" href="#">CSS</a></li>
      <li><a id="javascript" href="#">Javascript</a></li>
    </ul>
  </li>
</ul>
```
```js
// Find all list items after the CSS list item and hide them
let $css = $('#css').closest('li');
$css.nextAll().hide();

// Find all list items before the CSS list item and hide them
$css.prevAll().hide();

// Find all sibling lis and show them
$css.siblings().show();
```
[traversing](https://api.jquery.com/category/traversing/)
#traverse #siblings #closest #prevAll #nextAll