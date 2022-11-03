# Throttle: delay sending an HTTP request to the server for a short period of time.

We will most likely work with a module.
So, we will need to export it, and then import it into the HTML

If this were an html file, we would have our script tag with a type attribute set to module.
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Autocomplete!</title>
    <link rel="stylesheet" href="/stylesheets/normalize.css">
    <link rel="stylesheet" href="/stylesheets/autocomplete.css">
    <script type="module" src="/javascripts/autocomplete.js"></script>
  </head>
```

This function takes a callback and a delay in milliseconds as arguments and returns a new function that calls the callback after the specified delay elapses. 

`setTimeout` returns a positive integer value which identifies the created timer.
when we pass it to `clearTimeout`, the timeout we created will cancel.
So, in essence, we are making sure we are working with the latest user event. If a 
new value comes in, we don't want to work the the previous one.  We want to work with
the latest input.
`apply`'s first argument sets the execution context.  But, since we have already
set its execution context, it's best to set it to `null`.
```javascript
export default (func, delay) => {
  let timeout;
  return (...args) => {
    if (timeout) { clearTimeout(timeout) }
    timeout = setTimeout(() => func.apply(null, args), delay);
  };
};
```
In our main programming file, 
we need to import the module so we can use the function.
we then need to pass `debounce` the function we want 
to delay.
Here, it is an event listener. When the event occurs, we want to invoke `this.valueChanged` inside `debounce`.  
To do so, we pass the method `valueChanged` into `debounce` where it gets
set to parameter and placed inside the body of the returned function.  So,
essentially we have moved the function block
As a result, there is no use for the property method, so we reassign the property `valueChanged` to the returned function. In essence,we put the function block 
inside the body of another, and swapped that returned function with the current one.
```javascript
import debounce from './debounce.js';

const Autocomplete = {
  // code omitted

  bindEvents: function() {
    this.input.addEventListener('input', this.valueChanged);
   // code omitted
  },

  init: function() {
    // code omitted
    this.valueChanged = debounce(this.valueChanged.bind(this), 300);
    this.bindEvents();
  }
}
```
#setTimeout #debounce #partial-function #apply #bind


