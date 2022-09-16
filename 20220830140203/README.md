# jQuery DOM Traversal looking inwards from an object: children descendant selector
 
 We can start at the outermost `ul` and find all of the list items.
 One extremely useful method is the `find` method. You can call it on an existing jQuery object to traverse to one of its child elements using another CSS-like selector.

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
Here we pass the css element id selector in to jquery function to be wrapped in an object. Then we traverse it inwards to `li` elements. This finds ALL of them.
```js
$('ul#navigation').find('li').length
$('ul#navigation li')
```
with `length` the browser returns
```js
jQuery.fn.init(4) [li, li, li, li, prevObject: jQuery.fn.init(1)]
    0: li
    1: li
    2: li
    3: li
    length: 4
    prevObject: jQuery.fn.init [ul#navigation, prevObject: jQuery.fn.init(1)]
    [[Prototype]]: Object(0)
```

- Collecting children
we'd like to collect only the immediate children `li`s from the navigation `ul`. We can use the children method either with or without a selector,
```js
$('#navigation').children().length
```
Returned
```js
jQuery.fn.init [li, prevObject: jQuery.fn.init(1)]
    0: li
    length: 1
    prevObject: jQuery.fn.init [ul#navigation, prevObject: jQuery.fn.init(1)]
    [[Prototype]]: Object(0)
```

[traverse outward from an object](20220830135912)
#find #traverse_dom #children #list
