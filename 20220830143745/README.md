# Reduce the set of matched elements to those that match the selector or pass the function's test.

syntax
```js
.filter(selector)
.filter(function)
.filter(elements)
.filter(selection)
```
EXAMPLES
```html
<table>
        <tbody>
          <tr>
            <td>Cras ornare</td>
            <td class="protected">elementum sodales</td>
            <td>Proin id pretium</td>
          </tr>
          <tr>
            <td>non viverra magna</td>
            <td>Suspendisse quis</td>
            <td class="protected">feugiat metus</td>
          </tr>
          <tr>
            <td>Praesent luctus</td>
            <td>lorem sed</td>
            <td>est mollis</td>
          </tr>
        </tbody>
</table>
```

The jQuery :odd selector is 0 based.
```js
$('table').find('tr').filter(':odd');
// or
$('table').find('tr:odd');

// using a function
$('table' ).find('tr')
.filter(function( index ) {
  return index % 2 !== 0;
})
```

another good example: Find the list item that contains the text ac ante, 
```html
<ul>
  <li>Vestibulum tempor tortor et dapibus accumsan.</li>
  <li>Nam ut risus nec odio gravida vestibulum.</li>
  <li>
    Interdum et malesuada fames
    <ul>
      <li>ac ante</li>
      <li>ipsum primis</li>
      <li>in faucibus</li>
    </ul>
  </li>
  <li>Proin cursus ex eu faucibus malesuada.</li>
</ul>
```
```js
$('li').find('li').filter(":contains('ac ante')");
// or
$('li li').filter(":contains('ac ante')");
// or
$("li li:contains('ac ante')");
```
#filter #reduce #odd #find #pseudo