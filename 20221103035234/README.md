#  remove all the previous list items we may have rendered;

```html
<ul>
  <li>list 1</li>
  <li>list 2</li>
</ul>
```
we first see if there is a child element.  Then, we remove that child.  This is just one way of doing it. 
```javascript
  let listUI = document.createElement("ul");
  while (listUI.lastChild) {
    listUI.removeChild(listUI.lastChild);
  }
```
#remove-elements #remove