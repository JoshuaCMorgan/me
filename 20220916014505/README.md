# Toggle / Hide elements in HTML using classes

There are several ways to do this with the DOM
## Using classes
- use `DOMTokenList.replace()`
- syntax: `replace(oldToken, newToken)`

example HTML / JS

```html
<p><a id="replay" href="#" class="hide">Play another</a></p>
```
```css
#replay.hide {
  display: none;
}

#replay.show {
  display: visible;
}
```
```javascript
let replay = document.querySelector('#replay');
showReplayLInk: function() {
  replay.classList.replace('hide', 'show')
}

hideReplayLink: function() {
  replay.classList.replace('show', 'hide')
}
```
Or, you can use `DOMTokenList.add()` or `remove()`
syntax: 
```javascript
add(token0)
add(token0, token1)
```
```css
#replay {
  display: none;
}

#replay.visible {
  display: inline;
}
```
```javascript
const replay = document.querySelector("#replay");
 showReplayLink: function() {
  replay.classList.add("visible");
},
hideReplayLink: function() {
  replay.classList.remove("visible");
},
```

