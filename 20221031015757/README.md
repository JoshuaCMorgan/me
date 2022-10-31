# delegate events to the descendant (inner) elements of a parent element that match a given selector.

The function takes four arguments: parentElement, selector, eventType, and callback. It returns true if it was able to add an event listener and undefined if it wasn't. 

let's say we have this html
```html
<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="utf-8">
    <title>Event Delegation Function</title>
  </head>
  <body>
    <main>
      <section>
        <h1>Header</h1>
        <p>Content</p>
      </section>
      <aside>
        <h2>Sub Side Notes</h2>
        <p>Note 1</p>
        <p>Note 2</p>
      </aside>
    </main>
    <nav>
      <p>Side Note</p>
    </nav>
  </body>
</html>
```
If we want to add an event listener to a parent element but have it trigger if there exists a child element
- Line 2 ensures that parentElement contains a valid Element.
- Line 4 creates an array of DOM nodes that are descendants of parentElement that match the selector.
  -  Notice that we use parentElement to call querySelectorAll; 
  -  this limits the nodes to descendants of parentElement. 
  -  Furthermore, the handler determines the value of validTargets' every time the event occurs; this lets the code see new elements added to the DOM after the event listener gets attached to parentElement.
Line 5 ensures that callback only executes the target element is one of the valid targets.
```javascript
function delegateEvent(parentElement, selector, eventType, callback) {
  if (parentElement && parentElement instanceof Element) {
    return !parentElement.addEventListener(eventType, event => {
      const validTargets = Array.prototype.slice.call(parentElement.querySelectorAll(selector));
      if (validTargets.includes(event.target)) {
        callback(event);
      }
    });
  }
}
```

- Scenario 1: delegateEvent(element1, 'p', 'click', callback);
The function executes and returns undefined.
It doesn't add an event listener to any elements.

- Scenario 2: delegateEvent(element2, 'p', 'click', callback);
The function executes and returns true.
It adds a click event listener to element2.
If you click anywhere on the page, the callback function does not trigger.

- Scenario 3: delegateEvent(element2, 'h1', 'click', callback);
The function executes and returns true.
It adds a click event listener to element2.
If you click anywhere on the page, the callback function does not trigger.

- Scenario 4: delegateEvent(element3, 'h1', 'click', callback);
The function executes and returns true.
It adds a click event listener to element3.
If you click the h1 element that contains the text "Header," the callback function should trigger and display an alert message, e.g., 'Target: H1\nCurrent Target: MAIN'.
If you click anywhere else, the callback function does not trigger.

- Scenario 5: delegateEvent(element3, 'aside p', 'click', callback);
The function executes and returns true.
It adds a click event listener to element3.
If you click a p element that is a descendant of aside element inside main, the callback function should trigger and display an alert message, e.g., 'Target: P\nCurrent Target: MAIN'.
If you click anywhere else, the callback function does not trigger.

- Scenario 6: delegateEvent(element2, 'p', 'click', callback);
The function executes and returns true.
It adds a click event listener to element2.
If you click anywhere on the page, the callback function does not trigger.

#event-delegation #delegate 