# Toggle / Hide elements in HTML using classes

There are several ways to do this with the DOM
## Using classes
-  `DOMTokenList.replace()`
  - syntax: `replace(oldToken, newToken)`

- `DOMTokenList.add()` or `remove()`
-  `DOMTokenList.toggle()`
  - syntax
    - `toggle(token)`
    - `toggle(token, force)`

## Using data attribute
Below, we set the 'button' data attribute and form id attribute to match.
You'll notice that 'form' element has 'hidden' attribute.
When a button is clicked, we access the the dataset value, retrieve
the form element by using the id value and invoke 'hidden' global attribute.  
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Title of the Document</title>
  </head>
  <body>
    <button data-toggle-id="mail-id">
      Show the form
    </button>
    <form id="mail-id" hidden>
      Your mail:
      <input type="email">
    </form>
    <script>
      document.addEventListener('click', function(event) {
        let id = event.target.dataset.toggleId;
        if(!id) return;
        let elem = document.getElementById(id);
        elem.hidden = !elem.hidden;
      });
    </script>
  </body>
</html>
```

## Using toggle
 - `force` is boolean.  if true, toggle will be added; if false, toggle will be removed.
 - in the code below,
   - if the `remaining` is less than zero, then it is true and `'invalid'` will be added to the class
   - if the `remaining` is greater than zer, it is false and `'invalid'` is removed from the class.
 -  notice that we also disable the button element
```html
<!-- add a character counter that updates as the user types. -->
<!DOCTYPE html>
<html lang="en-US">
<head>
	<title>Events</title>
  <style>
    .composer {
      background: #f5f5f5;
      padding:  1em;
      width:  30em;
    }

    .composer textarea {
      width: 100%;
      height: 4em;
    }

    .composer textarea.invalid {
      color: red;
    }
  </style>
</head>
<body>
	<div class="composer">
    <textarea placeholder="Enter your message"></textarea>
    <p class="counter">
      140 characters remaining
    </p>
    <button type="submit">Post Message</button>
  </div>
</body>
	<script>
    let composer = document.querySelector('.composer');
    let textarea = composer.querySelector('textarea');
    let counter = composer.querySelector('.counter');
    let button = composer.querySelector('button');

    function updateCounter() {
      let length = textarea.value.length;
      let remaining = 10 - length;
      let message = `${remaining.toString()} characters remaining`;
      let invalid = remaining < 0;
      
      textarea.classList.toggle('invalid', invalid);
      button.disabled = invalid;

      counter.textContent = message;    
    }
    
    textarea.addEventListener('keyup', updateCounter);
    
    updateCounter();
       
  </script>
</html>
```

## Using replace

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
## Use `add()`  and `remove()`

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

#toggle  #classList  #add  #remove #display  #hide  #show  #replace #disabled

