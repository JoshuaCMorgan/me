# jQuery DOM Traversal: Looking Outwards from an object

There are a multitude of methods to help you find the elements you need, and traversing the DOM will be the most common action you'll be taking using jQuery. 

There are two methods that you'll use for this depending on the situation.
- `parent`
- `closest`
- `parents`

Here, we access the all parent elements of paragraphs and do something with them. 
```html
<blockquote>
  <p>Take off every Zig!</p>
</blockquote>
```
```js
let $p = $('p');
$p.parent().css('color', 'blue');
```

By passing in a string selector, we restrict which parent elements of all paragraphs are affected. Here we retrieve only those with class of highlight and pass that class selector in to the call to parent.
```html
<blockquote>
  <p>You have no chance to survive make your time.</p>
</blockquote>

<blockquote>
  <p>Ha ha ha ha ...</p>
</blockquote>

<blockquote class="highlight">
  <p>Captain !!</p>
</blockquote>

<blockquote>
  <p>Take off every Zig!</p>
</blockquote>
```
```js
let $p = $('p');
$p.parent('.highlight').css('color', 'blue');
```

`closest` is used if we want to look further out than an immediate parent. With `parent`, it never looks at the current element for consideration. With `closest`, it first looks at the current element to see if it is a match. 
The `closest` method is very useful for finding the first ancestor element that meets the criteria passed to the method. If we want to find the first `ul` when starting at a `li` instead of selecting all possible ancestor uls, we could call it like this:
```html
<style>
  .categories {
    font-size: 20px;
  }
  </style>
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
$('#javascript').closest('ul').addClass('categories');
```
If we wanted to grab all parent `ul` elements, there's a more comprehensive method called `parents` that will continue all the way out to the root element. 
```js
$('#javascript').parents('ul').addClass('categories');
```
#closest #parents #parent #traversing_dom 